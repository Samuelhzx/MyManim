注：
- 标题我用了彩色，但貌似在github上预览不了，所以最好下载到本地再看  
- 本文档适用于windows操作系统
- 读这篇文章需要一定python和命令行基础

# <font color=#f1d700>1.劝退</font>
先看这个：https://manim.org.cn/problems/persuade2quit

# <font color=#f1d700>2.介绍</font>
> Manim is an animation engine for explanatory math videos. It’s used to create precise animations programmatically, as seen in the videos at 3Blue1Brown.

Manim分多个版本：  
## <font color=#4ec9b0>ManimCE</font>
Manim爱好者们维护的版本  
### <font color=#d470d6>优点：</font>
他们在源代码中添加了很多注释，并且在 0.17.x 版本中增加了ManimGL没有的ai配音功能  
### <font color=#d470d6>缺点：</font>
渲染速度不如ManimGL，无法即时渲染

## <font color=#4ec9b0>ManimGL</font>
Grant和少数爱好者们维护的版本（几乎是Grant一个人）  
使用OpenGL渲染（因而得名）  
近期扬了CONFIG，导致老代码要大改才能运行
### <font color=#d470d6>优点：</font>
速度较快，可以即使渲染，**可交互**  
### <font color=#d470d6>缺点：</font>
对旧版本manim兼容很差，有渲染缺失现象


# <font color=#f1d700>3.相关链接</font>

## <font color=#4ec9b0>类似的软件或库</font>
https://reanimate.github.io/  
https://mafs.dev/  
https://github.com/JazonJiao/Manim.js  
https://github.com/manim-web/manim-web  
https://github.com/ambrosiogabe/MathAnimation  

## <font color=#4ec9b0>文档&教程</font>

### <font color=#d470d6>英文的：</font>
Elteoremadebeethoven的ManimCE文档: https://elteoremadebeethoven.github.io/  
ManimGL文档: https://3b1b.github.io/manim/  
ManimCE文档: https://docs.manim.community/en/stable/  

### <font color=#d470d6>中文的：</font>
mk文档: https://docs.manim.org.cn/  
cigar666的教程: https://www.bilibili.com/read/readlist/rl82339  
widcardw的视频教程: https://space.bilibili.com/31976300  
widcardw的文档: https://widcard.win/posts  
mk的视频教程: https://www.bilibili.com/medialist/detail/ml947351931  
知乎上一个教程合集: https://zhuanlan.zhihu.com/p/378999796

## <font color=#4ec9b0>其他</font>
mk版本的manim: https://github.com/manim-kindergarten/manim  
3b1b的网站: https://3blue1brown.com  
ManimGL下载: https://github.com/3b1b/manim  
mk的代码仓库: https://github.com/manim-kindergarten/manim_sandbox  
mk油管频道: https://www.youtube.com/channel/UCk1nsj8AvzuSVL_I4JieVNQ  
manim-jupyter在线编辑: https://try.manim.community/  
manim-physics: https://github.com/Matheart/manim-physics  
凡人忆拾重构的manim: https://github.com/YishiMichael/manim3  
乐正垂星的manim项目库: https://github.com/YuezhengChuixing/manim-projects  
Grant的manim问答&演示: https://www.youtube.com/watch?v=gakLOaZziWM&ab_channel=3Blue1BrownHidden


# <font color=#f1d700>4.安装</font>

> 需要安装：python>3.7(越高越好)、ffmpeg、pycairo、sox(可选)、LaTeX（需要打公式的话）


