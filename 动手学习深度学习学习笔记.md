# 遇到的问题和解决办法

---

1.由于我之前已经安装anaconda并且安装完python和pytorch，但是在此处直接运行pip install d2l==0.17.6却遇到了问题。原因是我的python版本过高，但是又因为conda中的python无法降级，此外更新numpy也行不通，所以在此我又重新按照手册的方法继续：使用下面的命令创建一个新的环境：
conda create --name d2l python=3.9 ，rd
现在激活 d2l境：

conda activa。再接着把pytorch进行安装，我的电脑的安装代码为：pip install torch==2.6.0 torchvision==0.21.0 torchaudio==2.6.0 --index-url https://download.pytorch.org/whl/cu126。

# 1.te d2l