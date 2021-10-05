### 任务一

本次代码的工作分为两部分，先将排序算法编码进自选图片，然后再从编码后的图片出解码出排序算法，并加载到jvm内存供使用。

编码由SteganographyFactory完成，先对排序的.java文件进行compile，也就是由.java文件生成.class文件，得到字节码。然后将这个.class转换成Byte数组bytes，包含文件名和文件内容信息。从原图中利用getRGB可以得到像素数组pixels。然后将bytes和pixels这两个数组进行一系列位运算，就把.class文件编码进了图片。因为pixels数组的大小是远大于bytes数组的，所以编码完后pixels的改动很小，得到的新图片与原图基本没差别。

第二步，要进行解码和加载，定义自己的类加载器SteganographyClassLoader，它继承自ClassLoader。当要加载一个类时，就调用loadClass方法。它首先向上委派，当上层的类加载器都发出没有找到所需类的消息时，它才自己尝试加载所需类。这时进入override的findClass方法，通过前面的编码操作的逆向操作，从编码后的图片中获得所需类型信息。最后再用Class.newInstance方法获得一个实例。



### 任务二

选择排序图片：file:///C:/Users/xjh/javaHw/jw03-SilenceXjh/example.SelectSorter.png

快速排序图片：file:///C:/Users/xjh/javaHw/jw03-SilenceXjh/example.QuickSorter.png

均为本地的绝对路径



### 任务三

选择排序

https://asciinema.org/a/QknpraCCquy8bsMfp4eJaf1qN

快速排序

https://asciinema.org/a/4ULqLnLwumvvMgQw9GiJ8B3Py



### 任务四

用时欣同学的图片S191220097.QuickSorter.png

URL为 file:///C:/Users/xjh/javaHw/jw03-SilenceXjh/othersImage/S191220097.QuickSorter.png （本地绝对路径）

能得到正确运行结果

https://asciinema.org/a/z0nUTXoe8Okv1YQfpXbWkBpjR