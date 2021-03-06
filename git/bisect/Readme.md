# git bisect
> 将代码提交的历史，按照两分法不断缩小定位。所谓"两分法"，就是将代码历史一分为二，确定问题出在前半部分，还是后半部分，不断执行这个过程，直到范围缩小到某一次代码提交。

```
// 假如一共51次提交记录
git log --pretty=oneline

// Head最近一次 4d83cf第一次，执行命令以后，代码库就会切换到这段范围正当中的那一次提交，本例是第26次提交。
git bisect start [终点] [起点]

// 26没有问题，错误是在代码历史的后半段引入的。执行上面的命令，Git就自动切换到后半段的中点（第38次提交）。
git bisect good

// 76有问题，Git就自动切换到第26次到第38次的中点（第32次提交)。
git bisect bad

// 接下来，不断重复这个过程，直到成功找到出问题的那一次提交为止。这时，Git会给出如下的提示。
b47892 is the first bad commit
```

