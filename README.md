# 基本计算器

这是我使用 JAVA AWT 的简单计算器
 
  我还创建了一个 **_executable JAR FILE_** 它将在每个 JAVA 平台上通过 **双击** 运行
 
  ### 用于下载`CALC.jar`
 
在 MASTER 中你可以找到这个文件并下载它或者直接[点击这里](https://github.com/wanghao221/Calculator/blob/master/CALC.jar)
    
    
    
教程：https://haiyong.blog.csdn.net/article/details/118576545


## 🧿 关于AWT

AWT （抽象窗口工具包）是一个有助于构建 GUI 的 API （图形用户界面）基于 java 应用程序。GUI使用一些图形帮助用户交互。它主要由一组的类和方法所必需的，如在一个简化的方式创建和管理的GUI按钮，窗口，框架，文本框，单选按钮 等等

我所提供的Java代码对于动作监听器接口用于事件处理的计算器。

![在这里插入图片描述](https://img-blog.csdnimg.cn/20210708172705521.png =300x)


# 🎶 逻辑部分
## 🏀 1.对于数字按钮

```java
if(e.getSource()==b1){ //b1 代表数字 1
 zt=l1.getText();
  z=zt+"1";// 1 将合并在前一个值的末尾
  l1.setText(z);
}
```

当按下任何数字按钮时，标签 l1 中的任何值都将存储在变量 zt 中，然后与相应的数字连接，然后显示在标签 l1 中，对于 NEGATIVE 和 DECIMAL PTS 按钮，我们也做了类似的处理

## ✨ 2.对于算术按钮

```java
if(e.getSource()==badd){  //对应加法
    num1=Double.parseDouble(l1.getText());
  z="";
  l1.setText(z);
  check=1; 
}
```

现在，我们将标签 l1 的值转换为 double 类型后，将其存储到变量 num1 中，这在技术上将是第一个数字，然后将标签 l1 设置为 null

我们将只使用一个检查变量来获取这个特定的气动按钮（这里是 +）被点击，这样我们就可以在我们的 = 按钮中执行这个操作

## 🍖 3.对于等号按钮

```java
if(e.getSource()==bcalc){          
    num2=Double.parseDouble(l1.getText());
  if(check==1)
    xd =num1+num2;
  if(check==2)
    xd =num1-num2;
  if(check==3)
    xd =num1*num2;
  if(check==4)
    xd =num1/num2; 
  if(check==5)
    xd =num1%num2;    
  l1.setText(String.valueOf(xd));
}
```

现在再次将值存储 l1到 num2变量中，这将是算术上的第二个数字，然后检查变量的值，check然后进行相应的操作，然后在标签中显示结果 l1

## 🎥 4.对于清除按钮

```java
 if(e.getSource()==bclr){
  num1=0;
  num2=0;
  check=0;
  xd=0;
   z="";
   l1.setText(z);
   } 
```

此处将我们使用的所有变量更新为其默认值 0

并将标签 l1 设置为 null，以便我们之后可以开始新的计算

## 🏆 5.对于退格按钮

```java
 if(e.getSource()==bback){  
  zt=l1.getText();
  try{
    z=zt.substring(0, zt.length()-1);
    }catch(StringIndexOutOfBoundsException f){return;}
  l1.setText(z);
}
```

这里只是l1通过使用substring函数删除最后一位数字来更新值

并处理了一个 StringIndexOutOfBoundsException 当我们在标签中的值为 null 并且仍然按下返回按钮时发生的异常

## ⏰ 6.特殊插件功能
我所做的只是处理了 EQUAL 和所有 ARITHMETIC Buttons 中的一个异常，并根据情况打印了所需的消息

算术按钮：

```java
try{
    num1=Double.parseDouble(l1.getText());
    }catch(NumberFormatException f){
      l1.setText("Invalid Format");
      return;
    }
```

等于按钮：

```java
try{
    num2=Double.parseDouble(l1.getText());
    }catch(Exception f){
      l1.setText("ENTER NUMBER FIRST ");
      return;
    }
```

当我们将值转换为双精度值时，但可以说，标签 l1 具有空值（即标签为空）并且我们仍然按下这些按钮，然后它将生成 NumberFormatException execption，所以处理并打印所需的消息。

==例如==：

如果我点击1然后+然后我点击-而不是其他一些数字按钮，因此这是一个无效的格式，并且当-当时被点击时标签为空因此生成了execption所以只是处理它并在标签中打印无效格式

类似地，当标签为空时，并且在这种情况下单击 = ENTER NUMBER FIRST 将显示在标签内

至此，我们结束了本次 Java AWT 教程。

## 🍺 GIF演示

![在这里插入图片描述](https://img-blog.csdnimg.cn/2021070817253030.gif#pic_center)

# 😊 结尾想说的
所以只需通过代码并尝试一下。如果您在理解或使用代码方面有任何困难，请在下方评论询问。

如果你想下载并运行我的，我已经上传了源代码和可执行的 jar 包，你可以在这里找到：

[https://github.com/wanghao221/Calculator](https://github.com/wanghao221/Calculator) 如果你喜欢这份工作，可以点个star。

> 我已经写了很长一段时间的技术博客，并且主要通过CSDN发表，这是我的一篇技术文章/教程。我喜欢通过文章分享技术与快乐。请访问我的博客： [https://haiyong.blog.csdn.net/](https://haiyong.blog.csdn.net/) 以了解更多信息。希望你们会喜欢！这里汇总了我的全部原创及作品源码：[GitHub](https://github.com/wanghao221/)

如果你真的从这篇文章中学到了一些新东西，喜欢它，收藏它并与你的小伙伴分享。🤗最后，不要忘了❤或📑支持一下哦
