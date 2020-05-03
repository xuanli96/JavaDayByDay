# JavaDayByDay
## Java基础
### day 01：关键字、标志符、常量、变量、运算符、方法、jdk9
### day 02: 选择循环语句，IDEA，方法重载
### day 03：数组，类与对象、封装、构造方法、常用的api类
### day 04
#### 继承
1.父类只能使用父类的东西，不知道子类的内容，只有子类知道父类的内容。<br>
2.父子类继承变量重名，创建子类对象是，访问有两种方式：直接通过子类对象访问成员变量，等号左边是谁，就优先用谁，没有则向上找；间接通过成员方法访问成员变量，该方法属于谁就优先用谁，没有则向父类找，不会向子类找。<br>
3.区分子类方法中重名的三种变量：局部变量：直接写成员变量；本类的成员变量：this.成员变量；父类的成员变量：super.成员变量。<br>
4.在父子类的继承关系中，创建子类对象，访问成员方法的规则：（重名时）创建的对象是谁，就优先用谁，没有则向父类找，不会向子类找。<br>
5.方法的重写（Override）<br>
在继承关系中，方法的名称一样，参数列表也一样。创建的是子类对象，则有先用子类方法。@Override，写在方法前面，用来检测是不是有效的正确覆盖重写（可选）<br>
子类方法的返回值必须小于等于父类方法返回值范围.java.lang.Object类是所有类的公共最高父类，java.lang.String类是Object类的子类<br>
子类方法的权限必须大于等于父类方法的权限修饰符，public>protected>(default)>private，default不是关键字，而是什么都不写，留空。<br>
6.重写（Override）和重载（Overload）区别：重载是发生在继承关系当中，方法名称一样，参数列表也一样。重载方法名称一样，参数列表不一样。<br>
7.继承中构造方法的访问特点：先执行父类构造方法，后执行子类构造方法。子类构造方法中有一个默认的super（）调用，所以一定是先调用的父类构造，后执行子类构造。子类构造方法可以通过super关键字来调用父类构造重载。只有子类构造方法，才能调用父类构造方法，普通方法不可以。不过一个子类构造调用多次super构造。<br>
8.super关键字三种用法：在子类的成员方法中，访问父类的成员变量；在子类的成员方法中，访问父类的成员方法；在子类的构造方法中，访问父类的构造方法<br>
9.this关键字的三种方法：在本类的成员方法中，访问本类的成员变量；在本类的成员方法中，访问本类的另一个成员方法；在本类的构造方法中，访问本类的另一个构造方法，this(...)调用也必须是构造方法的第一个语句，唯一一个，super和this两种构造调用，不能同时使用；<br>
10.super和this关键字图解<br>
11.Java继承的三个特征：Java语言是单继承的，一个类的直接父类只能有唯一一个；Java语言可以多级继承；一个子类的直接父类是唯一的，但是一个父类可以拥有很多个子类。<br>
#### 抽象类、抽象方法<br>
1.抽象方法：加上abstract关键字，然后去掉大括号，直接分号结束<br>
2.抽象类：抽象方法所在的类，必须是抽象类才行，在class之前写上abstract即可<br>
3.如何使用抽象类和方法：不能直接创建new抽象类对象；必须用一个子类来继承抽象父类；子类必须覆盖重写父类当中所有的抽象方法，覆盖重写的实现是去掉抽象方法的abstract的关键字，然后补上方法体大括号；创建子类对象进行使用。<br>
4.发红包案例<br>

