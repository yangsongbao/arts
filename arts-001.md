

## Algorithm

题目：https://leetcode.com/problems/two-sum/

难度：easy

Given an array of integers, return indices of the two numbers such that they add up to a specific target.

You may assume that each input would have exactly one solution, and you may not use the same element twice.

Example:

Given nums = [2, 7, 11, 15], target = 9,

Because nums[0] + nums[1] = 2 + 7 = 9,
return [0, 1].

分析：

找个数组中两数之和为特定值的数sum，返回其下标。

遍历数组，遍历一个值m的时候，想知道数组中存不存在值sum-m，则可以将遍历过的值存入map中，将可以在O(1)的时间复杂度内找出有没有(sum-m)及其下标，代码如下。

``` golang
func twoSum(nums []int, target int) []int {

	tmp := make(map[int]int)

	for i, num := range nums {
		v, exists := tmp[target - num]
		if  exists {
			return []int{v, i}
		}
		tmp[num] = i
	}
	return []int{}
}
```

## Review
文章：https://medium.com/golang-learn/go-project-layout-e5213cdcfaa2

最近刚转从java语言到go语言开发项目，对其项目包管理的方式有所疑惑，找到了这篇文章。说一下我的收获：
- go语言有工作区的概念，正规的项目Go代码保存在工作区中
- go的工作区中会有src，bin，pkg三个目录，
 - src：放源代码
 - bin：放编译后的可执行文件，可执行文件名字与源代码文件名字一样
 - pkg：放编译后的包文件，包文件名字与所在目录一样，注意：名字与package无关
- java语言的包名要和目录名一致，go语言的则不用，可以不同
- 不想被外部引用的代码需要放在“internal”目录中
- vendor目录用来放置你想按照原样导入和使用的代码


## Tip
http://wiki.jikexueyuan.com/project/go-command-tutorial/0.12.html

罗列go tools中一些常用的命令，对于新人很有用

gotools
- gofmt：格式化代码
- godoc：从注释中生成文档
- gotest：执行测试用例
- go build：编译器会把所有 \*.go 除了\*_test.go进行编译
- go install：用于编译并安装指定的代码包及它们的依赖包。
- go run：编译并运行命令源码文件。
- go get：根据要求和实际情况从互联网上下载或更新指定的代码包及其依赖包，并对它们进行编译和安装。
- go clean：删除掉执行其它命令时产生的一些文件和目录。
- go fix：把指定代码包的所有Go语言源码文件中的旧版本代码修正为新版本的代码。
- go list：列出指定的代码包的信息。
- go vet：用于检查Go语言源码中静态错误的简单工具。



## Share

[golang的协程调度-硬核原理](https://mp.weixin.qq.com/s/EMOcnVzVxw40EsDBFYWzRQ)
