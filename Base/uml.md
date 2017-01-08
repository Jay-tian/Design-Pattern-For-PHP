# 1.1 UML类图

UML(Unified Modeling Language)中文称为统一建模语言，本文主要介绍类图中各个类之间的关系(泛化，实现，聚合等),和各个类之间线条和箭头所代表的含义其他具体请查看维基百科或其他资料。

## 泛化关系(generalization)

UML一般用“泛化”(generalization)来描述继承关系，这个关系用从子类到父类的一条线来标志，线的顶端有一个空心闭合箭头。下图所示描述的是ShopProduct类和它的子类之间的关系：
![](/assets/generalization.jpg)

## 实现关系(realize)

UML用“实现”(realize)来描述接口和实现接口的类之间的关系,实现关系用一条带空心箭头的虚线表示。因此如果ShopProduct类实现了Chargeable接口，那它们的关系就如下所示：

![](/assets/realize.jpg)

## 关联关系(association)
当一个类的属性保存了对另一个类的实例(或多个实例)的引用时,就产生了关联，关联关系用直线来表示。如下图所示我们为Teacher类和Student类建立了模型，并创建了它们之间的关联
![](/assets/association.jpg)

事实上我们还可以用箭头来描述关联的方向，如果Teacher类拥有Student类的一个实例，但Student类没有Teacher类的实例，那么我们让关联箭头从Teacher类指向Student类这种关联称为单向关联
![](/assets/单向关联.jpg)

## 聚合关系(aggregation)和组合关系(composition)
与关联很相似，聚合和组合都描述了一个类长期持有其他类的一个或多个实例的情况，通过聚合和组合，被引用的实例成为引用对象的一部分。

在聚合的情况下，被包含的对象是容器的一个核心部分，但是它们也可以同时被其他对象所包含。聚合关系一般用一条菱形开头的线表示。

如下图所示，学生组成了一个班级，但是相同的学生对象可以被不同的班级实例引用，当我们要删掉一个班级类时不需要删除它所引用的这些学生类，因为学生还可以加入其它班级

![](/assets/aggregation.jpg)

组合则是一个更强的关系，被包含对象只能被它的容器引用，当容器被删除时，它也应该被删除。组合关系一般用一条带实心菱形箭头直线表示
![](/assets/composition.jpg)

Person类持有一个SocialSecurityData对象的引用，而该SocialSecurityData对象实例只属于包含它的Person类

## 依赖关系(dependency)
一个对象使用另一个对象的关系被描述为一个依赖关系，依赖关系由一条连接俩个类的实线和开放箭头表示。与关联关系不同的是，它是一种临时性的关系，通常在运行期间产生，并且随着运行时的变化； 依赖关系也可能发生变化。

![](/assets/dependency.jpg)

Report类使用了ShopProductWriter对象
注：在最终代码中，依赖关系体现为类构造方法及类方法的传入参数，箭头的指向为调用关系；依赖关系除了临时知道对方外，还是“使用”对方的方法和属性；