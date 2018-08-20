Android HTTPURLconnection文件上传

```Java
/**
 * 文件上传
 * @param urlStr
 * @param textMap 参数
 * @param fileMap 文件
 * @return
 **/
public String formUploadFile(String urlStr, Map<String, String> textMap, Map<String, String> fileMap) {
    String result = "";
    HttpURLConnection conn = null;
    String BOUNDARY = "------------------------61ce907dc755535c"; //boundary就是request头和上传文件内容的分隔符
    String contentType = "multipart/form-data";
    try {
        URL url = new URL(urlStr);
        conn = (HttpURLConnection) url.openConnection();
        conn.setConnectTimeout(10000);
        conn.setReadTimeout(10000);
        conn.setDoOutput(true);
        conn.setDoInput(true);
        conn.setUseCaches(false);
        conn.setRequestMethod("POST");
        conn.setRequestProperty("Connection", "Keep-Alive");
        conn.setRequestProperty("User-Agent", "Mozilla/5.0 (Windows; U; Windows NT 6.1; zh-CN; rv:1.9.2.6)");
        conn.setRequestProperty("Content-Type", "multipart/form-data; boundary=" + BOUNDARY);

        OutputStream out = new DataOutputStream(conn.getOutputStream());
        // text
        if (textMap != null) {
            StringBuffer strBuf = new StringBuffer();
            Iterator<Map.Entry<String, String>> iter = textMap.entrySet().iterator();
            while (iter.hasNext()) {
                Map.Entry<String, String> entry = iter.next();
                String inputName = entry.getKey();
                String inputValue = entry.getValue();
                if (inputValue == null) {
                    continue;
                }
                strBuf.append("\r\n").append("--").append(BOUNDARY).append("\r\n");
                strBuf.append("Content-Disposition: form-data; name=\"" + inputName + "\"\r\n\r\n");
                strBuf.append(inputValue);
            }
            out.write(strBuf.toString().getBytes());
            System.out.println(strBuf.toString());
        }

        // file
        if (fileMap != null) {
            Iterator<Map.Entry<String, String>> iter = fileMap.entrySet().iterator();
            while (iter.hasNext()) {
                Map.Entry<String, String> entry = iter.next();
                String inputName = entry.getKey();
                String inputValue = entry.getValue();
                if (inputValue == null) {
                    continue;
                }
                File file = new File(inputValue);
                String filename = file.getName();

                StringBuffer strBuf = new StringBuffer();
                strBuf.append("\r\n").append("--").append(BOUNDARY).append("\r\n");
                strBuf.append("Content-Disposition: form-data; name=\"" + inputName + "\"; filename=\"" + filename + "\"\r\n");
                strBuf.append("Content-Type:" + contentType + "\r\n\r\n");

                out.write(strBuf.toString().getBytes());

                DataInputStream in = new DataInputStream(new FileInputStream(file));
                int bytes = 0;
                byte[] bufferOut = new byte[1024];
                while ((bytes = in.read(bufferOut)) != -1) {
                    out.write(bufferOut, 0, bytes);
                }
                in.close();
            }
        }

        byte[] endData = ("\r\n--" + BOUNDARY + "--\r\n").getBytes();
        out.write(endData);
        out.flush();
        out.close();

        int res = conn.getResponseCode();
        Log.e(TAG, "response code:" + res);
        result = readIt(conn.getInputStream());
        Log.e(TAG, "uploadLogFile - result: "+ result);

    } catch (Exception e) {
        System.out.println("发送POST请求出错。" + urlStr);
        e.printStackTrace();
    } finally {
        if (conn != null) {
            conn.disconnect();
            conn = null;
        }
    }
    return result;
}
```

####参考文章：
[Android使用HttpURLConnection上传文件](https://blog.csdn.net/earbao/article/details/47613921)