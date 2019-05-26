# HW4 利用OpenGL设计贪吃蛇游戏

#### 任务介绍
- 贪吃蛇游戏：玩家控制贪吃蛇在游戏区域里驰骋，避免碰到自己或障碍物，尽可能地吃更多的食物以生长！

##### 游戏玩法：
- WASD控制蛇的移动
- 游戏开始，每隔一定时间会在地图空闲位置刷新一个食物，蛇触碰到食物后食物消失，蛇会增加一个单位的长度
- 当蛇触碰到自己或者障碍物，则游戏失败
- 当蛇接触到地图边界，蛇会在地图另一端重新进入地图

#### 开发环境
- OpenGL3
- GLFW
- GLAD

#### 要求：
1. 完成贪吃蛇游戏的框架搭建（60%）
2. 完成蛇以及食物的 **3D** 精灵加载和渲染，其中模型可以用简单的纯色几何模型实现如立方体、球体；或者网上下载合适的3D模型如[Apple-Poly](https://poly.google.com/view/5hRReRDr0v4)、[Snake-Poly](https://poly.google.com/view/2ovwPNrRijL)（20%）
3. 实现蛇的控制（20%）
4. Bonus：蛇的碰撞检测与响应

#### 类的设计
1. 设计食物的类:
![food](https://github.com/erosWu/homework-picture/blob/master/HW4/food.png?raw=true)
（因为食物只需要记载他自己的位置用来判断是否被蛇吃掉，所以只需要构造函数即可）

2. 设计贪吃蛇的类：
![snake](https://github.com/erosWu/homework-picture/blob/master/HW4/snake.png?raw=true)
（贪吃蛇需要对自身进行移动，吃食物以后会增加自身长度，移动等操作;同时自定义四个枚举变量表示蛇运动的四个方向）

#### 具体实现
1. 控制蛇的运动（需要注意的是，碰到边界不算碰撞，会穿过边界从另一边出来）
![snake](https://github.com/erosWu/homework-picture/blob/master/HW4/move.png?raw=true)

2. 键入信息后控制蛇的转向
![snake](https://github.com/erosWu/homework-picture/blob/master/HW4/turn.png?raw=true)

3. 蛇吃到食物后的变化
![snake](https://github.com/erosWu/homework-picture/blob/master/HW4/eat.png?raw=true)

4. 蛇自身的碰撞检测（因为蛇不会与边界发生碰撞，所以只需要检测蛇头是否碰到身体即可）
![snake](https://github.com/erosWu/homework-picture/blob/master/HW4/collision.png?raw=true)

5. 在OpenGL中渲染生成蛇和食物
![generate](https://github.com/erosWu/homework-picture/blob/master/HW4/generate.png?raw=true)

6. 控制蛇的速度
```

// 减慢蛇的运行速度（根据不同电脑自己的情况设置，否则蛇的运动速度可能会很快）
usleep(60000);


```
这部分要根据自己的电脑情况进行调整

7. 重新编写CMakeLists文件完成工程即可

#### 结果展示
1. 纵向运行
![move](https://github.com/erosWu/homework-picture/blob/master/HW4/up.png?raw=true)

2. 横向运行
![move](https://github.com/erosWu/homework-picture/blob/master/HW4/left.png?raw=true)

3. 吃掉食物后身体变长的蛇
![move](https://github.com/erosWu/homework-picture/blob/master/HW4/long.png?raw=true)

4. 吃到自己的身体，游戏结束
![move](https://github.com/erosWu/homework-picture/blob/master/HW4/out.png?raw=true)

#### 参考资料

1. [OpenGL游戏-框架设计](https://learnopengl.com/In-Practice/2D-Game/Setting-up)
2. [OpenGL游戏-精灵渲染](https://learnopengl.com/In-Practice/2D-Game/Rendering-Sprites)
3. [OpenGL游戏-碰撞检测](https://learnopengl.com/In-Practice/2D-Game/Collisions/Collision-detection)
4. [OpenGL模型创建](https://learnopengl.com/Getting-started/Hello-Triangle)
5. [Google Poly-3D模型库](https://poly.google.com)
