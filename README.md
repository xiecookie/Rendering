## Medium-Scale Wrinkle Reconstruction Using One RGB Image.   
### One.Extract texture using 3d face model fitting：  
https://github.com/LansburyCH/eos-expression-aware-proxy.git  
We are using google eos to do the 3D face fitting.  
The model chosen is the bfm2017 model.
The last thing we need to use is the texture of the face.  
#### Prerequisites
+ Visual Studio 2017 (>=15.5)  
+ Boost (>=1.50.0)  
+ OpenCV (>=2.4.3)  
+ Ceres (if compiling fit-model-ceres)  

### Two.Single image wrinkle reconstruction：python configuration
Run wrin_dis.py directly.  
  
+ **dir_tex**： input texture directory(filename is result.isomap.png)  
+ **dis2normal_coff**:  define how to tranfer displacement map to normal map:(default is 150)  
+ **dog_tresh**:  define the threshold the wrinkle is detected:(default is 60)  
+ **Target**:  generate normal_2048.jpg —— the normal map with 2048*2048 size generated.  
  
The final wrinkle map can be generated by overlaying the wrinkles of different input images with attach_mask  
#### Prerequisites    
+ python-opencv:4.5.5.62  
+ numpy:1.13.3  

### Three.Regression   
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

### Four.Training data  
directory：introduce/metahuman_trainpatch  
1. data中放的是纹理和置换贴图数据  
2. data_train中放的是使用的patch数据  
3. DOG是做高斯差分后的皱纹置信度数据  
4. patch中是纹理中对patch的标注  
