# ktt-anticont
快团团PC端anticontent参数破解
## 前言
快团团作为目前最为火热的私域团购工具，越来越引起大家的重视，也让很多人投入到快团团创业潮中。而对于从业者来说，通过技术手段，来实现运营手段的丰富性，提升工作效率，一直是一个快人一步的好选择。所以，本项目就是基于快团团PC端管理后台，对其关键参数的解析，以期实现丰富的功能！
## 准备工作
1. 准备一个快团团账号，登录后获取访问权限
2. 抓包工具--fiddler，fiddler的配置及使用不再做详细描述
3. chrome浏览器（或其它可开发者调试的浏览器）
## 抓包
对任意接口抓包，如下图
</br>
 ![image](https://github.com/BigWhitee/ktt-anticont/blob/main/1.png)
</br>
进行分析后，发现有一个关键加密参数 anti-content会随着翻页进行动态变化,其余接口均如此；其加密方式未知，所以解密anticontent是关键步骤
## 调试跟包
为获取anticontent加密方式，想到利用chrome的开发者调试工具，对参数进行调试跟包
选择第一个js打入断点
![image](https://user-images.githubusercontent.com/43695412/205470631-d280a786-e96e-4575-9ad2-f0fbabca780f.png)
