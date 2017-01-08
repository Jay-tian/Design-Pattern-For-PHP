# 1.1 UML类图

UML(Unified Modeling Language)中文称为统一建模语言，本文主要介绍类图中各个类之间的关系(泛化，实现，聚合等),和各个类之间线条和箭头所代表的含义其他具体请查看维基百科或其他资料。

## 泛化关系(generalization)

UML一般用“泛化”(generalization)来描述继承关系，这个关系用从子类到父类的一条线来标志性，线的顶端有一个空心闭合箭头。下图所示描述的是ShopProduct类和它的子类之间的关系：
![](/assets/generalization.jpg)

## 实现关系(realize)

UML用“实现”(realize)来描述接口和实现接口的类之间的关系,实现关系用一条带空心箭头的虚线表示。因此如果ShopProduct类实现了Chargeable接口，那它们的关系就如下所示：

![](/assets/realize.jpg)

## 关联关系(association)
当一个类的属性保存了对另一个类的实例(或多个实例)的引用时,就产生了关联，关系关系用直线来表示。如下图所示我们为Teacher类和Student类建立了模型，并创建了它们之间的关联
![](/assets/association.jpg)

事实上我们还可以用箭头来描述关联的方向，如果Teacher类拥有Student类的一个实例，但Student类没有Teacher类的实例，那么我们让关联箭头从Teacher类指向Student类这种关联称为单向关联
![](/assets/单向关联.jpg)

## 聚合关系(aggregation)和组合关系(composition)
与关联很相似，聚合和组合都描述了一个类长期持有其他类的一个或多个实例的情况，被


## 依赖关系(dependency)