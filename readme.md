# JavaScript对象基础
## 1. 声明对象的2种语法
```
let obj = { 'name' : 'frank" , 'age' : 18}        简单写法

let obj = new Object({'name' : 'frank','age' : 18})        正规写法，有点麻烦
```
## 2. 如何删除对象的属性
```
let obj = { 'name' : 'frank" , 'age' : 18 } 
```
1. `delete obj.name`  -- 会删除'name',并且控制台返回true
2. `delete obj['name']`  -- 第二种写法
3. `'name' in obj` -- 可使用 'in' 来查看是否还在 obj 中,但是无法判断是自身还是共有的,控制台返回true/false
4. `obj.hasOwnProperty('name')` -- 效果与3类似,可以判断属性是自身的还是共有的

## 3. 如何查看对象的属性
```
let obj = { 'name' : 'frank" , 'age' : 18 }
```
1. `Object.keys(obj)` -- 可以查看到自身所有的属性,包括prototype 
2. `Object.values(obj)` -- 查看自身属性的值
3. 直接控制台输入 `obj` 也可以看到自身的值与属性
4. `Object.entries(obj)` -- 返回以数组的形式查看自身属性与值
![图](/image/Object.entries(obj).jpg)   

5. `console.dir(obj)` -- 以目录方式打印出所有属性与值.

## 4. 如何修改或增加对象的属性

1. `let obj = { 'name' : 'frank" , 'age' : 18 }` -- 直接赋值
2. `obj.name = 'tom'` , `obj.age =20` -- 这就可以修改其属性的值
3. `Object.assign(obj,{name:'tom',age:20,sex:'man'})` -- 批量修改或增加
> 注意:已有的属性则修改,无则添加此属性.这些操作只能改自身与增自身.

## 5. 如何修改与增加自身的共有属性(原型)
1. `obj.__proto__.toString = 'xxx'` 
2. `Object.prototype.toString = 'yyy'`
> 不建议使用此方法,会导致许多问题产生.
### 可采用另一种方法
``` 
let obj = Object.create(obj2)
let obj['name'] = 'tom'
``` 
## 6.'name' in obj和obj.hasOwnProperty('name') 的区别
1. `'name' in obj` -- 可使用 'in' 来查看是否还在 obj 中,但是无法判断是自身还是共有的,控制台返回true/false
2. `obj.hasOwnProperty('name')` -- 效果与3类似,但可以判断属性是自身的还是共有的.

# 总结:
* 删除: `delete obj['name'] | delete obj.name`
* 查:  
     `Object.keys(obj)`   
     `Object.values(obj)`   
     `Object.entries(obj)`   
     `console.dir(obj)`   
* 改或增:  
`obj.name = 'tom'` , `obj.age =20`  
`Object.assign(obj,{name:'tom',age:20,sex:'man'})`
