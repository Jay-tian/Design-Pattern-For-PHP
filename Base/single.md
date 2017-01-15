# 1.1 设计原则－单一职责

**单一原则**(Single Responsibility Principle):每个类都应该有一个单一的功能，并且该功能应该由这个类完全封装起来。所有它的(这个类的)服务都应该严密的跟该功能平行(功能平行意味着**没有依赖**)。

单一原则是我们平时coding的过程中最容易理解但也是最不容易进行最佳实践的原则。它要求我们在设计类的时候就确定好类的作用域和目标.(现实生活中我们常常做不到这点，所以便有了后续的重构等等,so sad)。

举个例子，现在要创建一个用于读写配置文件的类

``` php
class FileParams
{
    public function readParams($sourceFile)
    {
        //从sourceFile中读取文本参数
    }
    
    public function writeParams($params, $sourceFile)
    {
        //将参数写入sourceFile中
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
现在似乎又再次满足了需求，然而还没等我们松口气，产品说他希望我们还能支持yml格式的文件。。。这时候回过头研究一下代码，就会发现正是因为上面的代码其实没有遵守单一原则导致代码越来越难以维护，如果我们把上面的功能拆封到不同的类之中。。。

```php
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


