# Rendering

### Preperation  
**Vulkan SDK**: https://vulkan.lunarg.com/sdk/home#windows  
勾选下载第三方库，里面有glm库（和SDL库）  
**glfw SDK**: https://www.glfw.org/download.html  
可以直接下载64位已编译版  
  
在包含目录添加三者的include目录  
在库目录添加vulkan-1.lib 和 glfw3.lib所在的目录  
附加依赖项添加vulkan-1.lib和glfw3.lib  
