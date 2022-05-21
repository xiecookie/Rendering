## 使用说明书  
### 1.拟合三维人脸：  
https://github.com/LansburyCH/eos-expression-aware-proxy.git  
我们使用的是google eos去做的三维人脸拟合  
选择的是bfm2017模型
我们最后需要使用的是人脸的纹理  
观察demo也需要生成的obj文件
#### Prerequisites
+ Visual Studio 2017 (>=15.5)  
+ Boost (>=1.50.0)  
+ OpenCV (>=2.4.3)  
+ Ceres (if compiling fit-model-ceres)  

### 2.皱纹像素块提取：python配置
python源码目录：introduce/wrinkle-py  
直接运行wrin_dis文件  
dir_tex：输入的纹理图片路径(文件名为result.isomap.png)  
dis2normal_coff=150  
生成normal_2048即生成的法线贴图  
可以通过attach_mask叠加不同图片的皱纹，生成最后的皱纹贴图  
#### Prerequisites    
+ python-opencv:4.5.5.62  
+ numpy:1.13.3  

### 3.回归器  
回归器使用的是pybind11调用C++代码  
在文件中已经生成了pyd文件供python文件调用  
如若调用pyd出现问题，则需要配置C++回归器环境重新生成pyd文件  
C++源码目录：introduce/Wrinkle
#### Prerequisites    
+ opencv 3.4.16  
+ eigen 3.3.9  
+ pybind11 2.8.1  

配置x64 Release  
需设置生成dll文件  
生成文件后缀名为pyd文件  

### 4.训练数据  
目录：introduce/metahuman_trainpatch.7z  
1. data中放的是纹理和置换贴图数据  
2. data_train中放的是使用的patch数据  
3. DOG是做高斯差分后的皱纹置信度数据  
4. patch中是纹理中对patch的标注  
