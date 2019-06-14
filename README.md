# javadbf
公司老项目中的一个jar包,用来处理dbf文件,但是没有考虑到中文的情况

原maven是：
<!-- https://mvnrepository.com/artifact/com.linuxense/javadbf -->
<dependency>
    <groupId>com.linuxense</groupId>
    <artifactId>javadbf</artifactId>
    <version>0.4.0</version>
</dependency>
这个是最新版,也是唯一一个版本。。。
线上发现问题,导出来的dbf文件有乱码的问题,但是只是部分,然后debug开始。。。

解决方案：
