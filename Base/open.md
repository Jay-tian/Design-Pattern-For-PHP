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
新版本上线刚不久，客户又反馈说，yml格式的文件更利于他们维护希望我们也能支持读取yml格式的文件，为了满足客户的需求我们的代码又要不得不改版一次

```php
public function readParams($sourceFile)
{
    if (isXml) {
         //读取xml文件参数
    } elseif (isYml) {
        //读取yml文件参数
    } else{
    //读取文本参数
    }
}
```
由此我们可以看出，每当我们需要满足新的功能时必须要修改代码，添加新的逻辑判断，而且随着时间推移这样的代码维护成本也会越来越高，这时候我们需要根据开闭原则对源代码进行重构。

在本例中不变的地方是读取参数，变化的是读取的类型，因此我们将变化的这部分独立出去

                                                          
```php
class ParamHandler
{
    public function readParams()
    {
        //根据不同文件类型实例化
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





