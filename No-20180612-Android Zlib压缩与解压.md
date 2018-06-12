### Zlib 压缩与解压

需注意：
 1. 因为`String` 与 `byte[]`的字节位数不一致会，所以直接不能直接转换，否则会数据格式不对导致解压失败
 2. 解压时，输出的 `byte[]` 数组的长度需要进行计算，否则可能不能解压全部数据，这里示例中由于数据较短所以默认 100 `byte[] result = new byte[100];` 

```java
try {
    // Encode a String into bytes
    String inputString = "blahblahblah";
    byte[] input = inputString.getBytes("UTF-8");

    // Compress the bytes
    byte[] output = new byte[100];
    Deflater compresser = new Deflater();
    compresser.setInput(input);
    compresser.finish();
    int compressedDataLength = compresser.deflate(output);
    System.out.println("compressedDataLength: " + compressedDataLength);
    compresser.end();

    // Decompress the bytes
    Inflater decompresser = new Inflater();
    decompresser.setInput(output, 0, compressedDataLength);
    byte[] result = new byte[100];
    int resultLength = decompresser.inflate(result);
    System.out.println("resultLength: " + resultLength);
    decompresser.end();

    // Decode the bytes into a String
    String outputString = new String(result, 0, resultLength, "UTF-8");
    System.out.println("outputString: " + outputString);
} catch (java.io.UnsupportedEncodingException ex) {
    ex.printStackTrace();
} catch (java.util.zip.DataFormatException ex) {
    ex.printStackTrace();
}
```