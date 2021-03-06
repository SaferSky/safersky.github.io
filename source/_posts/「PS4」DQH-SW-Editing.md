---
title: 「PS4」勇者斗恶龙英雄集结 SW饰品修改
top_img: https://images3.alphacoders.com/630/630540.jpg
tags: [PS4, SaveWizard]
categories: [Game Hack]
---

>最近打折入的老游戏。作为11区长盛不衰的国民级IP，画面真的不错，喜欢！
不过我不明白，这个奖杯的意义何在？？  
![](https://s2.ax1x.com/2019/01/02/FI1f78.jpg)   
跑题了，说正篇。 
<!-- more -->
 
## 修改教程
装备初始位置从`000048B2`开始。写法是：  
```
XXXX DD00 TT01 NNNN SS00 NNNN SS00 NNNN SS00 GG00  
```
`XXXX`：装备列表中位置  
`DD00`：装备ID；后面的00不用管  
`TT01`：TT为装备类型，00为武器，01为宝珠，02为饰品；后面的01不用管  
`NNNN`：技能数值；需要实际数值*10后再转换成16进制码；  
例如0A实际数值是1，64是10，03E8是100，1027是1000，最大值是BC7F（3270）  
`SS00`：SS为技能代码，后面的00不用管；每个装备最多3个技能，所以有三组  
`GG00`：GG为能否继承到二周目，01不能继承，02为可以继承；后面的00不用管  
  
举个栗子，改兔子护符（ID是04），想要附加效果为攻撃⼒ (02)、守備⼒ (03)、会心率 (07) 的最大值，且继承到二周目。  
从`0x48B2`开始搜索0004，确认装备列表位置后（例如36），如图下改写：  
```
3600 0400 0201 BC7F 0200 BC7F 0300 BC7F 0700 0200
```
![](https://s2.ax1x.com/2019/01/02/FI1W0f.png) 


## 装备技能ID  
由于武器和宝珠都是固定属性没法改，所以我们修改饰品。  
下面是全部饰品的装备ID和部分常用的技能（注意饰品前面的码是装备ID，后面是装备类型）：  

#### 饰品ID：  
00 02 史莱姆耳环  
01 02 吸引铃铛  
02 02 驱魔铃铛  
03 02 金戒指  
04 02 兔子护符  
05 02 吊袜带  
06 02 金手镯  
07 02 粉红珍珠戒指  
08 02 蝴蝶结领带  
09 02 知识眼镜  
0A 02 玻璃鞋  
0B 02 网纹紧身袜  
0C 02 怒火纹身  
0D 02 力量指环  
0E 02 流星手环  
0F 02 疾风戒指  
10 02 力量红宝石  
11 02 守护红宝石  
12 02 祈祷指环  
13 02 金色念珠  
14 02 豪杰手环  
15 02 能量腰带  
16 02 生命指环  
17 02 ⼥神指环  
18 02 幸福靴子  
19 02 怪盗的面具  
1A 02 巫术戒指  
1B 02 龙之护符  
1C 02 宴会眼镜  
1D 02 金项链  
1E 02 神秘牌  
1F 02 超级戒指  
20 02 力量吊坠  
21 02 心形吊坠  
22 02 海德拉腰带  
23 02 博爱指环  
24 02 战斗项链  
25 02 维纳斯之泪  
26 02 闪耀指环  
27 02 守护吊坠  
28 02 清醒戒指  
29 02 妖精的首饰  
2A 02 精灵指环  
2B 02 皇家徽章  
2C 02 聖印指环  
2D 02 破幻戒指  
2E 02 破毒戒指  
2F 02 魔王项链  
30 02 生命项链  
31 02 悠久之花的捧花  
32 02 宝石首饰  
33 02 海魔眼罩  

#### 技能效果：
02 攻撃⼒  
03 守備⼒  
07 会心率  
40 必殺技傷害  
0A 鬥志上昇速度  
2B 鬥志高昂持続時間  
1E 不消耗MP率  
20 攻撃時HP回復率  
34 死亡直後復活  
16 呪⽂発動速度  
51 移動速度増加  
58 防衛対象HP  
57 霍米隆登場率+15% (補血的主角史萊姆)  
63 金属史莱姆遭遇率  

## 全装备ID和技能列表
请在线浏览文档（只翻译了饰品和技能）：[有道云](http://note.youdao.com/noteshare?id=dad99bd25ee3997075c24c0bebc40a91)  