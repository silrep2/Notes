# NuMVC Note

## Denote

### cost(G, X)  
 
所有未被覆盖的边权重加起来。距离正确答案越远，值越大。

### dscore(v)
 
改变一个v的状态后的cost差

等于 `新的cost - 旧的cost`

dscore > 0  往好的方向发展

### confChange(v)
 
点v能否加入集合C

confChange = 0 : 禁止加入C

如果有一个点被移除了，它会被置为0，避免它之后马上又被加集合

## Pseudocode

```
利用贪心算法进行初始化集合C
一直迭代直到次数过多
	如果所有边都被覆盖（这是一个可行解）
		C* = C 保存当前最优可行解
		遍历C中的点，把dscore最高的点从C中删掉
	直到露出一个未被覆盖的边
	
	（删除一个点）
	再在C中选一个dscore最高的点u
	从集合C中删除点u，u的conf置为0。u的邻居的confChange置为1。

	（加入一个点）
	随机选择一个未被覆盖的边e
	e的两端选一个点v，confChange为1且dscore高。
	把v加进C，v的邻居conf置1

	（为下次迭代做准备）
	把所有未覆盖的边权重+1
	如果权重平均值过高，全部乘以e
```






