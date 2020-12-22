# TI2020_F_F407part
2020TI杯全国大学生电子设计大赛F题解决方案F407部分

视觉方案：https://github.com/bossConneR/K210_FACEDET

数据处理：https://blog.csdn.net/C_______________/article/details/109111308

CSDN博客：https://blog.csdn.net/Mol666/article/details/111529702

LAST UPDATE: 22/12/2020

|  Author   | Mol Chan  |
|  ----  | ----  |
|  QQ-mail | coco.yyyy@qq.com |
|  G-mail | chanmol666@gmail.com |

## Introduction

2020TI杯全国大学生电子设计大赛F题解决方案F407部分，与视觉部分和数据处理部分共同组成最终成品。

图片见**End Product**

## Details

- 人脸识别和口罩识别已经交由K210处理，只需处理K210返回的信号。F407主要承担测温、显示、报警的功能。

- 测温采用MLX90614红外测温传感器,核心函数在于温度转换。float SMBus_ReadTemp(void)函数将测得的光学信号，换算成温度。详见数据处理部分。

- 并口通信部分，F407和K210直连两个引脚，K210引脚做输出，F407引脚输入。一脚是数据有效脚，一脚是数据脚。其原理类似于IIC通信的SCL和SDA。详见源码port_detect()。其次还有F407和K210各两个引脚接两个外部按键电路，均作输入。用于切换，口罩识别模式和身份识别模式，测人体温、杯壁温度和水温度。
