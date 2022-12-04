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
![image](https://user-images.githubusercontent.com/43695412/205470656-d4f0d8ee-9077-403a-ac55-947bdf45d463.png)
![image](https://user-images.githubusercontent.com/43695412/205470683-7b5851b3-60a9-4800-bc3c-5f7fad6281ae.png)
翻页，成功断住,查看堆栈，寻找可以函数，大概如下位置找到
![image](https://user-images.githubusercontent.com/43695412/205470807-ef01418a-642a-4105-8b7d-7f322b82dee3.png)
使用了promise异步，无法直接查看结果，这时候就需要一步一步跟进去看了，辛苦活~
![image](https://user-images.githubusercontent.com/43695412/205470838-65e87e92-3b1f-4a6a-b915-507ce84b13d3.png)
一直单步跟到一个新的js后，终于看到我们的目标值
![image](https://user-images.githubusercontent.com/43695412/205470860-949c2b98-633c-4e51-8f4a-7223f84bd639.png)
找到目标后，单步进入分析
![image](https://user-images.githubusercontent.com/43695412/205470889-d17f05be-75fb-4190-b7ab-9589e57c901f.png)
![image](https://user-images.githubusercontent.com/43695412/205470905-6e781529-050f-48f7-8875-4dc2e9661370.png)
之后跳转到某个方法中，分析起来太费事了，直接js全扣，肝就完事，nodejs跑起来，缺啥补啥，懒得写了
## 最后
生成有效js后，我习惯使用python用于生产，使用execjs进行调用，成功获取到anti-content参数，破解也就算是完成了，接下来便可用于生产，模拟请求，实现自动化操作了
![image](https://user-images.githubusercontent.com/43695412/205471119-62e677f9-12d5-4b2b-83ed-acda4f4ce57c.png)
## 联系方式
js文件就不放了，有需要的联系我  
wx: YarnBlue, 添加好友务必备注：ktt破解
