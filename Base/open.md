# 设计原则－开闭原则

**开闭原则**(Open-Closed Principle, OCP):一个软件中的对象(类,模块,函数)应该对于**扩展**是开放的,对于**修改**是关闭的。

举个例子，现在要上线一个能读取文本配置文件的功能，于是我们创建了一个用于读取文本配置文件的类

``` php
class ParamsHandler

{
    public function readParams($sourceFile)
    {
        //从sourceFile中读取文本参数
    }
}
```
随着时间的推移这个功能使用的人越来越多，客户也提出了新的需求，他们希望这个功能能支持读取xml格式的参数，此时我们需要修改我们的读取类来满足客户的需求

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
    public function readParams()
    {
        //根据不同文件类型实例话
    }
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





