# Medium-Scale Wrinkle Reconstruction Using One RGB Image.   
<p align="center"> 
<img src="/example_output/example.jpg">
</p>  
  
## One. Extract texture using 3d face model fitting：  
https://github.com/LansburyCH/eos-expression-aware-proxy.git  
We used google eos to do the 3D face fitting.  
The model chosen is the bfm2017 model.  
The last thing we need to use is the texture of the face.  
After the face reconstruction step, the result output is like files in 'exmaple_data/' directory.
### Prerequisites
+ Visual Studio 2017 (>=15.5)  
+ Boost (>=1.50.0)  
+ OpenCV (>=2.4.3)  
+ Ceres (if compiling fit-model-ceres)  

## Two. Single image wrinkle reconstruction：python configuration
Run wrin_dis.py directly.  
  
+ **dir_tex**： input texture directory(filename is result.isomap.png)  
+ **dis2normal_coff**:  define how to tranfer displacement map to normal map:(default is 150)  
+ **dog_tresh**:  define the threshold the wrinkle is detected:(default is 60)  
+ **Target**:  generate normal_2048.jpg —— the normal map with 2048*2048 size generated.  
  
The final wrinkle map can be generated by overlaying the wrinkles of different input images with attach_mask  
```
python wrin_dis.py --dir_tex='example_data/result.isomap.png' --dis2normal_coff=150 ----dog_thres=60
```
### Prerequisites    
+ python-opencv:4.5.5.62  
+ numpy:1.13.3  

## Three. Regression   
The regressor uses pybind11 to call the C++ code  
The pyd file is already generated in the file for the python file to call  
If there is a problem calling pyd, you need to configure the C++ regressor environment to regenerate the pyd file  
  
**C++ source code directory**: introduce/Wrinkle
### Prerequisites    
+ opencv 3.4.16  
+ eigen 3.3.9  
+ pybind11 2.8.1  

Configure x64 Release.  
You need to set up the generated dll file.  
Generate a file with the suffix pyd file.  

## Four. Training data  
Directory：introduce/metahuman_trainpatch  
+  **data** is the texture map and replacement map data  
+  **data_train** is the patch data used  
+  the DOG is the confidence data of the wrinkles after Gaussian differencing  
+  patch is the annotation of the patch in the texture  

