# 斗地主AI
# Without Dizhu

该文件夹中为无地主1V1V1版本，每人18张牌，出牌规则与正常斗地主相同。

AI目前只有价值网络，决策网络会在以后加入

训练主要分为两部分，第一阶段是有监督学习，通过多次模拟获得输赢概率，从随机出牌开是不断学习，并积累数据用于又监督训练。
第二阶段为增强学习，同alpha go。

rules为出牌规则，policy为价值网络模块，net模块为resnet网络，game中包括Position类（记录当前局面），Yimodel类为RL部分

mcts模块为蒙特卡洛树搜索，主要用于之后加入决策网络，也可以加入之后的online play中。

神经网络输入为 上上一个玩家上一轮出牌、上一个玩家上上轮出牌、当前玩家手牌、当前玩家出过的牌、下家出过的牌、下下家出过的牌、当前玩家准备出的牌，输出为当前玩家当前出牌的价值。

已在gpu服务器上训练得到满意结果，第二阶段RL效果明显优于第一阶段有监督学习，速度也更快，所以可以直接开始RL不需要之前的有监督学习，第一阶段的代码也有部分删去。resvalue_5.h5为训练好的模型。






# With Dizhu

该文件夹中为有地主1V2版本，地主20张牌，两个农名各17张。

目前还在设计网络结构，目前准备用到transfer learning，神经网络前部分固定用于提取相同信息，最后全连接层分开用于分别决策（三人决策思路都有不同，其中两个农名的合作尤为重要）
