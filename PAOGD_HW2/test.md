## PAOGD_HW2 实验报告

#### 介绍
PAOGD个人作业2-角色动画基础

#### 开发环境
Blender2.8 beta

#### 场景描述

实现一个简单的行走循环动画

![HW2.gif](./HW2.gif "HW2.gif")


#### 具体实现
1. 首先导入我们需要用到的人体模型
![导入模型](https://github.com/erosWu/homework-picture/blob/master/PAOGD_HW2/import.png "import")
2. 为人体模型添加相应的骨骼以控制模型的行走
![插入骨骼](https://github.com/erosWu/homework-picture/blob/master/PAOGD_HW2/insert_bone.png "insert")
在插入骨骼的过程中要注意骨骼的命名规范
![命名规范](https://github.com/erosWu/homework-picture/blob/master/PAOGD_HW2/name_stander.png "name_standerd")
这有利于我们的操作，比如：对称操作
![对称操作](https://github.com/erosWu/homework-picture/blob/master/PAOGD_HW2/symatry.png)
我们可以先做好左侧的手臂骨骼，然后使用对称功能自动生成右边骨骼。
还要额外添加一组pole骨骼用于控制膝盖的方向，防止模型在行走过程中出现古怪的动作。
![pole](https://github.com/erosWu/homework-picture/blob/master/PAOGD_HW2/pole.png)
3. 为小腿添加反向动力学组件，控制行走的基础过程
![IK](https://github.com/erosWu/homework-picture/blob/master/PAOGD_HW2/ik.png)
P.S.：一定要注意链长的设定为2，否则控制身体的骨骼也会随着脚掌的移动而改变
还需要注意的是，我们要取消foot和leg之间的父子关系，并将leg的IK约束定到foot上，如此一来，通过控制脚掌，我们就能控制小腿和大腿的变化：
![change](https://github.com/erosWu/homework-picture/blob/master/PAOGD_HW2/change.png)
4. 给小腿添加极向目标，调整极向角度，确保膝盖在正常的方向
![pole_angle](https://github.com/erosWu/homework-picture/blob/master/PAOGD_HW2/pole_angle.png)
5. 
