## 创建自己的工作空间
    工作空间是一个包含功能包，可编辑源文件或编译包的文件夹，简而言之，
    我们今后的编写的源码或github上下载的源码都在这里编译。 
    按照官网教程：

```
$ mkdir -p ~/catkin_ws/src
$ cd ~/catkin_ws/
$ catkin_make
```

    首先是创建一个文件夹catkin_ws，并在里面另创建一个src文件夹，这个src就是我们以后放源码的地方了，
    之后使用catkin_make来编译我们的工作空间。编译好之后就可以看到我们的工作空间除了之前 
    的src之外又多了两个文件夹build和devel。下面我们需要在bash里面添加我们工作空间的环境变量：
```
$ source devel/setup.bash
```

    这只是一次添加环境变量，也就是说关闭终端后这个环境变量就消失了，
    我们可以将自己工作空间的环境变量永久添加到bash里，这样就不必每次都敲上面代码，具体方法是：
```
sudo gedit ~/.bashrc
```
    首先通过上面命令进入自己的bash文件，然后在最后一行输入：
```
source /home/cm/catkin_ws/devel/setup.bash
```

## 创建ROS功能包

    如果你使用的是catkin编译系统，那么可以很容易地创建一个功能包。
    首先进入你的工作空间的src目录下：
```
$ cd ~/catkin_ws/src
```
    然后运行catkin_create_pkg命令：
```
$ catkin_create_pkg my_pkg std_msgs roscpp
```
    NOTE:可以使用tab补全命令。
    catkin_create_pkg的第一个参数是功能包的名字，
    其余的参数是该功能包的依赖项。命令格式如下所示：
```
$ catkin_create_pkg [package name] [depend1] [depend2] ...
```



## 编译ROS功能包
    如果你在功能包中写了一些代码，
    那么我们需要对该功能包进行编译：
```
$ cd ~/catkin_ws
$ catkin_make
```
    NOTE:catkin_make命令必须在工作空间下面使用，否则会报错。
    上面的命令是对工作空间中所有的功能包进行编译，
    如果想单独编译一个功能包，可以在catkin_make后使用必要的参数：
    
```
$ catkin_make --pkg [package name]
```
    编译好之后，最好运行下面的命令，
    这样的话你就可以通过包名来运行你的程序了：
```
. ~/catkin_ws/devel/setup.bash
```
    tip:我习惯于将上面的命令添加到.bashrc中，这样就不用每次运行这个命令了。
    
## 启动ROS
## 停止ROS
