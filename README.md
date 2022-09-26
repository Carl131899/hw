# 嵌入式系统概论（单片机原理与应用）

>使用华为物联网培训IoT实验箱BearPi作为课程实验硬件平台。

## 一、课程前的准备

1. 下载安装 IDE 工具 [MDK-ARM](http://www2.keil.com/mdk5/)，课程中使用 ARM 的 Clang 编译器 [ArmClang](https://developer.arm.com/docs/100068/0614) ，配置工具 [ST 的 CubeMX](https://www.st.com/content/st_com/en/products/development-tools/software-development-tools/stm32-software-development-tools/stm32-configurators-and-code-generators/stm32cubemx.html)。
2. 下载安装 [vscode](https://code.visualstudio.com/)，课程中的文档和代码都使用 vscode 编辑，熟练使用vscode 请阅读 [vscode 教程](https://geek-docs.com/vscode/vscode-tutorials/what-is-vscode.html)。为了获得所见即所得的 [Markdown](https://help.github.com/articles/github-flavored-markdown/) 语言编辑体验，可以使用 [Typora](http://typora.io/)。
3. 下载安装 git 客户端 [sourcetree](https://www.sourcetreeapp.com/)，课程使用 sourcetree 和 [github](http://www.github.com) 作为项目管理和协作系统。
4. git 入门请读 [Git教程](https://www.liaoxuefeng.com/wiki/896043488029600)，进阶请阅读 [git 权威指南](https://gitee.com/progit/) 或其 [英文版](https://git-scm.com/book/en/v2)。
5. 在 win10 安装 SSCOM 串口工具。 

## 二、课程目录结构

  1. 教材目录中内含课程参考教材。
  2. BearPi目录中包含BearPi的所有硬件资料，尤其是详细的**数据手册**。一般教学中不会涉及此点，但本课程特别强调工程实践中对数据手册的理解。
  3. 课件目录包含制作的PDF课件。
  4. 练习目录包含实验作业要求文件。
  5. 示例代码目录包含课程中的所有实验代码示例。

## 三、 课后实验

> 课后实验必须委托在 [Gitee](https://www.gitee.com)上的本课程各自的私有代码仓库中。

1. 工具链的安装、配置和 GPIO 的简单应用
   - [ ] 安装和运行课前准备中要求的工具链。
   - [ ] 根据小熊派IoT实验板的PCB手册，使用 [ST 的 CubeMX](https://www.st.com/content/st_com/en/products/development-tools/software-development-tools/stm32-software-development-tools/stm32-configurators-and-code-generators/stm32cubemx.html) 创建 MDK 项目框架和硬件配置。
   - [ ] 实现实验板上的蓝色LED 亮与灭的按键控制，其中按键1 按一下LED亮，按键2 按一下LED灭。
   - [ ] 要求基于 [ST 的 CubeMX](https://www.st.com/content/st_com/en/products/development-tools/software-development-tools/stm32-software-development-tools/stm32-configurators-and-code-generators/stm32cubemx.html) 分两步增量实现用户代码和生成代码，理解框架和配置代码的增量开发。
   - [ ] 使用 STLink 和 MDK 调试代码的基本技巧：单步、断点、变量观察等。
   - [ ] 拓展：按键1 按一下 LED灯 0.5秒闪烁，每按一次闪烁时长增加 0.5秒。按键2 按一下，LED 闪烁时长恢复为 0.5秒。
   - [ ] 拓展：使用实验板上的 PA11、PB12 设计和实现两个按键和两个 LED 灯的GPIO <u>复用功能</u>：按键1 控制 LED1 的亮与灭，按键2 控制 LED2 的亮与灭。

2. 中断与时钟中断的应用
   - [ ] 中断系统：把上面的实验全部改为外部中断模式。
   - [ ] 用[逻辑分析仪](https://support.saleae.com/user-guide)验证 sysTick 的频率。
   - [ ] 时钟设置：计时、计数、测量脉宽。
   - [ ] 时钟中断：8Khz，驱动压电蜂鸣器发出滴滴声。
   - [ ] 时钟中断驱动时间片的代码框架。
   - [ ] 使用小熊派 IoT实验套件和STM32CubeMX，基于定时器2，实现 20KHz 定时中断，由此20KHz生成 100Hz的 PWM周期信号，产生占空比慢慢增加和慢慢减小的PWM信号，获得 LED的呼吸灯效果（每分钟呼吸 10次）。用[逻辑分析仪](https://support.saleae.com/user-guide)测量此信号的图形，自己编程用小熊派测量此信号的周期和高电平脉冲的周期变化。

3. ARM 存储系统与嵌入式 C语言的应用
   - [ ] C语言中局部变量、全局变量的生命周期，子函数尤其是递归子函数运行时生命周期。
   - [ ] 根据 volatile 修饰符的特性，构造一个程序（主程序、中断子程序的程序结构）。要求：无 volatile 时，程序会出现随机的运行逻辑错误。加入 volatile 后，程序随机的运行逻辑错误消失。*拓展阅读：*[详解C/C++中volatile关键字](https://blog.csdn.net/weixin_44363885/article/details/92838607)
   - [ ] 用 C语言和MDK编译器研究 ARM 的内存变量的大(小)尾存储方式和字节对齐方式，理解CPU 和编译器为何如此处理。*拓展阅读：*[C/C++内存对齐详解](https://zhuanlan.zhihu.com/p/30007037)，[内存对齐总结](https://www.cnblogs.com/iQXQZX/p/14049734.html)
   - [ ] *拓展思考*：总结主程序与中断服务子程序的数据交换规则，防止共享数据的不一致（脏数据）。

## 四、课程重点内容

>请课程的使用者在完成教材内容的同时特别关注以下几点

1. 基于Git 分布式版本管理系统的协作能力。
2. MarKDown 文档的写作能力，请阅读 [MarkDown 写作指南](https://shd101wyy.github.io/markdown-preview-enhanced/#/zh-cn/)。
3. 形成自己的编程风格和规范，课程中会给出一种风格规范，以提高代码的可阅读性、可复用性、可移植性、可靠性。
4. 嵌入式 C 语言的开发特性，比如 volatile、const、interrupt 等几个关键词后面的理论含义。
5. 嵌入式常规仪器（万用表，[逻辑分析仪](https://support.saleae.com/user-guide)，[示波器](https://www.tek.com.cn/oscilloscope/tbs1000b-edu-digital-storage-oscilloscope-manual/tbs1000b-and-tbs1000b-edu-series-oscil)等）的使用能力训练，嵌入式程序员易忽略此点。
6. 产品创新和规划能力，培养工程师的商业敏锐度。

> 使用课程时有任何问题和建议，请及时与我们联系，请 pull request 。
