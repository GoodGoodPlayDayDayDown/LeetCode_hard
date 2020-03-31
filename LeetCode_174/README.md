# 题目名称：地下城游戏

## 题目链接：https://leetcode-cn.com/problems/dungeon-game/


## 题解：

M*N的二维网格D，K初始位于左上角，P位于右下角，K通过向下或者向右运动一直到P的位置（M+N-2步），在每个房间有一个数字，K初始有一个数字，每进入一个房间则数字相加作为K的数字，要求最后到P的位置数值大于等于零。求K初始数字的最小值，也即求经过房间的最大值。

可以看到，每一步我们都要做出决策：向右还是向下。而我们一共要做出M+N-2步决策，包括M-1步向下，N-1步向右，所以我们的问题关键在于顺序。先向右后向下与反过来的顺序得到的数字和不一定相同，但是在同一种情况下，就是到达同一个位置的情况下，我们要保证数字最大（因为之后解决的问题完全相同），所以我们要用到动态规划。

我们设计一个二维的动态规划矩阵DP[x][y]，它由左边和上边到达，所以它的值为OPT[x][y]=MAX{OPT[x-1][y]+D[x][y], OPT[x][y-1]+D[x][y]}。注意初始化，在边界处，上边界直接由初始点一路向右得到，左边界由初始点一路向下得到，初始点的值即为该点的数值。最后返回右下角的数值。