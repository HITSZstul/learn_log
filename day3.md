1. 面向对象中object的toString和equals方法，以及其子类的重写
2. 向下转型和向上转型：
   - 向下转型：父类引用指向子类的对象，向下转型
   - 向下转型的例子是使用敌机父类，定义了精英敌机，普通敌机，boss敌机等子类对象。
   - 向上转型：子类引用指向父类的对象，向上转型
   - 在object类中，**对equal和toString的方法重写**的过充中，就是运用了向上转型：
   - ```java
        public boolean equals(Object o) {
            if (this == o) return true;
            if (!(o instanceof student student)) return false;
            return age == student.age && Objects.equals(name, student.name);
        }

        public boolean equals(Object o) {
            if (this == o) return true;
            if (o == null || getClass() != o.getClass()) return false;
            if (!super.equals(o)) return false;
            student student = (student) o;//这里即运用了向上转型
            return age == student.age && Objects.equals(name, student.name);
        }
    ```
3. 抽象类和抽象方法：抽象类有0到n个抽象方法，抽象类不能实例化，只能被继承。抽象类就是为了给子类提供统一的模板，子类必须实现抽象方法，子类可以扩展抽象类。
4. 对子类进行了统一后，在向下转型时，就可以通过创建不同的子类，但**只用抽象父类的引用**，就可以调用不同子类的方法。
5. 例子就是在飞机大战中，敌机父类，定义了精英敌机，普通敌机，boss敌机等子类对象。创建对象时**统一使用父类的引用**，在实现敌机的不同action时，也是通过父类的引用，调用不同的子类方法，从而实现了多态。
6. 子类对象初始化时，会先调用**父类的构造方法**，再调用子类的构造方法。
7. 接口中的defauft方法，可以不用实现，也可以重写。
8. 增加public default方法的**原因**：为了解决在方法中增加一个新的方法，对现有类造成的影响。
9. 接口中只有**抽象方法**和**final修饰的变量**