Android getContentResolver为空的问题

Cursor cursor = context.getContentResolver().query(uri, new String[]{Telephony.Sms._ID}, null, null, null);

参考链接
[Android---相册getContentResolver().query结果为空指针](https://blog.csdn.net/trent1985/article/details/51533274)