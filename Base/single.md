# 1.1 设计原则－单一职责

**单一原则**(Single Responsibility Principle):每个类都应该有一个单一的功能，并且该功能应该由这个类完全封装起来。所有它的(这个类的)服务都应该严密的跟该功能平行(功能平行意味着**没有依赖**)。

单一职责是面向对象编程的首要原则之一，这告诉我们每个类都应该只有一个职责，它们应该是处理同一模块的集合，通过对类限制单一职责，更有利于我们划定类的边界，更具模块化的组织类。

```php
class ShopProduct 
{
    public function findAllProducts()
    {
        $conn = $this->getConnection();
        $sql = "";
        $conn->query($sql);
    }
    
    public function getConnection() 
    {
    }
}
```
上述例子是一个很经典的例子，ShopProduct类不符合单一职责，因为它承担了过多的职责，如果其他类也需要连接数据库，或者是数据库的连接方式发生改变都需要改变这个类，因此需要对这个类进行拆分，使其满足单一职责。

```php
class ShopProductService
{
    public function findAllProducts()
    {
        return $this->getShopProductDao()->findAppProducts();
    }
}
```



