# N皇后

思路很简单

第一排放皇后，

然后第二排，放皇后，如果冲突，回溯

如果不冲突，继续放

如果放的时候发现每一个格子都冲突，说明放错了，直接回溯到上一轮继续下一个

问题1 怎么判断是不是冲突，？
同一列的话比较好检查，因为存一下列就行

同一行的可以不用管，因为我们一行只放一个

下面考虑交叉的

在一个矩阵中，任何一条斜线上的坐标 (row, col) 都有固定特征：

主对角线（左上到右下 \）：这条线上的所有格子，它们的 row - col 的差值是固定不变的。

副对角线（右上到左下 /）：这条线上的所有格子，它们的 row + col 的和是固定不变的。

为了能够O1的查询，我们用set来去存储

我们只需要 3 个 Set：一个记录用过的列，一个记录用过的主对角线差值，一个记录用过的副对角线和。放皇后之前查一下这三个 Set，瞬间就能判断安不安全！



```python 
class Solution:
    def solveNQueens(self, n: int) -> List[List[str]]:
        res = []#存放答案
        board = [['.']*n for _ in range(n)]#就是棋盘
        l = set()
        diag1 = set()#记录row+col
        diag2 = set()#记录row-col
        def backtract(row):
            if row == n:#到最后了，搜集一下答案
                res.append(["".join(r) for r in board])
                return 

            #遍历每一列，尝试放
            for col in range(n):
                if col in l or (row+col) in diag1 or (row-col) in diag2:
                    continue
                #放皇后
                board[row][col] = "Q"
                l.add(col)
                diag1.add(row+col)
                diag2.add(row-col)
                #然后下一行
                backtract(row+1)

                #然后回溯删除
                board[row][col] = "."
                l.remove(col)
                diag1.remove(row+col)
                diag2.remove(row-col)
        backtract(0)
        return res





```