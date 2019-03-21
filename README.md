# MVVM
WPF中的MVVM-DEMO

#### MVVM （Model-View-ViewModel的简写）我的理解就是对UI和代码进行弱绑定。
#### 可以从百度搜到一大堆的解释，

## 总结起来，
## MVVM的特点&优点：
### 1.分离开发?UI和业务代码分离,擅长UI的程序员可以单独编写UI,擅长业务的编写业务
####  View指的是XAML布局文件,
####  ViewModel相当于原本的xxx.cs文件
####  Binding相当于 xxx.Text = "xxx"
####  Command相当于Click
####  当你修改XAML的时候根本不会影响到ViewModel中的代码和逻辑。
####  当你修改ViewModel.cs的时候也不会因为xxx_Click 而去修改XAML中的控件而心烦
  
### 2.模块化?
#### 

### 3.后期升级维护方便?

### 4.代码可读性高?
#### 使用Command 和 Binding 之后 代码可读性高

#### 

## MVVM的缺点&不足：
#### 1.事件机制不合理

#### 2.窗口控制不方便
#### 当你想从某个窗口跳转至某个窗口 或者 关闭当前窗口的时候,
#### 参考项目中 WindowHelper 用来执行窗口跳转。
#### 关闭窗口可以考虑
````xml
Command="{Binding CloseCommand}"
CommandParameter="{Binding RelativeSource={RelativeSource Mode=FindAncestor, AncestorType=Window}}"
````
````csharp
/// <summary>
/// 关闭窗口
/// </summary>    
public ICommand CloseCommand => new DelegateCommand(obj =>
{
    if (obj is Window window)
    {
        window.Close();
     }
});
````
