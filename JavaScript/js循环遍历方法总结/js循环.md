
# js循环遍历
### for循环
```javascript
let arr = [1,2,3];
for (let i=0; i<arr.length; i++){
 console.log(i,arr[i])
}
```
- for通常用于遍历数组

### for in
```javascript
let obj = {name:'zhou',age:'**'}
for(let i in obj){
 console.log(i,obj[i])
}
// name zhou
// age **
```
- for in 循环主要用于遍历普通对象，i 代表对象的 key 值，obj[i] 代表对应的 value,当用它来遍历数组时候，多数情况下也能达到同样的效果，但是你不要这么做，这是有风险的，因为 i 输出为字符串形式，而不是数组需要的数字下标，这意味着在某些情况下，会发生字符串运算，导致数据错误，比如：'52'+1 = '521' 而不是我们需要的 53。另外 for in 循环的时候，不仅遍历自身的属性，还会找到 prototype 上去，所以最好在循环体内加一个判断，就用 obj[i].hasOwnProperty(i)，这样就避免遍历出太多不需要的属性。

### while

```javascript
let cars=["BMW","Volvo","Saab","Ford"];
let i=0;
for (;cars[i];)
{
console.log(cars[i])
i++;
};
// BMW
// Volvo
// Saab
// Ford

//然后是 while 循环方法
cars=["BMW","Volvo","Saab","Ford"];
var i=0;
while (cars[i])
{
console.log(cars[i] + "<br>")
i++;
};
```
- 它们可以实现同样的效果，事实上它们底层的处理是一样的，不过 for 循环可以把定义、条件判断、自增自减操作放到一个条件里执行，代码看起来方便一些，仅此而已。

### do while
```javascript
let i = 3;
do{
 console.log(i)
 i--;
}
while(i>0)
// 3
// 2
// 1
```
- do while 循环是 while 循环的一个变体，它首先执行一次操作，然后才进行条件判断，是 true 的话再继续执行操作，是 false 的话循环结束。

### forEach
```javascript
let arr = [1,2,3];
arr.forEach((i,index)=>{
console.log(i,index)
})
// 1 0
// 2 1
// 3 2
```

- forEach循环，数组中有几个元素就循环几次。循环数组中每一个元素并采取操作， 没有返回值， 可以不用知道数组长度,他有三个参数，只有第一个是必需的，代表当前下标下的 value。另外请注意，forEach 循环在所有元素调用完毕之前是不能停止的，它没有 break 语句，如果你必须要停止，可以尝试 try catch 语句，就是在要强制退出的时候，抛出一个 error 给 catch 捕捉到，然后在 catch 里面 return，这样就能中止循环了，如果你经常用这个方法，最好自定义一个这样的 forEach 函数在你的库里。

### map
```javascript

let arr = [1,2,3];
let tt = arr.map(function(i){
 console.log(i)
 return i*2;
})
// [2,4,6]
```

- map() 方法返回一个新数组，数组中的元素为原始数组元素调用函数处理后的值。注意：map 和 forEach 方法都是只能用来遍历数组，不能用来遍历普通对象。

### filter
   ```javascript
var arr = [{name:"jack",age:16},{name:"mary",age:28},{name:"tom",age:45}]
 let result = arr.filter(v => v.age>20)
 console.log(result)
```
![036376bf41d09f6e49a5f4c9752e713a.png](en-resource://database/13996:1)

- filter 方法是 Array 对象内置方法，它会返回通过过滤的元素，不改变原来的数组

### some
```javascript
let arr = [1,2,3]
let t = arr.some(i=>{
return i>1
})
//true
```
- 用于见此数组中元素是否满足指定条件，返回布尔值，不改变元素组

### every
```javascript
let arr = [1,2,3]
let t = arr.every(i=>{
retuen i>1
})
```
//1
- every 方法为数组中的每个元素执行一次 callback 函数，直到它找到一个使 callback 返回 false（表示可转换为布尔值 false 的值）的元素。如果发现了一个这样的元素，every 方法将会立即返回 false

### reduce
```javascript
let arr = [1,2,3];
let ad = arr.reduce(function(i,j){
 return i+j;
})
// 6

```

- reduce() 方法接收一个函数作为累加器，数组中的每个值（从左到右）开始缩减，最终计算为一个值,reduceRight()方法则从末尾开始计算

### for of
```javascript

let arr = ['name','age'];
for(let i of arr){
 console.log(i)
}
// name
// age
```

- for of 循环是 Es6 中新增的语句，用来替代 for in 和 forEach，它允许你遍历 Arrays（数组）, Strings（字符串）, Maps（映射）, Sets（集合）等可迭代(Iterable data)的数据结构,注意它的兼容性。