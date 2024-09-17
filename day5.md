1. [leetcode 两数相加](https://leetcode.cn/submissions/detail/558964005/)
2. **Java Exception**
   1. try catch finally: 执行顺序: try -> catch -> finally，finally 无论是否出现异常都会执行，catch捕获异常后，程序不会中止
   2. throw and throws，将异常抛出，可以是自定义的异常，也可以是catch捕获的异常，throw 只能抛出一个异常，throws 可以抛出多个，**throws 只能出现在方法声明中，throw 可以在方法体中出现**，throws将异常交给调**用它的函数处理**，throw**将异常抛出**，自己处理。
   3. finally不执行的情况: 
      1. 在finally中调用了System.exit(0)或者Runtime.getRuntime().halt(0)，
      2. 程序终止，return
      3. 线程中断
   4. 内部类：主要是使用接口创建对象的方式，还有lamuda表达式创建对象的方式