### day 05
#### 接口
1.多个类的公共规范；是一种引用数据类型，最重要的内容就是其中的抽象方法；<br>
2.如果是Java7，那么接口中可以包含有常量、抽象方法，如果是Java8，还可以额外包含默认方法、静态方法，Jva9，还可以包含私有方法。<br>
3.接口中的抽象方法，修饰符必须是两个固定的关键字：public abstract，这两个关键字修饰符，可以选择性的省略。<br>
4.接口使用步骤：接口不能直接使用，必须有一个实现类来实现该接口；接口的实现类必须覆盖重写接口中所有的抽象方法；创建实现类的对象，进行使用。（如果实现类并没有覆盖重写接口中所有的抽象方法，那么这个实现类自己就必须是抽象类）<br>
5.Java8开始，接口里允许定义默认方法，public defualt ，接口的默认方法，可以通过接口实现类对象，直接调用，接口的默认方法，也可以被接口实现类进行覆盖重写<br>
6.Java8开始，接口里允许定义静态方法。public static 返回值类型 方法名称（参数列表）{方法体}。不能通过接口实现类的对象来调用接口中的静态方法；通过接口名称直接调用其中的静态方法。接口名.接口方法（）；<br>
7.需要抽取一个共有方法，用来解决两个默认方法之间重复代码的问题，但是这个共有方法不应该让实现类使用，应该是私有化的。Java9，接口中定义私有方法。普通私有方法，解决多个默认方法之间重复代码问题，private 返回值类型 方法名称（参数列表）{方法体}；静态私有方法，解决多个静态方法之间重复代码问题，private static 返回值类型 方法名称（参数列表）{方法体}<br>
8.接口当中也可以定义“成员变量”，但是必须使用public static final 三个关键字进行修饰。从效果上看，这其实就是接口的常量。格式：public static final 数据类型 常量名称=数据值；一旦使用final关键字进行修饰，说明不可改变；接口当中的常量，可以省略public static final，但照样是常量；接口中的常量，必须进行赋值，不能不赋值；接口中常量的名称，使用完全大写的字母，用下划线进行分隔<br>
9.在Java9+版本中，接口的内容可以有：<br>
成员变量其实是常量，格式：public static final 数据类型 常量名称=数据值，常量必须进行赋值，而且一旦赋值就不能改变，常量名称完全大写，用下划线进行分隔；<br>
接口中最重要的就是抽象方法，格式：public abstract 返回值类型 方法名称（参数列表）{方法体} 实现类必须覆盖重写接口所有的抽象方法，除非实现类是抽象类；<br>
Java8开始，接口里允许定义默认方法，public defualt 返回值类型 方法名称（参数列表）{方法体}，接口的默认方法，可以通过接口实现类对象，直接调用，接口的默认方法，也可以被接口实现类进行覆盖重写；<br>
Java8开始，接口里允许定义静态方法。public static 返回值类型 方法名称（参数列表）{方法体}，不能通过接口实现类的对象来调用接口中的静态方法，通过接口名称直接调用其中的静态方法。接口名.接口方法（）；<br>
Java9，接口中定义私有方法，普通私有方法，解决多个默认方法之间重复代码问题，private 返回值类型 方法名称（参数列表）{方法体}；静态私有方法，解决多个静态方法之间重复代码问题，private static 返回值类型 方法名称（参数列表）{方法体}<br>
10.接口使用注意事项：<br>
接口不能有静态代码块；<br>
接口不能有构造方法；<br>
一个类的直接父类是唯一的，但是一个类可以同时实现多个接口，public class MyinterfaceImpl implements MyInterfaceA，MyInterfaceB{//覆盖重写许所有抽象方法}；<br>
如果实现类所实现的多个接口中，有重名的抽象方法，那么只需要需改重写一次即可；<br>
如果实现类没有覆盖重写所有接口当中的所有抽象方法，实现类必须是抽象类；<br>
如果实现类实现的多个接口当中，存在重复的默认方法，那么实现类一定要对冲突的默认方法进行覆盖重写；<br>
一个类如果直接父类当中的方法，和接口当中的默认方法产生了冲突，优先用父类当中的方法；<br>
11.接口之间的多继承：类与类之间是单继承的，直接父类只有一个；类与接口之间是多实现的，一个类可以实现多个接口；接口与接口之间是多继承的；多个父接口当中的抽象方法如果重复，没关系；多个父接口当中的默认方法如果重复，那么子接口必须进行默认方法的覆盖重写，而且要带着default关键字<br>
#### 多态
1.extends继承火车implements实现，是多态性的前提。对象拥有多种形态，叫多态性。<br>
2.代码中体现多态性，父类引用指向子类对象，父类名称 对象名=new 子类名称（）；或者 接口名称 对象名=new 实现类名称（）；<br>
3.多态中成员变量的使用特点：访问成员变量的两种方式：直接通过对象名称访问，看等号左边是谁，优先用谁，没有则向上找，不能向下找；间接通过成员方法访问，看该方法属于谁优先用谁，没有则向上找，如果子类没有覆盖重写，就是父类方法，如果子类覆盖重写，就是子类方法；成员变量不能覆盖重写；编译看左边，运行还看左边。<br>
4.多态中成员方法的使用特点：看new的是谁，就优先用谁，没有则向上找；编译看左边，运行看右边，如果左边没有调用的方法，则编译器报错，成员变量不在此列。<br>
5.多态性的优点<br>
6.对象的向上转型：图，对象一旦向上转型为父类，那么无法调用子类原本持有的内容，解决办法，用对象的向上转型还原<br>
7.instanceof：如果希望调用子类特有方法，需要向下转型<br>
