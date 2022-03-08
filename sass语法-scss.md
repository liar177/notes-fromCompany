# sass语法-scss

## 1.css功能扩展

### 1.1嵌套规则

这点基本上与less类似，不再赘述

### 1.2 父选择器 `&` (Referencing Parent Selectors: `&`)

 在嵌套 CSS 规则时，有时也需要直接使用嵌套外层的父选择器，例如，当给某个元素设定 `hover` 样式时，或者当 `body` 元素有某个 classname 时，可以用 `&` 代表嵌套规则外层的父选择器。 

```scss
a {
  font-weight: bold;
  text-decoration: none;
  &:hover { text-decoration: underline; }
  body.firefox & { font-weight: normal; }
}
```

编译为：

```css
a {
  font-weight: bold;
  text-decoration: none; }
  a:hover {
    text-decoration: underline; }
  body.firefox a {
    font-weight: normal; }
```

### 1.3属性嵌套（觉得不常用，没有记录）

## 2 SassScript

### 2.1变量`$` (Variables: `$`)

变量以美元符号开头，变量名称基本上与选择器名称构成相同，赋值方法与css属性写法一致

```
$parent-color: #ccc;
#app{
	background-color: $parent-color;
}
```



scss中变量支持块级作用域，作用范围类似 let 和 const 定义的变量，

​	将局部变量转换为全局变量可以使用 !global

```scss
#main {
  $width: 5em !global;
  width: $width;
}

#sidebar {
  width: $width;
}
```

### 2.2 运算

scss支持的运算类型完整且强大，会在不同单位运算时自动转换值，值得注意的是除法

以下三种情况 `/` 将被视为除法运算符号，其他情况下不会做编译处理：

- 如果值，或值的一部分，是变量或者函数的返回值
- 如果值被圆括号包裹（这点应该记住）
- 如果值是算数表达式的一部分

### 2.3函数（这部分比较复杂，暂不做了解）

### 2.4 @extend

 在设计网页的时候常常遇到这种情况：一个元素使用的样式与另一个元素完全相同，但又添加了额外的样式，这种情况下就可以使用 @extend继承第一个元素选择器下的所有样式。 

```scss
.error {
  border: 1px #f00;
  background-color: #fdd;
}
.seriousError {
  @extend .error;
  border-width: 3px;
}
```

同一个选择器可以延伸给多个选择器，它所包含的属性将继承给所有被延伸的选择器：

```scss
.error {
  border: 1px #f00;
  background-color: #fdd;
}
.attention {
  font-size: 3em;
  background-color: #ff0;
}
.seriousError {
  @extend .error;
  @extend .attention;
  border-width: 3px;
}
```

当一个选择器延伸给第二个后，可以继续将第二个选择器延伸给第三个，例如：

```scss
.error {
  border: 1px #f00;
  background-color: #fdd;
}
.seriousError {
  @extend .error;
  border-width: 3px;
}
.criticalError {
  @extend .seriousError;
  position: fixed;
  top: 10%;
  bottom: 10%;
  left: 10%;
  right: 10%;
}
```

### 2.5混合 @mixin

1.定义混合指令@mixin

```scss
@mixin large-text {
  font: {
    family: Arial;
    size: 20px;
    weight: bold;
  }
  color: #ff0000;
}
```

2.引用混合样式 @include   有点类似@extend 但是可以想函数一样设置入参传入

```scss
.page-title {
  @include large-text;
  padding: 4px;
  margin-top: 10px;
}
```

3.参数 (Arguments)

 参数用于给混合指令中的样式设定变量，并且赋值使用。在定义混合指令的时候，按照变量的格式，通过逗号分隔，将参数写进圆括号里。引用指令时，按照参数的顺序，再将所赋的值对应写进括号： 

```scss
@mixin sexy-border($color, $width: 1in) {
  border: {
    color: $color;
    width: $width;
    style: dashed;
  }
}
p { @include sexy-border(blue); }
h1 { @include sexy-border(blue, 2in); }
```

