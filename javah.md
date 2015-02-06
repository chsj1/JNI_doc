#使用javah命令生成C/C++头文件
=============================
本文档主要介绍javah的用法，以及怎样用它来生成jni类型的头文件

##javah的man文档翻译
```
javah
  javah - 用于生成C（和C++，以下略）方法原型和头文件
  javah根据java类生成C头文件和源代码文件。这些文件提供了java代码和C代码之间交互的纽带。

SYNOPSIS
  javah [ options ] fully-qualified-classname. . .

DESCRIPTION
  javah 生成实现本地方法所需的 C 头文件和源文件。C 程序用这些文件在本地源代码中引用对象。
  .h 文件含有一个 struct 定义，该定义的布局与相应类的布局平行。该 struct 中的域对应于类中的实例变量。

  头文件名以及在头文件中所声明的结构名都来源于类名。如果传给 javah 的类是在某个包中，则头文件名和结构名前都要冠以该包名。
  下划线 (_) 用作名称分隔符。 
  
　缺省情况下，javah 为每个在命令行中列出的类都创建一个头文件，且将该文件放在当前目录中。用 -stubs 选项创建源文件。用 -o 选项将所有列出类的结果串接成一个单一文件。 
　
　新的平台相关方法接口（Java 平台相关代码接口 (JNI)）不需要头文件信息或 stub 文件。javah 仍可用于生成 JNI 风格的本地方法所需的本地函数原型。javah 在缺省情况下生成 JNI 风格的输出并将结果放在 .h 文件中。

OPTIONS
  -o 输出文件 
　将命令行中列出的所有类的头文件或源文件串接到输出文件中。-o 或 -d 两个选项只能选择一个。

  -d 目录 
　设置 javah 保存头文件或 stub 文件的目录。-d 或 -o 两个选项只能选择一个。

  -stubs 
　使 javah 从 Java 对象文件生成 C 声明。 

  -verbose 
　指明长格式输出，并使 javah 将所生成文件的有关状态的信息输出到标准输出设备中。 
　　
　-help 
　输出 javah 用法的帮助信息。 
　　
　-version 
　输出 javah 的版本信息。 
　
　-jni 
　使 javah 创建一输出文件，该文件包含 JNI 风格的本地方法函数原型。这是缺省输出，所以 -jni 的使用是可选的。 
　　
　-classpath 路径 
　指定 javah 用来查询类的路径。如果设置了该选项，它将覆盖缺省值或 CLASSPATH 环境变量。

  -bootclasspath 路径 
　指定加载自举类所用的路径。缺省情况下，自举类是实现核心 Java 平台的类，位于 jre\lib\rt.jar 和 jre\lib\i18n.jar 中。 
　　
　-old 
　指定应当生成旧 JDK1.0 风格的头文件。 
　　
　-force 
　指定始终写输出文件。

ENVIRONMENT VARIABLES
  CLASSPATH
  一个系统环境变量，用冒号分开(linux下，windows下用分号隔开)。为java程序提供了默认的查找路径。
```