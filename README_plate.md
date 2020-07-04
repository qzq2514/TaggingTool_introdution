# TaggingTool_plate
车牌位置和车牌号码标注软件  
可用于标记车身定位数据、车牌定位数据、车牌字符识别数据

## V1版本
### 主要界面
![](https://github.com/qzq2514/ImageForGithubMakdown/blob/master/TaggingTool/1.PNG)

### 使用方法： 
1.将要标记数据放在"Images"文件夹下，本软件设计初衷为标记多个美国州的车牌数据，即将数据放在对应州下的文件夹，如"Images/AL"  
  图片车牌的groundTruth由文件名中的Tag标识决定，如"[IFPID-39707][TAG-2A95L32][STATE-AL][MAKE-].jpg"  
  的车牌标识为"2A95L32",程序会自动识别并加载  
2.load按钮：加载数据后以开始标注数据  
  zoom按钮: 聚焦车牌区域便于车牌字符标注  
  ![](https://github.com/qzq2514/ImageForGithubMakdown/blob/master/TaggingTool/2.PNG)
  其他按钮功能自行测试 
  
## V2版本  
  V1版本的字符标识由Ground Truth的Label决定,V2版本除了可以自动加载groundTruth,还可手动选择每个字符的tag：  
  ![](https://github.com/qzq2514/ImageForGithubMakdown/blob/master/TaggingTool/3.PNG)
  
  PS:程序仍可能有一些未知Bug,但对于标注简单车牌数据已完全足够
  
  
 ## V3版本
 V3版本有较大改动，相比之前V1和V2,V3版本可以标注车牌的四个角点，并进行仿射，在仿射后的车牌正面标注字符信息。
 先再整张车牌按照左上-右下-右上-左下的顺序标注车牌的角点信息
![](https://github.com/qzq2514/ImageForGithubMakdown/blob/master/TaggingTool/4.PNG)
车牌自动仿射并放大后再正面车牌上标注字符信息
![](https://github.com/qzq2514/ImageForGithubMakdown/blob/master/TaggingTool/5.PNG)

## V4版本
V4版本会放大预标签的较为宽松的车牌定位(可以使用MobileNet SSD或者cascade进行预车牌定位，但是没有也无妨，可以自己手动在界面上画车牌定位框)，  
并在放大后的车牌上进行四个车牌四个角点的标注
![](https://github.com/qzq2514/ImageForGithubMakdown/blob/master/TaggingTool/6.PNG)
![](https://github.com/qzq2514/ImageForGithubMakdown/blob/master/TaggingTool/8.PNG)
和V3一样，车牌自动仿射并放大后再正面车牌上标注字符信息
![](https://github.com/qzq2514/ImageForGithubMakdown/blob/master/TaggingTool/7.PNG)

## SSD版本
SSD版本在仿射后拉正的车牌上使用MobileNet-SSD进行字符的定位和识别,相比较于V4版本仅仅使用传统图像处理下的二值化等检测定位字符,SSD版本能够
较紧地框住车牌，更加提高标注软件的效率,以下是效果(并未进行手动框图)
![](https://github.com/qzq2514/ImageForGithubMakdown/blob/master/TaggingTool/ssd.PNG)

## SSD-stack版本
在SSD版本的基础上增加了堆叠的多排字符的识别和检测功能
![](https://github.com/qzq2514/ImageForGithubMakdown/blob/master/TaggingTool/IL_stack.PNG)

## 标注检查软件V1:
可以将车牌和字符区域截取并分开保存，并检查标注的情况(是否框的太紧或字符识别错误)并进行修改，此外标注软件还可以修改指定的的字符标签和删除重复图片。
其余的功能可以详细看checkGuide.pdf

## 标注检查软件V2:
增加重命名(命令行调用)、初始化图片功能

## 标注检查软件extract版本:
检查过程中可以分类标注的数据。  
如分州:先手动将检查结果中的plate车牌分到extract文件下不同文件夹，代表不同的州，之后点击extract按钮即可分类


