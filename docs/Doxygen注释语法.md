> Doxygen 是一个非常流行的源代码文档生成工具，能够从源代码的注释中生成说明文档，支持多种变成语言，如 C、Objective-C、C#、PHP、Java、Python、IDL（Corba、Microsoft 和 UNO/OpenOffice 风格）), Fortran, 某种程度上还有 D. Doxygen 也支持硬件描述语言 VHDL 。

> 该文件内容主要简单的描叙 Doxygen 的注释语法，以备以后查阅。

# Doxygen 注释语法

## 支持的注释

Doxygen 只对源文件中的两种注释有所响应，需要生成文档的注释都要遵循这两种规则。

* 单行注释：///`或者`//!
* 多行注释：`/**`或者`/*!`

## 文件注释

对整个源文件的注释，一般放在整个文件的开头。

```c
/**
 * @file 文件名
 * @brief 简介
 * @details 细节
 * @mainpage 工程概览
 * @author 作者
 * @email 邮箱
 * @version 版本号
 * @date 年-月-日
 * @license 版权
 */
```

例如：

```c
/**
 * @file Test.h
 * @brief 测试头文件
 * @details 这个是测试Doxygen
 * @mainpage 工程概览
 * @author jdzhangxin
 * @email jdzhangxin@126.com
 * @version 1.0.0
 * @date 2017-11-17
 */
```

生成的文档效果：

![img](https://upload-images.jianshu.io/upload_images/1730134-339e732f4b3fe3fd.png?imageMogr2/auto-orient/strip|imageView2/2/w/811/format/webp)

## 类定义注释

类定义的注释方式非常简单，使用`@brief`后面填写类的概述，换行填写类的详细信息。

```c
 /**
 * @brief 类的简介
 * @detail 类的详细概述
 */
```

例如：

```c
 /**
 * @brief 测试类
 * 主要用来演示Doxygen类的注释方式
 */
 class Test{
 };
```

文档效果：

![img](https://upload-images.jianshu.io/upload_images/1730134-509ca5cdaff70836.png?imageMogr2/auto-orient/strip|imageView2/2/w/796/format/webp)

> 命名空间、结构体、联合体、枚举定义与类定义注释方式一致。

## 常量/变量的注释

常量/变量包括以下几种类型

- 全局常量变量
- 宏定义
- 类/结构体/联合体的成员变量
- 枚举类型的成员

注释分为两种方式，代码前注释、代码后注释，可根据具体情况自行选择。

- 代码前注释

  ```c
  /// a rectangle length variable  
  int length=100;
  ```

  例如：

  ```c
  /// 缓存大小
  #define BUFSIZ 1024*4
  ```

- 代码后注释

  ```c
  常量/变量 ///< 注释
  ```

  例如：

  ```c
  #define BUFSIZ 1024*4 ///< 缓存大小
  ```

  生成文档效果：

  ![img](https://upload-images.jianshu.io/upload_images/1730134-722b8a69463f405a.png?imageMogr2/auto-orient/strip|imageView2/2/w/796/format/webp)

## ▲函数注释

一个完整的函数注释：

```c
/**
 * @brief 函数简介
 * @detail 详细说明
 * 
 * @param 形参 参数说明
 * @param 形参 参数说明
 * @return 返回说明
 *   @retval 返回值说明
 *   @retval 返回值说明
 *
 * @note 注解
 * @attention 注意
 * @warning 警告
 * @exception 异常
 */
```

例子：

```c
/**
* @brief 主函数
* @details 程序唯一入口
*
* @param argc 命令参数个数
* @param argv 命令参数指针数组
* @return 程序执行成功与否
*     @retval 0 程序执行成功
*     @retval 1 程序执行失败
* @note 这里只是一个简单的例子
*/
int main(int argc, char* argv[])
```

文档效果：

![img](https://upload-images.jianshu.io/upload_images/1730134-ead3b48ba10f6f0d.png?imageMogr2/auto-orient/strip|imageView2/2/w/798/format/webp)

## 其它关键字

| 命令          | 生成字段名   | 说明                           |
| ------------- | ------------ | ------------------------------ |
| `@see`        | 参考         |                                |
| `@class`      | 引用类       | 用于文档生成连接               |
| `@var`        | 引用变量     | 用于文档生成连接               |
| `@enum`       | 引用枚举     | 用于文档生成连接               |
| `@code`       | 代码块开始   | 与`@endcode`成对使用           |
| `@endcode`    | 代码块结束   | 与`@code`成对使用              |
| `@bug`        | 缺陷         | 链接到所有缺陷汇总的缺陷列表   |
| `@todo`       | TODO         | 链接到所有TODO 汇总的TODO 列表 |
| `@example`    | 使用例子说明 |                                |
| `@remarks`    | 备注说明     |                                |
| `@pre`        | 函数前置条件 |                                |
| `@deprecated` | 函数过时说明 |                                |

## 参考

https://www.jianshu.com/p/9464eca6aefe