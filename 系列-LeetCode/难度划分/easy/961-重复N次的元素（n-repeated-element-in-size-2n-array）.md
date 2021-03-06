961 - 重复N次的元素（n-repeated-element-in-size-2n-array）
===

> Create by **jsliang** on **2020-01-28 11:06:31**  
> Recently revised in **2020-01-28 11:22:36**

## <a name="chapter-one" id="chapter-one"></a>一 目录

**不折腾的前端，和咸鱼有什么区别**

| 目录 |
| --- | 
| [一 目录](#chapter-one) | 
| <a name="catalog-chapter-two" id="catalog-chapter-two"></a>[二 前言](#chapter-two) |
| <a name="catalog-chapter-three" id="catalog-chapter-three"></a>[三 解题及测试](#chapter-three) |
| <a name="catalog-chapter-four" id="catalog-chapter-four"></a>[四 LeetCode Submit](#chapter-four) |
| <a name="catalog-chapter-five" id="catalog-chapter-five"></a>[五 解题思路](#chapter-five) |

## <a name="chapter-two" id="chapter-two"></a>二 前言

> [返回目录](#chapter-one)

* **难度**：简单
* **涉及知识**：哈希表
* **题目地址**：https://leetcode-cn.com/problems/n-repeated-element-in-size-2n-array/
* **题目内容**：

```
在大小为 2N 的数组 A 中有 N+1 个不同的元素，
其中有一个元素重复了 N 次。

返回重复了 N 次的那个元素。

示例 1：

输入：[1,2,3,3]
输出：3

示例 2：

输入：[2,1,2,5,3,2]
输出：2

示例 3：

输入：[5,1,5,2,5,3,5,4]
输出：5 

提示：

4 <= A.length <= 10000
0 <= A[i] < 10000
A.length 为偶数

来源：力扣（LeetCode）
链接：https://leetcode-cn.com/problems/n-repeated-element-in-size-2n-array
著作权归领扣网络所有。商业转载请联系官方授权，非商业转载请注明出处。
```

## <a name="chapter-three" id="chapter-three"></a>三 解题及测试

> [返回目录](#chapter-one)

小伙伴可以先自己在本地尝试解题，再回来看看 **jsliang** 的解题思路。

* **LeetCode 给定函数体**：

```js
/**
 * @param {number[]} A
 * @return {number}
 */
var repeatedNTimes = function(A) {
    
};
```

根据上面的已知函数，尝试破解本题吧~

确定了自己的答案再看下面代码哈~

> index.js

```js
/**
 * @name 重复N次的元素
 * @param {number[]} A
 * @return {number}
 */
const repeatedNTimes = (A) => {
  for (let i = 0; i < A.length; i++) {
    if (A.indexOf(A[i]) !== A.lastIndexOf(A[i])) {
      return A[i];
    }
  }
};

console.log(repeatedNTimes([2, 1, 2, 5, 3, 2])); // 2
```

`node index.js` 返回：

```js
2
```

## <a name="chapter-four" id="chapter-four"></a>四 LeetCode Submit

> [返回目录](#chapter-one)

```js
Accepted
* 102/102 cases passed (72 ms)
* Your runtime beats 82.72 % of javascript submissions
* Your memory usage beats 56.5 % of javascript submissions (36.8 MB)
```

## <a name="chapter-five" id="chapter-five"></a>五 解题思路

> [返回目录](#chapter-one)

经过前面题目的摧残，看到这道题我有点怀疑自己眼光，是不是看错了，结果还真是这样：

> 【解法一】indexOf & lastIndexOf

```js
const repeatedNTimes = (A) => {
  for (let i = 0; i < A.length; i++) {
    if (A.indexOf(A[i]) !== A.lastIndexOf(A[i])) {
      return A[i];
    }
  }
};
```

enm...Submit 提交：

```js
Accepted
* 102/102 cases passed (72 ms)
* Your runtime beats 82.72 % of javascript submissions
* Your memory usage beats 56.5 % of javascript submissions (36.8 MB)
```

这样子的话，我可以变着法子虐他啊！

先用 `Map`：

> 【解法二】Map

```js
const repeatedNTimes = (A) => {
  const map = new Map();
  for (let i = 0; i < A.length; i++) {
    if (map.get(A[i])) {
      return A[i];
    }
    map.set(A[i], 'jsliang');
  }
};
```

Submit 提交：

```js
Accepted
* 102/102 cases passed (72 ms)
* Your runtime beats 82.72 % of javascript submissions
* Your memory usage beats 69.5 % of javascript submissions (36.3 MB)
```

再用 `Array`：

> 【解法三】Array

```js
const repeatedNTimes = (A) => {
  const arr = [];
  for (let i = 0; i < A.length; i++) {
    if (arr[A[i]] !== undefined) {
      return A[i];
    }
    arr[A[i]] = A[i];
  }
};
```

Submit 提交：

```js
Accepted
* 102/102 cases passed (72 ms)
* Your runtime beats 82.72 % of javascript submissions
* Your memory usage beats 96.5 % of javascript submissions (36.1 MB)
```

最后我就不再探索啦，太过简单了，不想瞅瞅其他大佬的答案了~

如果小伙伴有更好的思路想法，欢迎评论留言或者私聊 **jsliang**~

---

**不折腾的前端，和咸鱼有什么区别！**

![图](../../../public-repertory/img/z-index-small.png)

**jsliang** 会每天更新一道 LeetCode 题解，从而帮助小伙伴们夯实原生 JS 基础，了解与学习算法与数据结构。

**浪子神剑** 会每天更新面试题，以面试题为驱动来带动大家学习，坚持每天学习与思考，每天进步一点！

扫描上方二维码，关注 **jsliang** 的公众号（左）和 **浪子神剑** 的公众号（右），让我们一起折腾！

> <a rel="license" href="http://creativecommons.org/licenses/by-nc-sa/4.0/"><img alt="知识共享许可协议" style="border-width:0" src="https://i.creativecommons.org/l/by-nc-sa/4.0/88x31.png" /></a><br /><span xmlns:dct="http://purl.org/dc/terms/" property="dct:title">jsliang 的文档库</span> 由 <a xmlns:cc="http://creativecommons.org/ns#" href="https://github.com/LiangJunrong/document-library" property="cc:attributionName" rel="cc:attributionURL">梁峻荣</a> 采用 <a rel="license" href="http://creativecommons.org/licenses/by-nc-sa/4.0/">知识共享 署名-非商业性使用-相同方式共享 4.0 国际 许可协议</a>进行许可。<br />基于<a xmlns:dct="http://purl.org/dc/terms/" href="https://github.com/LiangJunrong/document-library" rel="dct:source">https://github.com/LiangJunrong/document-library</a>上的作品创作。<br />本许可协议授权之外的使用权限可以从 <a xmlns:cc="http://creativecommons.org/ns#" href="https://creativecommons.org/licenses/by-nc-sa/2.5/cn/" rel="cc:morePermissions">https://creativecommons.org/licenses/by-nc-sa/2.5/cn/</a> 处获得。