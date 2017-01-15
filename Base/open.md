# 设计原则－开闭原则

**开闭原则**(Open-Closed Principle, OCP):一个软件中的对象(类,模块,函数)应该对于**扩展**是开放的,对于**修改**是关闭的。

举个例子，现在要创建一个用于读取配置文件的类

``` php
class ParamsHandler

{
    public function readParams($sourceFile)
    {
        //从sourceFile中读取文本参数
    }
}
```
好了，一切看起来似乎都非常完美，直到有一天，我们被告知我们这个只能读取文本参数的类不能满足需求了，产品经理希望它还能读取xml格式的参数。。。

于是你就改吧改吧代码又变成下面这个样子：

```php
public function readParams($sourceFile)
{
    if (preg_match("/\.xml$/i", $sourceFile)) {
        //读取xml文件参数
    } else {
        //读取文本参数
    }
}
```
现在似乎又再次满足了需求，然而还没等我们松口气，产品说他希望我们还能支持yml格式的文件。。。

在上面的例子中每当需要支持新的格式文件的参数读取时就得更改readParams的源码

```php
class ParamHandler
{
}
interfact ParamHandler
{
    public function readParams();
}

class XmlParamHandler implement ParamHandler
{
    public function readParams()
    {
    //读取xml文件参数
    }
}

class YmlParamHandler implement ParamHandler
{
   public function readParams()
    {
    //读取yml文件参数
    }
}



```
这样一来





