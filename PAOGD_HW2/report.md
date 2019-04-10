## PAOGD_HW2 实验报告

#### 介绍
PAOGD个人作业2-角色动画基础

#### 开发环境
Blender2.8 beta

#### 场景描述

实现一个简单的行走循环动画

![HW2.gif](https://github.com/erosWu/homework-picture/blob/master/PAOGD_HW2/HW2.gif?raw=true "HW2.gif")


#### 具体实现
1. 首先导入我们需要用到的人体模型
![导入模型](https://github.com/erosWu/homework-picture/blob/master/PAOGD_HW2/import.png?raw=true "import")
2. 为人体模型添加相应的骨骼以控制模型的行走
![插入骨骼](https://github.com/erosWu/homework-picture/blob/master/PAOGD_HW2/insert_bone.png?raw=true "insert")
在插入骨骼的过程中要注意骨骼的命名规范
![命名规范](https://github.com/erosWu/homework-picture/blob/master/PAOGD_HW2/name_stander.png?raw=true "name_standerd")
这有利于我们的操作，比如：对称操作
![对称操作](https://github.com/erosWu/homework-picture/blob/master/PAOGD_HW2/symatry.png?raw=true)
我们可以先做好左侧的手臂骨骼，然后使用对称功能自动生成右边骨骼。
还要额外添加一组pole骨骼用于控制膝盖的方向，防止模型在行走过程中出现古怪的动作。
![pole](https://github.com/erosWu/homework-picture/blob/master/PAOGD_HW2/pole.png?raw=true)
3. 为小腿添加反向动力学组件，控制行走的基础过程
![IK](https://github.com/erosWu/homework-picture/blob/master/PAOGD_HW2/ik.png?raw=true)
P.S.：一定要注意链长的设定为2，否则控制身体的骨骼也会随着脚掌的移动而改变
还需要注意的是，我们要取消foot和leg之间的父子关系，并将leg的IK约束定到foot上，如此一来，通过控制脚掌，我们就能控制小腿和大腿的变化：
![change](https://github.com/erosWu/homework-picture/blob/master/PAOGD_HW2/change.png?raw=true)
4. 给小腿添加极向目标，调整极向角度，确保膝盖在正常的方向
![pole_angle](https://github.com/erosWu/homework-picture/blob/master/PAOGD_HW2/pole_angle.png?raw=true)
5. 将骨骼与人物模型绑（两种方法）
* 选中人物模型，在属性栏中选中修改器选项：
![modifier](https://github.com/erosWu/homework-picture/blob/master/PAOGD_HW2/modifier.png?raw=true)
在修改器中选择添加修改器，并选择形变中的骨架：
![transform](https://github.com/erosWu/homework-picture/blob/master/PAOGD_HW2/transform.png?raw=true)
然后我们进入权重模式，选中对应的骨骼，自行涂抹权重
![weight_paint](https://github.com/erosWu/homework-picture/blob/master/PAOGD_HW2/weight_paint.png?raw=true)
* 第二种方法是一个特别方便的功能是自动分配权重，如此一来我们就不用进入权重模式自行涂权重，而且这一功能还会为我们自动分配骨骼组
首先我们需要将骨骼与人物模型都选中（复选按键为shift）
![选中](https://github.com/erosWu/homework-picture/blob/master/PAOGD_HW2/choose.png?raw=true)
然后按下ctrl + P 使用关系菜单，选中骨架形变中的附带自动权重。
![权重](https://github.com/erosWu/homework-picture/blob/master/PAOGD_HW2/weight.png?raw=true)
这样一来，blender不仅为我们自动分配了骨骼组，还为每个骨骼组都配置了相应的权重，十分便捷
![auto_weight](https://github.com/erosWu/homework-picture/blob/master/PAOGD_HW2/auto_weight.png?raw=true)

完成上述操作后，我们就可以发现，改变骨骼的形状，人物模型也会跟着改变。
![obj_change](https://github.com/erosWu/homework-picture/blob/master/PAOGD_HW2/obj_change.png?raw=true)

6. 制作原地走路动画
    * 我们可以将走路这一过程分为5个阶段
    ![phase1](https://github.com/erosWu/homework-picture/blob/master/PAOGD_HW2/phase1.png?raw=true)
    ![phase2](https://github.com/erosWu/homework-picture/blob/master/PAOGD_HW2/phase2.png?raw=true)
    ![phase3](https://github.com/erosWu/homework-picture/blob/master/PAOGD_HW2/phase3.png?raw=true)
    ![phase4](https://github.com/erosWu/homework-picture/blob/master/PAOGD_HW2/phase4.png?raw=true)
    ![phase5](https://github.com/erosWu/homework-picture/blob/master/PAOGD_HW2/phase5.png?raw=true)
    进入dope sheet（动画编辑表界面）:
    ![dopesheet](https://github.com/erosWu/homework-picture/blob/master/PAOGD_HW2/dopesheet.png?raw=true)
    我们分别在时间轴上的五个点钟插入这五个关键帧（不难发现第一个阶段和第三个阶段正好是完全对称的，我们可以再时间轴上通过ctrl+C完成复制，然后在对应的时间轴上通过ctrl+shift+V来进行对称粘贴）完成这一操作后我们就已经有一个走路的基础模型了
    
    * 为了让这一个过程进行循环，我们进入NIA界面:
    ![NIA](https://github.com/erosWu/homework-picture/blob/master/PAOGD_HW2/NIA.png?raw=true)
    在dopesheet中将设置好的动画取名，然后点击Push Down按钮，就可以发现我们的动作在NIA中出现了（因为我已经完成了push操作，dopesheet中并没有动画的帧）
    ![NIA_](https://github.com/erosWu/homework-picture/blob/master/PAOGD_HW2/NIA_.png?raw=true)
     ![walkcycle](https://github.com/erosWu/homework-picture/blob/master/PAOGD_HW2/walkcycle.png?raw=true)
     通过点击N弹出的动画数据工具栏，我们可以调整动作重复的次数，整个动作过程所占据的帧数等属性
     ![property](https://github.com/erosWu/homework-picture/blob/master/PAOGD_HW2/property.png?raw=true)

7. 制作完整的走路动画
    * 在人物脚底下添加一个空物体，并让他呈现坐标轴的样式
    ![axe](https://github.com/erosWu/homework-picture/blob/master/PAOGD_HW2/axe.png?raw=true)
   ![axe_](https://github.com/erosWu/homework-picture/blob/master/PAOGD_HW2/axe_.png?raw=true)
   * 选中坐标轴和人物模型并将他们绑定（注意此时要选择保持变换）
   ![keep](https://github.com/erosWu/homework-picture/blob/master/PAOGD_HW2/keep.png?raw=true)
   * 改变坐标轴的位置，并对他进行旋转，然后在在dopesheet中插入关键帧
   * 打开曲线编辑器，可以编辑人物在每个方向上行走的速度，进行适当的调整，让走路过程看起来更加自然
   ![graph](https://github.com/erosWu/homework-picture/blob/master/PAOGD_HW2/graph.png?raw=true)
   * 重复之前走路动画的操作，在NIA中调整属性进行循环即可
   ![repeat](https://github.com/erosWu/homework-picture/blob/master/PAOGD_HW2/repeat.png?raw=true)
