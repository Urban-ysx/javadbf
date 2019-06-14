# javadbf
公司老项目中的一个jar包,用来处理dbf文件,但是没有考虑到中文的情况<br>
**原maven是：**
````javascript
<!-- https://mvnrepository.com/artifact/com.linuxense/javadbf -->
<dependency>
    <groupId>com.linuxense</groupId>
    <artifactId>javadbf</artifactId>
    <version>0.4.0</version>
</dependency>
````
这个是最新版,也是唯一一个版本。。。
线上发现问题,导出来的dbf文件有乱码的问题,但是只是部分,然后debug开始。。。
**解决方案：**
Utils类<br>
```java
    public static byte[] textPadding(String text, String characterSetName, int length, int alignment,
                                     byte paddingByte) throws UnsupportedEncodingException {
        if (text.length() >= length) {
            return text.substring(0, length).getBytes(characterSetName);
        }
        byte byte_array[] = new byte[length];
        Arrays.fill(byte_array, paddingByte);
        //支持中文字符长度
        byte[] bytes = text.getBytes(characterSetName);
        switch (alignment) {
            case ALIGN_LEFT:
                System.arraycopy(bytes, 0, byte_array, 0, bytes.length);
                break;
            case ALIGN_RIGHT:
                int t_offset = length - text.length();
                System.arraycopy(bytes, 0, byte_array, t_offset, bytes.length);
                break;
        }
        return byte_array;
    }
