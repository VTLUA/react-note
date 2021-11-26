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

```
Syntax highlighted code block

# Header 1
## Header 2
### Header 3

- Bulleted
- List

1. Numbered
2. List

**Bold** and _Italic_ and `Code` text

[Link](url) and ![Image](src)
```

For more details see [Basic writing and formatting syntax](https://docs.github.com/en/github/writing-on-github/getting-started-with-writing-and-formatting-on-github/basic-writing-and-formatting-syntax).

### Jekyll Themes

Your Pages site will use the layout and styles from the Jekyll theme you have selected in your [repository settings](https://github.com/VTLUA/react-note/settings/pages). The name of this theme is saved in the Jekyll `_config.yml` configuration file.

### Support or Contact

Having trouble with Pages? Check out our [documentation](https://docs.github.com/categories/github-pages-basics/) or [contact support](https://support.github.com/contact) and we’ll help you sort it out.
