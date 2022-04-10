#  JAVA面向对象程序设计知识速过

## 														————MOOC翁恺

**一、封装**

​	封装简单理解就是将数据和操作打包在一起

**二、包**

* default(默认状态，什么都没有)： 仅在同一包内可见。使用对象：接口、变量、方法。
* private ：仅在同一类中可见。
* protected ：不太好说。。。。也不太懂
* public ：对所有包和类都可见。

代码文件开头的improt是引用包,这样就可以使用这个包中非private修饰的函数或变量。

**三、static**

* 类中声明带static的变量称为类变量，他是可以由类直接调用，而普通的成员变量是不能直接使用的，

  必须创建一个对象调用。例如：

  ```java
  public class Display{
      private int value = 0;
      private static int step = 1;
      
      public Display(int value){
          this.value = value;
      }
      
      public static void main(String[] args){
          Display.step = 2;	//对
        	Display.value = 2;	//错
          //成员变量的使用必须是先创建该类的对象然后用这个对象调用
          Display display = new Display(10);
          display.value = 2;	//对
          //所以我们称带上static的变量为类变量
      }
  }
  ```

* 此外，类变量的效果如其名，只针对类，不针对对象，只要值一改变，整个类中的值都改变。

  ```java
  //接上
  Display.step = 3 ;
  System.out.println(Display.step);
  System.out.println(display.step);
  /*结果:
  3
  3
  */
  display.step = 1;
  System.out.println(Display.step);
  System.out.println(display.step);
  /*结果:
  1
  1
  */
  ```

**四、接口**

