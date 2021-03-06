# starting
hello world!

## **2020.09.15**
### 参数调整方法分为两大类：
(1) 离线参数调整方法：Kessler对称最优原理参数调整算法、ISTE最优参数整定算法、继电反馈控制作用下的参数自调整算法、Ziegler Nichols参数自调整算法、遗传算法（GA）。这些算法通过固定公式和工程经验获得参数，计算繁琐，计算量大，部分参数过分依赖数学模型。参数一旦寻到最优值将固定不变，不能满足环境的变化。

(2) 文章提出学习在线参数的方法包括：模拟退火算法（SA）、粒子群算法（PSO）、单纯形法和强化学习方法等等。PSO收敛速度慢容易陷入局部最优，单纯形法优化过程中性能会出现较大波动、SA收敛速度慢，实时性差。<sup>[1]</sup>
### 常用的强化学习算法
* (1) 动态规划
* (2) 蒙特卡罗
* (3) 瞬时差分算法
* (4) Q-学习
* (5) 自适应启发评价算法 （Adaptive Heuristic Critic Algorithm，简称 AHC 算法）
* (6) Sarsa算法
* (7) 学习自动机
* (8) 本文的强化学习算法是连续动作强化学习自动机，其算法属于学习自动机算法，与以上常用的算法有所区别。其优点是：在随机或未知的系统模型情况下，随机试错，与环境相互作用，最终可以达到一个改善系统性能。与常用的强化学习不同的是：通过概率密度函数获得收敛信息。<sup>[1]</sup>

## **2020.9.16**
### 仿人智能控制<sup>[2]</sup>
1. 仿人智能控制的智能性：
* 控制规律具有非线性；
* 控制方式表现为多模态控制方式：根据被控动态过程特征识别采取相应的控制方法；
* 控制具有变结构特点：当
系统状态穿越状态空间的不连续曲面时， 反馈控制的结构就
发生变化， 从而使系统性能达到某个希望指标；
* 智能控制具有整体自寻优特点；
* 定性分析、仿真研究和应用研究表明，仿人智能控制系统有大范围渐进稳定性，对于任何复杂的被控对象都是可控的。
### 仿人智能控制的在线学习
* 面向控制器的参数学习：包括对各种数据的训练学习，对样本数据的分类学习；
* 面向控制器的结构学习：变化范围较大，作为控制器的粗调，参数学习作为控制器的细调；
* 面向控制器本身的总结性记忆性学习：对特定阶段形成的有效的控制方法，要进行记忆存储，在以后的控制过程中若出现类似的现象或情况，可直接调用先前存储的有关数据信息，省去重复的中间计算处理过程。
* 面向被控对象的环境学习
* 面向复杂不确定被控对象的学习

## **2020.9.18-21**
### **智能控制领域的常用算法**
* 专家系统
* 遗传算法
* 模糊逻辑
* 神经网络
* 模糊逻辑和神经网络是两种万能逼近器，两者的结合，即模糊神经网络和神经模糊逻辑算法


**A Multiresolution Analysis-Assisted Reinforcement Learning Approach to Run-by-Run Control（一种多分辨率分析辅助强化学习的逐段控制方法）**：<sup>[3]</sup>  


Exponentially weighted moving average (EWMA) controller 在工业上广泛使用，但在多尺度干扰和缺乏精确处理模型的环境下，性能不佳。


本文使用的方法是 Wavelet-aided RL-based Run-by-run controller（WRL-RbR controller），这个方法首次结合基于小波域的多分辨率分析和强化学习，优势是(1)在大的动作空间中选择最优或近似最优动作的灵活性（可以使用空间分布传感器数据），(2)目标处理流程的期望值收敛更快（相对于过程建模）。


这里多分辨率分析是指对含多频率噪声的数据进行降噪处理，帮助从噪声信号数据中提取重要特征。


强化学习算法用于错误预测：错误的更新$E_t=f_t-\hat y_t$（其中$f_t$是重构的信号，即过程输出，$\hat y_t$是感兴趣的质量特征，即模型预测输出）用马尔可夫链建模，过程偏移量$a_t$的预测决策用马尔可夫决策过程（MDP）建模。为了解MDP，有必要离散化$E_t$和$a_t$，由于有大量($E_t$,$a_t$)元组，因此采用强化学习的方法来解马尔可夫决策模型。


