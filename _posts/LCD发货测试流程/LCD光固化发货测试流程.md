# LCD光固化发货测试流程

### 环境搭建

##### 准备材料

- 已烧录好最新镜像文件的TF卡1张；


- H3主板1块;

- 可以正常显示的曝光屏一块以及配套电源；

- 已烧录好最新Hex的Solo主板或Dual主板1块;

- 已烧录好最新镜像文件和光固化软件的核心板1块;

- 触摸屏1块，屏幕排线1条;

- HDMI连接线1条;

- 带Micro USB接口的数据线1条;

- 4988驱动1个，步进电机1个，碰撞开关1个；

- 12V电源1个；

- 带有CWS测试文件的U盘或SD卡；

  ​

##### 接线

* TF卡插H3主板卡槽；
* 核心板插Solo主板或Dual主板插槽；
* 4988模块插Solo主板或Dual主板Z轴插槽，**注意4988模块上箭头指向主板外沿**；
* 步进电机接Solo主板或Dual主板Z轴电机接口；
* 碰撞开关接Solo主板或Dual主板Z Min接口；
* 用排线连接触摸屏与Solo主板或Dual主板；
* 用带Micro USB接口的数据线连接H3主板与Solo主板或Dual主板；
* 用HDMI线连接H3主板与曝光屏，曝光屏用其配套电源供电；
* 确保以上所有步骤后用12V电源给Solo主板或Dual主板供电开始测试；

![连接图](/images/dlp_in_circuit.jpg)



### 测试要点

##### 启动过程

- H3主板指示灯点亮；

- 曝光屏背光开启；

- 触摸屏显示正常；

- 软件自动启动；

  ​

##### H3连接测试

- 软件启动后，右上角的连接状态为已连接；

  ![主界面](/images/main_page.png)






- 点击“设置--光固化设置”，按照准备的曝光屏设置曝光屏宽(475），高(295)，分辨率(1680*1050)，接口(HDMI)。

  ![设置曝光屏参数](/images/set_resolution.png)





- 设置后H3板将会自动重启，右上角状态变为已断开，曝光屏在H3启动过程应有图像显示；

  ![h3重启界面](/images/h3_reboot.jpg)

  ​

  ​

- 重启完成后“曝光屏分辨率”的值变为设置的值，右上角的连接状态变为已连接，设置成功；

  ![设置成功](/images/set_resolution_success.png)

  ​

  ​

#####电控测试

* 在主界面连续点击空白处10次进入“机器设置”界面，点击“Z轴设置”，给Z轴设置合适的“驱动电压”，“每毫米步进数”，将“碰撞开关位置”设置为“安装在最小”；

  ![Z轴设置](/images/axis_z_config.png)

  ​

  ​

* 回到主界面点击“维护 -- 回零点 -- 平台归位到最低点”，电机开始转动，此时触发碰撞开关，电机停止转动。

  ![归位](/images/home_axis.png)

  ​

  ​

* 回到主界面电机“维护 -- 清理”，弹出设置曝光时间，设置5，点击确定后Solo主板或Dual主板out1接口下方led灯点亮，曝光屏显示一张全屏的纯白色图片，5秒后，led灯熄灭，曝光屏显示的白色图片也消失。


![曝光](/images/expose_full_screen.png)





##### 打印流程测试

* 将带有测试文件的U盘或SD卡插入主板，在主界面点击“模型”进入“模型列表”界面，按住右侧的列表下拉松手刷新，可以刷出测试文件；

  ​

* 点击选中测试文件，如果测试文件是CWS格式，左侧进度条会有变化，进度条加载完成后出现3D渲染界面；

  ![模型列表](/images/model_list.png)

  ​

  ​

* 点击“开始打印”进入打印界面，电机开始转动，触摸屏和曝光屏不显示图片，out1接口下方led灯熄灭状态；

  ![开始打印](/images/ready_expose.png)

  ![准备曝光](/images/out1_close.jpg)






* 手动触发一次碰撞开关，电机开始反向转动一段距离然后再按原来的方向以更慢的速度转动，此时再触发一次碰撞开关，电机停止转动，触摸屏和曝光屏开始显示图片，同时out1接口下方led灯点亮；

  ![曝光单层](/images/expose_layer.png)

  ![曝光单层](/images/out1_open.jpg)

  ​

  ​

* 几秒后，触摸屏和曝光屏显示的图片消失，同时out1接口下方的led灯自动熄灭，电机在几秒后开始转动，转动时先往一个方向转动一定距离再往另一个方向转动一定距离。

  ​

* 几秒后，触摸屏和曝光屏开始显示图片，同时out1接口下方led灯点亮，点击“停止 -- 确定”退出打印界面，此时out1接口下方led灯熄灭，曝光屏不显示图像，打印停止；

  ![停止打印](/images/stop_print.png)

  ​

  ​





