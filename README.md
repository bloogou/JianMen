# -
A html game ,create by simple js. 

working on the develop branch

目前 在 develop分支 开发未合并到master分之
=======
//********开发日志

/12 - 18/
战斗系统，想在里面先加一点 动画 ，画风采用 龙宫三太子 系列

4.战斗
3.建筑 事件
包括 外出 是做成 事件还是 地点～
也就是说，地点等级 变化.

关于 draw 按分层原理，应该抽成 独立的服务 被调用 具体的 逻辑 因该被写在调用者上，也就是说 用draw 定义绘画接口 ，具体绘画逻辑应落在 调用者里面，再调用一下。
这也是 所谓 引擎 2D库/3D库的作用。。 

12月15日记录有 框架分析


/12 15/

5.特殊事件展示 ok 就是 w-》展示 人物信息，s-〉展示武功 ; e->简单的回退 上一层建筑;r->刷新当前 建筑/场景
4.战斗
3.建筑 事件



*******
简单说明一下项目架构（假装有 游戏架构）:

	大概思路， 数据结构 + 页面跳转 + 事件触发，底层服务支持上层调用，最上层的就是各个建筑的 各个事件，分别独立成 js 去掉用 各个 服务，
主要是绘画Api。当 处于某个建筑界面时，命令会从最上层 接收器一点点 转发过来。
	目前 只有一个初始 的门派建筑，所以初始化也简单些，以后的扩展恐怕就难了，倒时再说～

 dataBase 是数据结构，各种对象的 组成；
 datasTemp 是 demo数据，以后回扩展到数据库；大概会沿用pgsql 习惯了～，而且开源免费，对json原生支持；

然后从上往下说

index.js就是 最开始的 初始化；
	load 装载-> orderInputFun 最初的命令接收函数 -> 转发到 orderHandel.js

orderHandel.js专门对命令 分发处理
	checkOrder() 区分是特殊命令，还是需要分发给各个建筑的命令；->dispatcher -> menpai_JShandler();

menpaiJS  因为目前 默认初始化为 门派 所以 将一部分上层逻辑 写在这里
扩展的话，直接进行替换就好
用  [世界] 替换-~-> [门派] ,将门派 下放.

yanwuchg.js 就是 4
这个是目前的 唯一 功能页面 事件还没写;明天...


draw.js 就是将所有的 高层业务逻辑 -> 转换为 图像 绘画出来.





/1214

1.回退 暂时不设计为 公共方法 ok
2.基本场景跳转 完成 扩充～
3.建筑 事件
4.战斗
5.特殊事件展示 


(资源碎片化加载)xxx






//1207

首先要搞定的就是 数据结构：各种对象的结构 定义

对于 这种定义我有经验，同样对于kill样的游戏 也有一套简单框架（框架 != 引擎）

翻一番 搬过来～

其实也就是 表结构嘛,暂时用js,后改成数据库.



不过 有很多 都是要 考虑的

～～～～～～～～～～～～·
目前是 这样的

主要 结构 分为：人，武功（内功），建筑，场景
所有 其他的 被规划为 事件
分别对应用 独立的脚本去  响应~


还有几个 环节 要处理一下
首先是 （按照 行进逻辑来）
1.开始界面
2. 门派 place 建筑 管理 -> 以后扩展为 保存上次 位置
3. 对应各个 门派内 建筑内部 逻辑
4. 外出 逻辑处理 特殊的3.
5. 外出每个 页面独立逻辑
6. 较为独立的功能～




!~!~~!~!~!~!~!~2017 ~!!~!~!~!~!~!~!~!



>>>>>>> develop
