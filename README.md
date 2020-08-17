# 号来

[![Developing](https://img.shields.io/badge/Developing-200817-brightgreen.svg)](https://github.com/nguaduot/yys-cbg-bench)

[阴阳师藏宝阁](https://yys.cbg.163.com/)衍生小工具，用于提取游戏帐号要点并生成报告。目前仍处于开发阶段。例：

商品页面：[阴阳师藏宝阁-初心未改-南瓜多糖](https://yys.cbg.163.com/cgi/mweb/equip/28/202006230501616-28-2KCLGHIJVPTIL)

生成报告：[完整结果](sample/cbg_全平台互通新区_初心未改_南瓜多糖_20200710132623_bench.png) | [精简结果](sample/cbg_全平台互通新区_初心未改_南瓜多糖_20200710132623_bench_lite.png)

### 依赖

**号来**使用 Python3 编写，依赖的第三方库：

```
pip install pillow
```

### 文档

```
python cbg_bench.py -h
```

```
+ 选项：
  -h, --help     帮助
  -v, --version  程序版本
  -l, --lite     输出结果精简化(未指定则输出完整结果)
  -u, --url      藏宝阁商品详情链接
+ 若未指定 -u, 程序会读取未知参数, 若也无未知参数, 不启动程序
+ 不带任何参数也可启动程序, 会有参数输入引导
输出结果:
签到: {天数} ¥{售价} {若检测到合服则显示提示, 多服合一无法获知归属服, 需留心}
  金币 {金币} 黑蛋 {'御行达摩'数量+推测已消耗量(据此可了解练度)} 体力 {体力} 勾玉 {勾玉} 蓝票 {神秘的符咒+现世符咒} 御札 {御札/金御札}
  庭院: 初语谧景 + {除初始之外的其他庭院}
  风姿百物: {风姿度, 据此可了解外观向收集量(皮肤/头像框等)}
图鉴SP&SSR式神: {'500天未收录SSR'未使用则显示} {'999天未收录SP'未使用则显示}
  未拥有式神: {未拥有SP数量}+{未拥有SSR数量}
    SP碎片收集: {未拥有式神(图鉴已点亮也可能未拥有, 需留心)} {该式神碎片量, 据此可知有无碗} ...
    SSR碎片收集: {未拥有式神(图鉴已点亮也可能未拥有, 需留心)} {该式神碎片量, 据此可知有无碗} ...
  部分多号机拥有情况: {式神} {该式神拥有数量} ...
联动式神拥有&碎片收集情况:
  {联动期数}: {该期式神} {拥有数量(低稀有度低星式神无法获知)}/{碎片量(低稀有度式神无法获知)} ...
  ...
六星/满级/六星满级御魂: {藏宝阁未提供未满级御魂数据, 因此六星御魂数量无法查到}/{各星级满级御魂总量}/{六星满级御魂数量}
  满级普通御魂: {满级非首领御魂数量}
    {两件套属性} {该类御魂数量}
    ...
  满级首领御魂: {满级首领御魂数量}
    荒骷髅 {'荒骷髅'数量}
    歌伎 {'鬼灵歌伎'数量}
散一速: {散件套一速} 招财 {招财套一速}
  [{位置}] {该位置散一速套御魂, 以及其余速度满收益御魂} {副属性'速度'值} ...
  ...
高分暴击&暴伤御魂: {高分暴击御魂数量}+{高分暴击伤害御魂数量}
  陆|暴击 输出分:
    {陆号位主属性'暴击'的高分御魂} {该御魂分数, 按有效属性'攻击加成'/'速度'/'暴击'/'暴击伤害'评分, 非首领御魂5+, 首领御魂7+} ...
    ...
  陆|暴击伤害 输出分&副属性暴击值:
    {陆号位主属性'暴击伤害'的高分御魂} {该御魂分数, 按有效属性'攻击加成'/'速度'/'暴击'/'暴击伤害'评分, 非首领御魂5+, 首领御魂7+}: 暴击 {副属性'暴击'值}
    ...
部分御魂方案:
  {是否能做}: {何用途的何式神} {御魂套装} {加速计算的分数限制, 按有效属性'攻击加成'/'速度'/'暴击'/'暴击伤害'评分}
  ...
* 通过计算御魂方案来粗略了解御魂池及练度, 内置的几种方案(从易到难排序):
  1. 真蛇副本用到的超星针歌小小黑, 攻暴值未作限制, 基本满暴就能用
  2. 探索困28副本用到的超星破荒/破歌茨林, 破荒攻暴 15815+, 破歌 15723+
     数据参考: https://nga.178.com/read.php?tid=21014251
  3. 觉醒十层副本用到的高速破荒茨林, 速度 160+, 攻暴 15810+
     数据参考: https://nga.178.com/read.php?tid=15698562
  4. 御魂十层副本用到的高速狂荒/破荒玉藻前, 速度 162+, 狂荒攻暴 15696~20090, 破荒 17843~20090
     数据参考: https://nga.178.com/read.php?tid=20569256
  5. 探索困28副本用到的超星破荒玉藻前, 攻暴 21644+
     数据参考: https://nga.178.com/read.php?tid=21014251
* 计算过程可能比较耗时, 已最大程度优化, 分派大量子进程同时计算, CPU核心全利用. '痒痒鼠, 烤机不?'
```

[号来生成文档](sample/cbg_bench_help.png)

### 作者

> “不会在记事本用 Python 写小工具的程序猿的不是好痒痒鼠！”
>
> —「初心未改」区@**南瓜多糖**

痒痒鼠相关问题欢迎来找我讨论，代码改进或漏洞也欢迎一起交流。
