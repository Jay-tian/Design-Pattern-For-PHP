# 1.1 UML类图

UML(Unified Modeling Language)中文称为统一建模语言，本文主要介绍类图中各个类之间的关系（泛化，实现，聚合等）其他具体请查看维基百科或其他资料。

## 泛化关系(generalization)

UML一般用“泛化”(generalization)来描述继承关系，这个关系用从子类到父类的一条线来标志性，线的顶端有一个空心闭合箭头,如下图所示描述的是A继承B

![](/Static/generalization.jpg)

## 实现关系(realize)

UML用“实现”(realize)来描述接口和实现接口的类之间的关系,实现关系用一条带空心箭头的虚线表示

## 关联关系(association)

当一个类的属性保存了对另一个类的实例(或多个实例)的引用时,就产生了关联 我们可以用箭头来描述关联方向。

## 聚合关系(aggregation)

## 组合关系(composition)

## 依赖关系(dependency)