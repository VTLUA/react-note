## React-note

这篇文章是用于复习React的一些知识点

### 什么是声明式编程
声明式编程是一种编程范式，它关注的是你要做什么，而不是如何做。它表达逻辑而不显式地定义步骤。这意味着我们需要根据逻辑的计算来声明要显示的组建。他没有描述控制流步骤。声明式编程的例子有HTML/SQL。

```html
    // html file
    <div>
        <p>Declarative Programming</p>
    </div>
```

```sql
   // sql file
   select * from student where firstName = "declarative";
```

### 声明式编程 VS 命令式编程
声明式编程的编写方式描述了应该做什么，而命令式编程描述了如何做。在声明式编程中，让编译器决定如何做事情。声明式程序很容易推理，因为本身代码描述了它做什么。

```js
    const numers = [1,2,3,4,5];

    // 声明式
    const doubleWithDec = numbers.map(number => number * 2);

    // 命令式编程
    const doubleWithImp = [];
    for (let i = 0; i < numbers.length; i++) {
        const numberDouble = numbers[i] * 2;
        doubleWithImp.push(numberDouble);
    }
```
### 什么是函数式编程
函数式编程是声明式编程的一部分。JavaScript中的函数是第一公民，这意味着函数是数据，你可以像保存变量一样在应用程序中保存、检索和传递这些函数。

+ 不可变性
+ 纯函数
+ 数据转换
+ 高阶函数
+ 递归
+ 组合

> ****不可变性****
>
>不可变性意味着不可改变。在函数编程中，你无法更改数据，也不能更改数据。如果要更改数据，则须复制数据副本来进行更改。
>
>例如，这是一个student对象和changeName函数，如果要改变学生的名称，则要先复制对象，返回新对象。
>
>在JavaScript中，函数参数是对实际数据的引用，你不应该是用student.firstName = "test1"，这会改变实际的student对象，应该使用Object.assign复制返回新对象。

```js
   let student = {
        firstName: "testing",
        lastName: "testing",
        age: "18"
   };
   
   function changeName (name) {
        // student.firstName = "testing11" //should not do it
        let copiedStudent = Object.assign({}, student);
        copiedStudent.firstName = "testing1";
        return copiedStudent;
   };
   
   console.log(changeName(student));

   console.log(student);
```
> ****纯函数****
> 
> 纯函数是始终接受一个或者多个参数并进行计算后返回数据或者函数的函数。它没有副作用，例如设置全局状态，更改应用程序状态，它总是将参数视为不可变数据。
> 
> 我想使用 appendAddress 的函数向student对象添加一个地址。 如果使用非纯函数，它没有参数，直接更改 student 对象来更改全局状态。
> 
> 使用纯函数，它接受参数，基于参数计算，返回一个新对象而不修改参数

```js
   let student = {
        firstName: "testing",
        lastName: "testing",
        age: "18"
   };
   
   // 非纯函数
   function addAddress () {
        student.address = {streetNumber:"0000", streetName: "first", city:"somecity"};
   };
   
   console.log(addAddress());
   
   // 纯函数
   function addAddress () {
        let copyStudent = Object.assign({}, student);
        copyStudent.address = {streetNumber:"0000", streetName: "first", city:"somecity"};
        retutn copyStudent;
   }
   
   console.log(appendAddress(student));

   console.log(student);
```

> **** 数据转换 ****
> 
> 我们讲了很多不可变性的内容，如果数据是不可变的，我们如何改变数据。如上所诉，我们总是生成原始数据的转换副本，而不是直接更改原始数据。
> 
> 再介绍一些 javascript内置函数，当然还有很多其他的函数，这里有一些例子。所有这些函数都不改变现有的数据，而是返回新的数组或对象。
> 
```js
   let cities = ["irving", "lowell", "houston"];
   
   // we can get the comma separated list
   console.log(cities.join(","));
   // "irving, lowell, houston"
   
   // if we want to get cities start with i
   const citiesA = cities.filter((items, i) => i == 0);
   console.log(citiesA);
   // ["irving"]
   
   // if we want to capitalize all the cities
   const citiesB = cities.map(items => items.toUpperCase());
   console.log(citiesB);
   // ["IRVING", "LOWELL", "HOUSTON"]
```
> **** 高阶函数 ****
> 
> 高阶函数是将函数作为参数或者函数的函数。有时它们都有，这些高阶函数可以操作其他的函数。
> 
> Array.map，Array.filter和Array.reduce是高阶函数，因为它们将函数作为参数。
> 
```js
    const numbers = [10,20,40,50,60,70,80]

    const out1 = numbers.map(num => num * 100);
    console.log(out1);
    // [ 1000, 2000, 4000, 5000, 6000, 7000, 8000 ]

    const out2 = numbers.filter(num => num > 50);
    console.log(out2);
    // [ 60, 70, 80 ]

    const out3 = numbers.reduce((out,num) => out + num);
    console.log(out3);
    // 330
```
> 下面是另一个名为isPersonOld的高阶函数示例，该函数接受另外两个函数，分别是 message和isYoung 。
> 
```js
   const message = msg => `He is ${msg}`;
   const isYoung = age => age < 25;
   
   function isPersonOld (age, isYoung, message) {
        const result = isYoung(age) ? message('young') : message('old');
        return result;
   }
   
   console.log(isPersonOld(12, isYoung, message))
   // He is young
```
> **** 递归 ****
> 
> 递归是一种函数在满足一定条件之前调用自身方法的技术。只要在逻辑不复杂的情况下，我们最好使用循环。
> 
> 下面是一个演示递归的例子，在这个递归中，打印一个类似于楼梯的名称。我们也可以使用for循环，但只要可能，我们更喜欢循环。
> 
```js
   function printMyName (name, count) {
        if (count <= name.length) {
            console.log(name.substring(0, count));
            printMyName(name, ++count);
        }
   }
   console.log(printMyName('abcdefg', 1));
   /**
     a
     ab
     abc
     abcd
     abcde
     abcdef
     abcdefg
   */
   
   // for循环
    var name = "Bhargav"
    var output = "";
    for(let i=0; i<name.length; i++) {
        output = output + name[i];
        console.log(output);
    }
```

