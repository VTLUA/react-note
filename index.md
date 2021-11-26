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

>不可变性
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


