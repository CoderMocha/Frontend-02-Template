# 学习笔记
> 7月6日 第二周

## JS语言通识
### 1 范用语言分类方法
#### 1.1 按语法分类
- 非形式语言
    - 中文、韩文
- 形式语言（***乔姆斯基谱系***）
    - 0型：无限制文范
    - 1型：上下文相关文法
    - 2型：上下文无关文法
    - 3型：正则文法（***Regular***）
    
#### 1.2 产生式(BNF)
- 用尖括号包裹起来的名称表示语法结构名
- 语法结构分成基础结构和需要用其他语法结构定义的复合结构
    - 基础结构称为终结符（***Terminal Symbol***）
    - 复合结构称为非终结符（***Nonterminal Symbol***）
    - 引号和中间的字符表示终结符
    - 可以有括号
    - `*` 表示一次或多次
    - `|` 表示或
    - `+` 表示至少一次
 
e.g. 用BNF表示四则运算 1+2*3  

终结符：
- Number
- `+`
- `-`
- `*`
- `/`

非终结符
- MultiplicativeExpress
- AdditiveExpress
```xml
<AdditiveExpress> ::= 
    <MultiplicativeExpress> | <AdditiveExpress> "+" <MultiplicativeExpress> | <AdditiveExpress> "-" <MultiplicativeExpress>
<MultiplicativeExpress> ::= 
    <Number> | <MultiplicativeExpress> "*" <Number> | <MultiplicativeExpress> "/" <Number>
```
习题：编写带括号的四则运算的产生式

----

#### 1.3 通过产生式理解乔姆斯基谱系
- 0型：无限制文范
  - ?::=?
- 1型：上下文相关文法
  - ?`<A>`?::=?`<B>`?
- 2型：上下文无关文法
  - `<A>`::=?
- 3型：正则文法（***Regular***）
  - `<A>`::=`<A>`?
  - `<A>`::=?`<A>` 
  
#### 1.4 其他产生式
- EBNF
- ABNF
- Customized
  
#### 1.5 现代语言的特例
- C++中，`*`可能表示乘法符号或是指针，具体指哪一个，取决于`*`前面的标识符是否被声明为类型；
- VB中，`<`可能是小于号，也可能是XML直接量的开始，取决于当前位置是否可以接受XML直接量；
- Python中，行首的tab符和空格会根据上一行的行首空白以一定规则被处理成虚拟终结符 ***indent*** 或 ***dedent***;
- JavaScript中，`/`可能是除号，也可能是正则开头，处理方式类似于VB，字符串模版中也需要特殊处理`}`，以及自动插入`;`规则。

#### 1.6 语言的分类
- 形式语言——按用途分类
  - 数据描述语言
    -  JSON
    -  HTML
    -  XAML
    -  SQL
    -  CSS
  - 编程语言
    - C
    - C++
    - Java
    - C#
    - Python
    - Ruby
    - Perl
    - Lisp
    - T-SQL
    - Clojure
    - Haskell
    - JavaScript
- 形式语言——按表达方式分类
  - 声明式语言
    -  ……
  - 命令式语言
    - ……

#### 1.7 图灵完备性
> 所有的可计算的问都可以用来描述的语言
- 命令式——图灵机
  - goto
  - if和while
- 声明式——Lambda
  - 递归
  
#### 1.8 动态与静态
- 动态
  - 在用户的设备上/在线服务器上
  - 产品实际运行时
  - Runtime
- 静态
  - 在程序员的设备上
  - 在产品开放时
  - Compiletime  

#### 1.9 类型系统
- 动态类型系统和静态类型系统
- 强类型和若类型
  - String + Number
  - String == Boolean
- 复合类型
  - 结构体
  - 函数签名
- 子类型
- 泛型
  - 逆变/协变   
  
#### 1.10 一般命令式编程语言
- Atom
  - Identifier
  - Literal 
- Expression
  - Atom
  - Operator
  - Punctuator
- Statement
  - Expression 
  - Keyword
  - Punctuator
- Structure
  - Class
  - Process
  - Namespace 
- Program
  - Program
  - Module
  - Package
  - Library 
  
## 重学JavaScript
### 1 
- 语法
- 语义
- 运行时
- Atom
- Grammer
  - Literal
  - Variable
  - Keywords
  - Whitespace
  - Line Terminal
- Runtime 
- Type
- Execution Content
- Types
  - Number
  - String
  - Boolean
  - Object
  - Null
  - Undefined
  - Symbol 


### 2 JS类型——Number
> IEEE 754 Double Float
- Sign(1) 符号位，缩写S
- Exponent(11) 指数位，缩写E
  - 指数位大于1000000000 BIN 时表示正 
  - 指数位小于1000000000 BIN 时表示负
- Fraction(52) 精度位，缩写F
  
运算公式：  
```math
Value = (-1)^S * (1+F) * 2^E
```
