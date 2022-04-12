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

### 四、接口和ArrayList

* 用于人机交互和业务逻辑，就是UI和业务逻辑，通过接口实现

```java
public class NoteBook {
    //泛型类，容器类  储存对象
    private ArrayList<String> notes = new ArrayList<String>();
    private int size = 0;
   
    public void add(String s){
    	notes.add(s);
        //notes.add() 是ArrayList中的方法    
    }
    
    public void add(String s,int location){
        notes.add(location,s);
        //将加入的字符串放在数组的几号位
        //如果该位置已经存放了东西，那么这些东西就会后移一位
    }
    
    public int getSize(){
        return notes.size();
        //notes.size()也是ArrayList中的方法
    }
    
    public String getNote(int index){
		return notes.get(index);
    }
    
    public void removeNote(int index){
        notes.remove(index);
    }
    
    public String[] list(){
        String[] a = new String[notes.size()]
        for(int i = 0; i < notes.size(); i ++ ){
			a[i] = notes.get(i);
        }
        return a;
    }
    
    public static void main(String[] args){
        NoteBook nb = new NoteBook();
        nb.add("first");
        nb.add("second");
        System.out.println(nb.getSize());
        String[] a = nb.list();
        for(String s : a){
            System.out.println(s);
            
        }
        
    }
    
}
```

### 五、对象数组

```java
String[] a = new String[10];
```

* 对象数组中的每个元素都是对象的管理者而非对象本身(每个管理者都管理着一个字符串)

### 六、ArrayList和HashSet

```java
ArrayList<String> a = new ArrayList<String>();
HashSet<String> s = new HashList<String>();
```

ArrayList 存储字符串是堆积。

HashSet 储存字符串 是集合，如果有一样的东西，后面的就会替代前面的。

```java
public String toString(){
	return ""+i;
}
```

问题：为什么加入这个和没加入这个有区别？

​	没加入前打印的是地址，加入后打印的是变量，而且加入后是自动调用。

打印对象b的时候，构造函数内的自动会调用初始化，还自动调用了toString()

CSDN：

为什么toString 方法会自动被调用？

这个问题其实比较简单的，大家可以直接看 Java 中相关类的源代码就可以知道了。

public static String valueOf(Object obj) 方法
参数： obj 

返回：

       如果参数为 null， 则字符串等于 "null"；
    
       否则， 返回 obj.toString() 的值
现在的问题是，当用户调用 print 或 println 方法打印一个对象时，为什么会打印出对象的 toString()方法的返回信息。

解决：

​	1.这个是 Ojbect 中的 toString()方法，toString ()方法会打印出 return 信息。

​	2.这两个方法是 System.out.print 和 println()方法传入一个 Object 类对象时打印 的内容，当然，传入其它类时，同样如此。 

### 七、子父类

* Java中不存在对象给对象的赋值。

* 子类的对象可以给父类的变量赋值。

* 父类的对象不能给子类的变量赋值。

  我的理解是，子类的属性包括了父类的，还有更多的属性，所以子类的属性种类住够给父类套上，然而父类的属性种类不够子类的，这样赋值时就会产生未赋值的属性，产生错误。

  ```java
  //视频中的代码
  //CD是Item的子类
  Item item = new Item("a",0,true,"...");
  CD cd = new CD("a","a",0,0,"...");
  /* 1 */
  item = cd;   
  CD cc = (CD) item;
  
  /* 2 */
  //item = cd;
  CD cc = (CD) item;
  //为什么没写上面一句就报错了，这个地方还是有点不懂，位于视频的向上造型这一集6分19秒
  //在我重新看了五遍之后，我听到了一句话，“取决于你那个被造型变量当时实际所管理的类型是什么”，所以1处的item所管理的是个CD类型，因此能够被造型。而2处的item所管理的还是Item类型，因此由上面的三条中的最后一条结论可知，父类的对象是不能给子类的变量赋值，所以报错了。
  ```

  介于上面三点，对象不可以给对象赋值，1处我理解为将cd的变量值赋给item，而不是把这个对象赋给它。

  

  * 造型和类型转化，在基本类型里是类型转化，例如int ,double。在对象中是叫做造型。