* 第t次运行结束时的系统状态定义为流程输出和模型预测输出之间的差值$E_t=f_t-\hat y_t$，$E_{t+1}$只依赖于$E_t$，所以随机过程E是一个马尔可夫链。
* 在RbR控制上下文中，运行时的操作是预测偏移量，然后使用偏移量来获得配方值。实际应用中，预测偏移量的作用空间很小，可以离散成有限个数量。由于MDP的目标是开发一个将实际错误最小化的行动策略，因此采用平均报酬作为绩效的衡量标准。
* 强化学习是一种基于仿真的解决MDPs的方法，根于贝尔曼方程，使用随机逼近原理


## **2020.9.22-24**
**ON CONVERGENCE RATE OF ADAPTIVE MULTISCALE VALUE FUNCTION APPROXIMATION FOR REINFORCEMENT LEARNING（强化学习的自适应多尺度值函数逼近的收敛速度）**：<sup>[4]</sup>


本文采用基于值的最优策略寻找最大期望的长期奖励，即通过研究Bellman方程所描述的最优值函数。


通过自适应基的线性组合来逼近最优价值函数，从而产生多尺度逼近，本文设计了一个多尺度值函数逼近的通用框架，适用于分段常数函数、分段多项式以及小波分析中的其他尺度函数。本文补充了前人工作中收敛性分析和近似残差方面的结果的不足。GMSA(Generalized MultiScale Approximation)和ATC(Adaptive Tile Coding)都是基于树近似的，区别在于基的选择。


这里的多分辨率分析是指，利用树近似，在平滑的函数区域使用低分辨率，在剧烈变化的函数区域使用高分辨率。


## **2020.9.29**
**Neurofuzzy Reinforcement Learning Control Schemes for Optimized Dynamical Performance**<sup>[5]</sup>


模糊系统和神经网络方案：无模型的、存储知识做出决策。对于模糊系统，不准确的专家知识会导致功能退化；对于神经网络，当数据不能服务于特定领域时会有缺点。结合使用，综合知识、专家特征、学习能力。


文中对比单一模糊控制、Q学习模糊控制、神经网络模糊控制，后两种策略在模糊控制的基础上增加了学习优化过程，都产生了优于单一模糊控制的结果，其中模糊神经网络效果最佳。


## **2020.9.30**
**Multi-scale reinforcement learning with fuzzy state**<sup>[6]</sup>


一般的强化学习在遇到状态空间较大的复杂问题时，学习速度会降低。在大状态空间下，分层方法是有效的。分层方法将任务分解为子任务的状态转移子序列来学习实现更容易的子目标。这表明改变时间尺度会影响学习效果。


提出了模糊状态的概念，为空间多尺度表示提供了一种方法。实验表明，改变空间尺度同样可以影响学习性能。不同的空间学习尺度表现出不同的学习速度和学习精度，在此基础上提出了一种提高学习速度同时保持学习精度的多尺度学习方法。


文中以复杂环境下的机器人导航作为仿真实验验证多尺度强化学习性能。


# **参考文献**
>[1] 甘晓琴.基于强化学习的仿人智能控制器参数在线学习与优化[D].重庆:重庆大学,2010.

>[2] 王培进.仿人智能控制的在线学习模型[J].计算机工程与应用,2001,27(1):80-82. DOI:10.3321/j.issn:1002-8331.2001.01.027.

>[3] R. Ganesan, T. K. Das and K. M. Ramachandran, "A Multiresolution Analysis-Assisted Reinforcement Learning Approach to Run-by-Run Control," in IEEE Transactions on Automation Science and Engineering, vol. 4, no. 2, pp. 182-193, April 2007.

>[4] T. Li and Q. Zhu, "On Convergence Rate of Adaptive Multiscale Value Function Approximation for Reinforcement Learning," 2019 IEEE 29th International Workshop on Machine Learning for Signal Processing (MLSP), Pittsburgh, PA, USA, 2019, pp. 1-6.

>[5] M. Abouheaf and W. Gueaieb, "Neurofuzzy Reinforcement Learning Control Schemes for Optimized Dynamical Performance," 2019 IEEE International Symposium on Robotic and Sensors Environments (ROSE), Ottawa, ON, Canada, 2019, pp. 1-7.

>[6] Xiao-Dong Zhuang, Qing-Chun Meng, Han-Ping Wang and Bo Yin, "Multi-scale reinforcement learning with fuzzy state," Proceedings. International Conference on Machine Learning and Cybernetics, Beijing, China, 2002, pp. 1523-1528 vol.3.