## <font color=#4ec9b0>ffmpeg安装:</font>
try:
    [一键下载](https://www.gyan.dev/ffmpeg/builds/packages/ffmpeg-5.0.1-essentials_build.zip)，
    [ffmpeg安装教程](https://blog.csdn.net/HYEHYEHYE/article/details/122000352)从第二章开始看  
except:
	[ffmpeg安装教程](https://blog.csdn.net/HYEHYEHYE/article/details/122000352)

## <font color=#4ec9b0>sox安装:</font>
try:
	[一键下载](https://sourceforge.net/projects/sox/files/latest/download)  
except:
	去官网下载

## <font color=#4ec9b0>LaTeX安装:</font>

[TeXLive一键下载](https://mirror.ctan.org/systems/texlive/tlnet/install-tl.zip)  
[LaTeX在Windows的安装教程](https://blog.csdn.net/weixin_43257343/article/details/107938216)

## <font color=#4ec9b0>Pycairo安装:</font>
[选择合适的pycairo版本下载](https://www.lfd.uci.edu/~gohlke/pythonlibs/#pycairo)，然后  
```
pip install xxx.whl
```
## <font color=#4ec9b0>ManimGL安装:</font>
最新版：
```
git clone https://github.com/3b1b/manim.git
cd manim
pip install -r requirements.txt
pip install -e .
```
> 如果没有git那就download zip, 下载下来的文件夹叫manim-master

pypi版：
```
pip install manimgl
```
## <font color=#4ec9b0>ManimCE安装:</font>
```
pip install manim
```

# <font color=#f1d700>4.基础知识&格式</font>
最好要能读懂manim源代码，读不懂也没关系，但得更努力  

## <font color=#4ec9b0>基本格式：</font>

```Python
from manimlib import *

class xxx(Scene):
	def construct(self):
        #这里写代码
        #manim会调用construct方法并用其中的代码生成视频
```

### <font color=#d470d6>示例：</font>

```Python
from manimlib import *

class SquareToCircle(Scene):
    def construct(self):
        circle = Circle()
        circle.set_fill(BLUE, opacity=0.5)
        circle.set_stroke(BLUE_E, width=4)

        self.add(circle)
```
## <font color=#4ec9b0>运行方法：</font>
不是直接点运行，而是在命令行输入指令  


### <font color=#d470d6>ManimGL:</font>
一种：
```
manimgl start.py SquareToCircle
```
这样会进入交互界面。屏幕上会弹出一个窗口，这时你可以：  
- 滚动鼠标中键来上下移动画面  
- 按住键盘上 z 键的同时滚动鼠标中键来缩放画面  
- 按住键盘上 f 键的同时移动鼠标来平移画面  
- 按住键盘上 d 键的同时移动鼠标来改变三维视角  
- 按下键盘上 r 键恢复到最初的视角
> 如果直接按按键没用就加个ctrl，比如改变三维视角就用ctrl+d

最后，你可以通过按 q 或 esc 来关闭窗口并退出程序  

另一种：
```
manimgl start.py -ow
```
渲染最后一帧并生成视频
### <font color=#d470d6>ManimCE:</font>
```
manim start.py SquareToCircle -pqm
```

生成中等质量的视频

---

> 可以在代码中增加这些：
> ```python
> if __name__ == "__main__":
>     __import__("os").system("manimgl start.py SquareToCircle")
> ```
> 这样就能直接点运行，而不用命令行了


> 以上是基础指令，还可以输入
> `
> manimgl -help
> `
> 或
> `
> manim -help
> `
> 来查看更多功能

# <font color=#f1d700>5.报错</font>
1  
类似这样的：
> (process:13596): GLib-GIO-WARNING **: <font color=blue>21:44:32.108</font>: Unexpectedly, UWP app \`45747ThomasWeber.TurboWarpDesktop_1.7.1.0_x64__dx91esefr5w5e' (AUMId `45747ThomasWeber.TurboWarpDesktop_dx91esefr5w5e!TurboWarp') supports 3 extensions but has no verbs

> xxx\lib\site-packages\pyglet\libs\win32\__init__.py:326: UserWarning: Could not set COM MTA mode. Unexpected behavior may occur.
  warnings.warn("Could not set COM MTA mode. Unexpected behavior may occur.")

不必管他  
2
> WARNING  You may be using Windows platform and have not specified the path of `temporary_storage`, which may cause OSError. So it is recommended to specify the `temporary_storage` in the config file (.yml)

这是提示你没有设置视频和一些临时文件的存放地址  
解决方法：
- 进入manim库文件夹里，找到一个叫default_config.yml的文件，打开，这是manim的默认配置。其中有一行写着：temporary_storage: ""  
- 在引号里写你想要存放视频和一些临时文件的地址
- **这个文件里还有很多可以改的，比如window_position代表进入交互后窗口的位置；font是默认字体；background_color是底色。**