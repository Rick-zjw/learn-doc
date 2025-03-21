好的，我将为你整理一份 TypeScript 的学习知识库，内容覆盖基础入门与进阶语法部分，并以结构清晰的文档形式呈现，便于你学习和查阅。
完成后我会将文档内容展示给你。

# TypeScript 学习知识库（基础与进阶）

TypeScript 是 JavaScript 的**超集**，增加了强大的静态类型系统，可以在编译阶段捕获错误 ([TypeScript 中文手册 - TypeScript 中文手册](https://typescript.bootcss.com/#:~:text=TypeScript%E5%85%B7%E6%9C%89%E7%B1%BB%E5%9E%8B%E7%B3%BB%E7%BB%9F%EF%BC%8C%E4%B8%94%E6%98%AFJavaScript%E7%9A%84%E8%B6%85%E9%9B%86%E3%80%82%20%E5%AE%83%E5%8F%AF%E4%BB%A5%E7%BC%96%E8%AF%91%E6%88%90%E6%99%AE%E9%80%9A%E7%9A%84JavaScript%E4%BB%A3%E7%A0%81%E3%80%82%20TypeScript%E6%94%AF%E6%8C%81%E4%BB%BB%E6%84%8F%E6%B5%8F%E8%A7%88%E5%99%A8%EF%BC%8C%E4%BB%BB%E6%84%8F%E7%8E%AF%E5%A2%83%EF%BC%8C%E4%BB%BB%E6%84%8F%E7%B3%BB%E7%BB%9F%E5%B9%B6%E4%B8%94%E6%98%AF%E5%BC%80%E6%BA%90%E7%9A%84%E3%80%82))。TypeScript 代码需要经过编译（`tsc` 编译器）转换为纯 JavaScript，然后再运行，因此它在任何支持 JavaScript 的环境中都能使用 ([TypeScript 中文手册 - TypeScript 中文手册](https://typescript.bootcss.com/#:~:text=TypeScript%E5%85%B7%E6%9C%89%E7%B1%BB%E5%9E%8B%E7%B3%BB%E7%BB%9F%EF%BC%8C%E4%B8%94%E6%98%AFJavaScript%E7%9A%84%E8%B6%85%E9%9B%86%E3%80%82%20%E5%AE%83%E5%8F%AF%E4%BB%A5%E7%BC%96%E8%AF%91%E6%88%90%E6%99%AE%E9%80%9A%E7%9A%84JavaScript%E4%BB%A3%E7%A0%81%E3%80%82%20TypeScript%E6%94%AF%E6%8C%81%E4%BB%BB%E6%84%8F%E6%B5%8F%E8%A7%88%E5%99%A8%EF%BC%8C%E4%BB%BB%E6%84%8F%E7%8E%AF%E5%A2%83%EF%BC%8C%E4%BB%BB%E6%84%8F%E7%B3%BB%E7%BB%9F%E5%B9%B6%E4%B8%94%E6%98%AF%E5%BC%80%E6%BA%90%E7%9A%84%E3%80%82))。下面从基础概念到进阶用法，对 TypeScript 的核心知识点进行系统整理。

## 1. TypeScript 基础概念

### 类型系统与基本类型

TypeScript 引入了静态类型系统，为变量、函数等提供明确的类型标注（Type Annotation）。通过类型检查，很多常见错误能在编译阶段被发现，而非等到运行时。TypeScript 支持与 JavaScript **几乎相同的基础数据类型**，例如字符串（`string`）、数字（`number`）、布尔值（`boolean`）等，同时还提供了实用的**枚举类型**等扩展 ([基础类型 · TypeScript中文网 · TypeScript——JavaScript的超集](http://www.tslang.cn/docs/handbook/basic-types.html#:~:text=TypeScript%E6%94%AF%E6%8C%81%E4%B8%8EJavaScript%E5%87%A0%E4%B9%8E%E7%9B%B8%E5%90%8C%E7%9A%84%E6%95%B0%E6%8D%AE%E7%B1%BB%E5%9E%8B%EF%BC%8C%E6%AD%A4%E5%A4%96%E8%BF%98%E6%8F%90%E4%BE%9B%E4%BA%86%E5%AE%9E%E7%94%A8%E7%9A%84%E6%9E%9A%E4%B8%BE%E7%B1%BB%E5%9E%8B%E6%96%B9%E4%BE%BF%E6%88%91%E4%BB%AC%E4%BD%BF%E7%94%A8%E3%80%82))。常见的基本类型包括：

- **原始类型**：`string`（字符串），`number`（数字），`boolean`（布尔值），`symbol`（符号），`bigint`（大整数），以及表示空值的`null`和`undefined`等。这些与 JavaScript 中的原始类型对应。
- **数组类型**：如`number[]`表示数字数组，`string[]`表示字符串数组。也可用泛型表示法`Array<T>`定义数组类型 ([基础类型 · TypeScript中文网 · TypeScript——JavaScript的超集](http://www.tslang.cn/docs/handbook/basic-types.html#:~:text=TypeScript%E5%83%8FJavaScript%E4%B8%80%E6%A0%B7%E5%8F%AF%E4%BB%A5%E6%93%8D%E4%BD%9C%E6%95%B0%E7%BB%84%E5%85%83%E7%B4%A0%E3%80%82%20%E6%9C%89%E4%B8%A4%E7%A7%8D%E6%96%B9%E5%BC%8F%E5%8F%AF%E4%BB%A5%E5%AE%9A%E4%B9%89%E6%95%B0%E7%BB%84%E3%80%82%20%E7%AC%AC%E4%B8%80%E7%A7%8D%EF%BC%8C%E5%8F%AF%E4%BB%A5%E5%9C%A8%E5%85%83%E7%B4%A0%E7%B1%BB%E5%9E%8B%E5%90%8E%E9%9D%A2%E6%8E%A5%E4%B8%8A%20%60))。
- **元组（Tuple）**：表示元素数量和类型都固定的数组，例如`[string, number]`表示一个包含字符串和数字的元组 ([基础类型 · TypeScript中文网 · TypeScript——JavaScript的超集](http://www.tslang.cn/docs/handbook/basic-types.html#:~:text=%E5%85%83%E7%BB%84%20Tuple))。
- **枚举（enum）**：用于定义一组命名常量的类型。比如：`enum Color { Red, Green, Blue }`定义了一个颜色枚举类型，`Color.Red`等于0，`Color.Green`等于1（默认从0开始递增） ([基础类型 · TypeScript中文网 · TypeScript——JavaScript的超集](http://www.tslang.cn/docs/handbook/basic-types.html#:~:text=%E4%B8%BA%E4%BA%86%E8%AE%A9%E7%A8%8B%E5%BA%8F%E6%9C%89%E4%BB%B7%E5%80%BC%EF%BC%8C%E6%88%91%E4%BB%AC%E9%9C%80%E8%A6%81%E8%83%BD%E5%A4%9F%E5%A4%84%E7%90%86%E6%9C%80%E7%AE%80%E5%8D%95%E7%9A%84%E6%95%B0%E6%8D%AE%E5%8D%95%E5%85%83%EF%BC%9A%E6%95%B0%E5%AD%97%EF%BC%8C%E5%AD%97%E7%AC%A6%E4%B8%B2%EF%BC%8C%E7%BB%93%E6%9E%84%E4%BD%93%EF%BC%8C%E5%B8%83%E5%B0%94%E5%80%BC%E7%AD%89%E3%80%82%20TypeScript%E6%94%AF%E6%8C%81%E4%B8%8EJavaScript%E5%87%A0%E4%B9%8E%E7%9B%B8%E5%90%8C%E7%9A%84%E6%95%B0%E6%8D%AE%E7%B1%BB%E5%9E%8B%EF%BC%8C%E6%AD%A4%E5%A4%96%E8%BF%98%E6%8F%90%E4%BE%9B%E4%BA%86%E5%AE%9E%E7%94%A8%E7%9A%84%E6%9E%9A%E4%B8%BE%E7%B1%BB%E5%9E%8B%E6%96%B9%E4%BE%BF%E6%88%91%E4%BB%AC%E4%BD%BF%E7%94%A8%E3%80%82))。
- **对象类型**：用于描述普通的对象结构（键值对集合）。可以直接用字面量类型注解，如`{ x: number; y: number }`，也可以使用接口或类型别名（详见下文）。

此外，TypeScript 还引入了一些特殊类型：

- **`any`**：任意类型，表示关闭类型检查。这在类型不确定或需要渐进迁移时很有用，但也**最不安全**。被标记为`any`的值可以绕过编译器的类型检查（可赋值并调用任意属性），相当于对类型系统的退避 ([基础类型 · TypeScript中文网 · TypeScript——JavaScript的超集](http://www.tslang.cn/docs/handbook/basic-types.html#:~:text=%E6%9C%89%E6%97%B6%E5%80%99%EF%BC%8C%E6%88%91%E4%BB%AC%E4%BC%9A%E6%83%B3%E8%A6%81%E4%B8%BA%E9%82%A3%E4%BA%9B%E5%9C%A8%E7%BC%96%E7%A8%8B%E9%98%B6%E6%AE%B5%E8%BF%98%E4%B8%8D%E6%B8%85%E6%A5%9A%E7%B1%BB%E5%9E%8B%E7%9A%84%E5%8F%98%E9%87%8F%E6%8C%87%E5%AE%9A%E4%B8%80%E4%B8%AA%E7%B1%BB%E5%9E%8B%E3%80%82%20%E8%BF%99%E4%BA%9B%E5%80%BC%E5%8F%AF%E8%83%BD%E6%9D%A5%E8%87%AA%E4%BA%8E%E5%8A%A8%E6%80%81%E7%9A%84%E5%86%85%E5%AE%B9%EF%BC%8C%E6%AF%94%E5%A6%82%E6%9D%A5%E8%87%AA%E7%94%A8%E6%88%B7%E8%BE%93%E5%85%A5%E6%88%96%E7%AC%AC%E4%B8%89%E6%96%B9%E4%BB%A3%E7%A0%81%E5%BA%93%E3%80%82%20%E8%BF%99%E7%A7%8D%E6%83%85%E5%86%B5%E4%B8%8B%EF%BC%8C%E6%88%91%E4%BB%AC%E4%B8%8D%E5%B8%8C%E6%9C%9B%E7%B1%BB%E5%9E%8B%E6%A3%80%E6%9F%A5%E5%99%A8%E5%AF%B9%E8%BF%99%E4%BA%9B%E5%80%BC%E8%BF%9B%E8%A1%8C%E6%A3%80%E6%9F%A5%E8%80%8C%E6%98%AF%E7%9B%B4%E6%8E%A5%E8%AE%A9%E5%AE%83%E4%BB%AC%E9%80%9A%E8%BF%87%E7%BC%96%E8%AF%91%E9%98%B6%E6%AE%B5%E7%9A%84%E6%A3%80%E6%9F%A5%E3%80%82%20%E9%82%A3%E4%B9%88%E6%88%91%E4%BB%AC%E5%8F%AF%E4%BB%A5%E4%BD%BF%E7%94%A8%20,%E7%B1%BB%E5%9E%8B%E6%9D%A5%E6%A0%87%E8%AE%B0%E8%BF%99%E4%BA%9B%E5%8F%98%E9%87%8F%EF%BC%9A))。应谨慎使用`any`，避免其在代码中蔓延。
- **`unknown`**：未知类型，是`any`的安全版本。任何类型的值都可以赋给`unknown`类型的变量，但从`unknown`取值时必须先进行类型缩小或断言，否则无法直接使用其属性或方法 ([[TypeScript] 使用 unknown 类型代替 any 类型 - Meowu's Web Blog](https://fullstackbb.com/typescript/typescript-unknown-as-top-type/#:~:text=%E6%89%80%E4%BB%A5%E4%BB%8E%20,%E7%B1%BB%E5%9E%8B%E3%80%82))。换言之，`unknown`要求开发者显式检查类型，确保安全后再使用，未检查就使用会导致编译错误。
- **`void`**：空类型，通常用于标注**无返回值**的函数（例如函数仅执行操作不返回任何值时返回类型为`void`）。声明`void`类型的变量只可赋值为`undefined`或`null`（在非严格模式下） ([基础类型 · TypeScript中文网 · TypeScript——JavaScript的超集](http://www.tslang.cn/docs/handbook/basic-types.html#:~:text=match%20at%20L292%20%E6%9F%90%E7%A7%8D%E7%A8%8B%E5%BA%A6%E4%B8%8A%E6%9D%A5%E8%AF%B4%EF%BC%8C,%EF%BC%9A))。
- **`never`**：表示**永不存在值**的类型，用于不会正常结束的函数（例如抛出异常或死循环）或无法达到的代码分支。`never`是所有类型的子类型（可以赋给任何类型），但没有任何类型是它的子类型（除了`never`本身），即使是`any`也不能赋值给`never` ([基础类型 · TypeScript中文网 · TypeScript——JavaScript的超集](http://www.tslang.cn/docs/handbook/basic-types.html#:~:text=))。

### 类型注解与类型推断

TypeScript 中，可以通过**类型注解**明确指定变量、参数和返回值的类型。例如：

```ts
let message: string = "Hello, TypeScript";
function add(x: number, y: number): number {
  return x + y;
}
```

上述代码中，变量`message`被注解为字符串类型，函数`add`的参数和返回值类型也分别注解为`number`。类型注解让编译器能够据此进行类型检查，保证赋值和操作符合预期类型。如果赋予不匹配的值，编译器会报错。例如：

```ts
let msg = "hello";
msg = 123;  // ❌错误: 不能将number赋给string类型
```

即使不写类型注解，**类型推断**机制也会根据初始值推断出变量类型 ([tsconfig.json · TypeScript中文网 · TypeScript——JavaScript的超集](http://www.tslang.cn/docs/handbook/tsconfig-json.html#:~:text=%E5%A6%82%E6%9E%9C%E4%B8%80%E4%B8%AA%E7%9B%AE%E5%BD%95%E4%B8%8B%E5%AD%98%E5%9C%A8%E4%B8%80%E4%B8%AA%20,%E4%B8%80%E4%B8%AA%E9%A1%B9%E7%9B%AE%E5%8F%AF%E4%BB%A5%E9%80%9A%E8%BF%87%E4%BB%A5%E4%B8%8B%E6%96%B9%E5%BC%8F%E4%B9%8B%E4%B8%80%E6%9D%A5%E7%BC%96%E8%AF%91%EF%BC%9A))。上例中变量`msg`初始为字符串，因此推断类型为`string`，后续再赋数字就会被禁止。同理，函数如果没有显式标注返回类型，TypeScript 会根据`return`语句自动推断返回值类型。借助类型推断，很多情况下可以**省略类型标注**而仍享受静态检查的好处。

TypeScript 的类型系统采用**结构化类型**（结构类型系统）原则：只要两个类型的结构兼容，不要求显式声明继承关系也能互相赋值 ([类 · TypeScript中文网 · TypeScript——JavaScript的超集](http://www.tslang.cn/docs/handbook/classes.html#:~:text=TypeScript%E4%BD%BF%E7%94%A8%E7%9A%84%E6%98%AF%E7%BB%93%E6%9E%84%E6%80%A7%E7%B1%BB%E5%9E%8B%E7%B3%BB%E7%BB%9F%E3%80%82%20%E5%BD%93%E6%88%91%E4%BB%AC%E6%AF%94%E8%BE%83%E4%B8%A4%E7%A7%8D%E4%B8%8D%E5%90%8C%E7%9A%84%E7%B1%BB%E5%9E%8B%E6%97%B6%EF%BC%8C%E5%B9%B6%E4%B8%8D%E5%9C%A8%E4%B9%8E%E5%AE%83%E4%BB%AC%E4%BB%8E%E4%BD%95%E5%A4%84%E8%80%8C%E6%9D%A5%EF%BC%8C%E5%A6%82%E6%9E%9C%E6%89%80%E6%9C%89%E6%88%90%E5%91%98%E7%9A%84%E7%B1%BB%E5%9E%8B%E9%83%BD%E6%98%AF%E5%85%BC%E5%AE%B9%E7%9A%84%EF%BC%8C%E6%88%91%E4%BB%AC%E5%B0%B1%E8%AE%A4%E4%B8%BA%E5%AE%83%E4%BB%AC%E7%9A%84%E7%B1%BB%E5%9E%8B%E6%98%AF%E5%85%BC%E5%AE%B9%E7%9A%84%E3%80%82))。例如：

```ts
interface Person { name: string; }
class User { 
  name: string; 
  age: number;
  constructor(name: string, age: number) { this.name = name; this.age = age; }
}
let p: Person;
p = new User("Alice", 30);  // 可以，将 User 实例赋给 Person 接口
```

尽管 `User` 类并未明确实现 `Person` 接口，但只要对象包含所需的 `name` 属性且类型匹配，就被视作兼容。这种**“鸭子类型”**（按结构匹配而非按声明匹配）使得 TypeScript 更加灵活 ([接口 · TypeScript中文网 · TypeScript——JavaScript的超集](http://www.tslang.cn/docs/handbook/interfaces.html#:~:text=,%E7%9A%84%E5%AF%B9%E8%B1%A1%E5%AE%9E%E7%8E%B0%E4%BA%86%E8%BF%99%E4%B8%AA%E6%8E%A5%E5%8F%A3%E3%80%82%E6%88%91%E4%BB%AC%E5%8F%AA%E4%BC%9A%E5%8E%BB%E5%85%B3%E6%B3%A8%E5%80%BC%E7%9A%84%E5%A4%96%E5%BD%A2%E3%80%82%20%E5%8F%AA%E8%A6%81%E4%BC%A0%E5%85%A5%E7%9A%84%E5%AF%B9%E8%B1%A1%E6%BB%A1%E8%B6%B3%E4%B8%8A%E9%9D%A2%E6%8F%90%E5%88%B0%E7%9A%84%E5%BF%85%E8%A6%81%E6%9D%A1%E4%BB%B6%EF%BC%8C%E9%82%A3%E4%B9%88%E5%AE%83%E5%B0%B1%E6%98%AF%E8%A2%AB%E5%85%81%E8%AE%B8%E7%9A%84%E3%80%82))。

## 2. 类型进阶

基础类型之上，TypeScript 提供了更丰富的**组合类型**和类型工具来表达复杂的类型关系。

### 联合类型与交叉类型

**联合类型（Union Types）**表示一个值可以是几种类型之一，用管道符`|`分隔备选类型。例如，`string | number`类型表示值可以是字符串或数字。 ([高级类型 · TypeScript中文网 · TypeScript——JavaScript的超集](http://www.tslang.cn/docs/handbook/advanced-types.html#:~:text=%E8%81%94%E5%90%88%E7%B1%BB%E5%9E%8B%E8%A1%A8%E7%A4%BA%E4%B8%80%E4%B8%AA%E5%80%BC%E5%8F%AF%E4%BB%A5%E6%98%AF%E5%87%A0%E7%A7%8D%E7%B1%BB%E5%9E%8B%E4%B9%8B%E4%B8%80%E3%80%82%20%E6%88%91%E4%BB%AC%E7%94%A8%E7%AB%96%E7%BA%BF%EF%BC%88%20%60,%E3%80%82))定义：联合类型用竖线分隔每个类型，表示值可以为其中任意一种。使用联合类型时，只能访问**所有候选类型的公共属性**，以保证安全。例如:

```ts
function printId(id: string | number) {
  if (typeof id === "string") {
    // 在这个分支里，id 被缩小为 string 类型
    console.log(id.toUpperCase());
  } else {
    // 在这个分支里，id 被缩小为 number 类型
    console.log(id.toFixed(2));
  }
}
```

在上面代码中，通过 `typeof` 类型守卫（详见下节）缩小了联合类型，使我们能够针对不同类型执行不同操作。如果不进行类型缩小，直接对联合类型变量调用只有某一部分类型才有的方法，编译器会报错。 ([高级类型 · TypeScript中文网 · TypeScript——JavaScript的超集](http://www.tslang.cn/docs/handbook/advanced-types.html#:~:text=%E8%BF%99%E9%87%8C%E7%9A%84%E8%81%94%E5%90%88%E7%B1%BB%E5%9E%8B%E5%8F%AF%E8%83%BD%E6%9C%89%E7%82%B9%E5%A4%8D%E6%9D%82%EF%BC%8C%E4%BD%86%E6%98%AF%E4%BD%A0%E5%BE%88%E5%AE%B9%E6%98%93%E5%B0%B1%E4%B9%A0%E6%83%AF%E4%BA%86%E3%80%82%20%E5%A6%82%E6%9E%9C%E4%B8%80%E4%B8%AA%E5%80%BC%E7%9A%84%E7%B1%BB%E5%9E%8B%E6%98%AF%20%60A%20,%E5%B0%B1%E5%87%BA%E9%94%99%E4%BA%86%E3%80%82))

与联合类型相反，**交叉类型（Intersection Types）**使用`&`将多个类型叠加，表示一个值同时满足所有类型要求。交叉类型常用于将多种属性合并为一种类型，例如 `TypeA & TypeB` 包含了 `TypeA` 和 `TypeB` 的所有属性。交叉类型可以用来实现 mixin 模式或扩展现有类型，但要注意若类型有重名属性其类型需兼容，否则交叉会得不到任何值类型（`never`）。

### 类型别名 (Type Alias) 与接口 (Interface)

**类型别名**使用`type`关键字为一种类型起一个新名字。类型别名可用于原始类型、联合类型、元组甚至交叉类型等任意类型 ([高级类型 · TypeScript中文网 · TypeScript——JavaScript的超集](http://www.tslang.cn/docs/handbook/advanced-types.html#:~:text=%E7%B1%BB%E5%9E%8B%E5%88%AB%E5%90%8D%E4%BC%9A%E7%BB%99%E4%B8%80%E4%B8%AA%E7%B1%BB%E5%9E%8B%E8%B5%B7%E4%B8%AA%E6%96%B0%E5%90%8D%E5%AD%97%E3%80%82%20%E7%B1%BB%E5%9E%8B%E5%88%AB%E5%90%8D%E6%9C%89%E6%97%B6%E5%92%8C%E6%8E%A5%E5%8F%A3%E5%BE%88%E5%83%8F%EF%BC%8C%E4%BD%86%E6%98%AF%E5%8F%AF%E4%BB%A5%E4%BD%9C%E7%94%A8%E4%BA%8E%E5%8E%9F%E5%A7%8B%E5%80%BC%EF%BC%8C%E8%81%94%E5%90%88%E7%B1%BB%E5%9E%8B%EF%BC%8C%E5%85%83%E7%BB%84%E4%BB%A5%E5%8F%8A%E5%85%B6%E5%AE%83%E4%BB%BB%E4%BD%95%E4%BD%A0%E9%9C%80%E8%A6%81%E6%89%8B%E5%86%99%E7%9A%84%E7%B1%BB%E5%9E%8B%E3%80%82))。例如：

```ts
type Point = { x: number; y: number };      // 别名定义对象类型
type ID = number | string;                 // 别名定义联合类型
type Callback = (data: string) => void;    // 别名定义函数类型
```

以上定义了 `Point` 对象类型，`ID` 联合类型，以及 `Callback` 函数类型的别名。**类型别名**主要用于简化复杂类型的书写，以及为类型赋予语义化的名称，方便理解。

**接口（Interface）**则专门用于描述**对象的结构**。使用`interface`关键字可定义对象应该有哪些属性和方法。例如：

```ts
interface Person {
  name: string;
  age: number;
  speak(): void;
}
```

接口描述了一组属性的**形状**，实现该接口的对象需要具有这些属性。TypeScript 接口在本质上是**结构类型**：并不要求一个对象显式声明“实现”了接口，只要该对象满足接口所要求的结构，就被认为实现了接口 ([接口 · TypeScript中文网 · TypeScript——JavaScript的超集](http://www.tslang.cn/docs/handbook/interfaces.html#:~:text=,%E7%9A%84%E5%AF%B9%E8%B1%A1%E5%AE%9E%E7%8E%B0%E4%BA%86%E8%BF%99%E4%B8%AA%E6%8E%A5%E5%8F%A3%E3%80%82%E6%88%91%E4%BB%AC%E5%8F%AA%E4%BC%9A%E5%8E%BB%E5%85%B3%E6%B3%A8%E5%80%BC%E7%9A%84%E5%A4%96%E5%BD%A2%E3%80%82%20%E5%8F%AA%E8%A6%81%E4%BC%A0%E5%85%A5%E7%9A%84%E5%AF%B9%E8%B1%A1%E6%BB%A1%E8%B6%B3%E4%B8%8A%E9%9D%A2%E6%8F%90%E5%88%B0%E7%9A%84%E5%BF%85%E8%A6%81%E6%9D%A1%E4%BB%B6%EF%BC%8C%E9%82%A3%E4%B9%88%E5%AE%83%E5%B0%B1%E6%98%AF%E8%A2%AB%E5%85%81%E8%AE%B8%E7%9A%84%E3%80%82))。比如：

```ts
function greet(person: Person) {
  console.log(`Hello, ${person.name}`);
}
let user = { name: "Bob", age: 25, speak() { console.log("Hi") } };
greet(user);  // OK，user具有Person接口所需的属性
```

即使对象 `user` 有额外的属性 `speak`，但只要至少包含了 `name` 和 `age` 并类型正确，就可以作为 `Person` 使用。这体现了接口的鸭子类型特性。

接口还支持**可选属性**和**只读属性**等特性：在属性名后加`?`号表示可选，例如`age?: number`表示对象可以有也可以没有`age`属性；在属性名前加`readonly`表示只能在初始化时赋值，之后不可修改。

*接口 vs 类型别名*：大多数情况下接口和类型别名都能定义对象结构，可以互相替代。但接口支持**声明合并**（多次定义同名接口会自动合并其成员）和`extends`继承，这对为已有类型扩展属性很有用；类型别名则可以直接表示联合类型等接口无法表示的形式。因此具体选择视需求而定。

### 类型断言 (Type Assertion)

有时我们比编译器更清楚某个值的实际类型，此时可以使用**类型断言**告诉编译器“相信我，这个值就是这种类型”。类型断言在语法上有两种形式：尖括号语法和 `as` 语法。例如：

```ts
let someValue: any = "this is a string";
let strLength: number = (<string>someValue).length;      // 尖括号语法
let strLength2: number = (someValue as string).length;   // as语法
```

以上代码中，我们将 `someValue`（类型为`any`）断言为`string`，从而能访问字符串的 `length` 属性。**类型断言并不会影响运行时**，仅在编译阶段起作用，它不会做特殊的类型检查或解构操作 ([基础类型 · TypeScript中文网 · TypeScript——JavaScript的超集](http://www.tslang.cn/docs/handbook/basic-types.html#:~:text=match%20at%20L368%20%E9%80%9A%E8%BF%87%20%E7%B1%BB%E5%9E%8B%E6%96%AD%E8%A8%80,%E8%BF%99%E7%A7%8D%E6%96%B9%E5%BC%8F%E5%8F%AF%E4%BB%A5%E5%91%8A%E8%AF%89%E7%BC%96%E8%AF%91%E5%99%A8%EF%BC%8C%E2%80%9C%E7%9B%B8%E4%BF%A1%E6%88%91%EF%BC%8C%E6%88%91%E7%9F%A5%E9%81%93%E8%87%AA%E5%B7%B1%E5%9C%A8%E5%B9%B2%E4%BB%80%E4%B9%88%E2%80%9D%E3%80%82%20%E7%B1%BB%E5%9E%8B%E6%96%AD%E8%A8%80%E5%A5%BD%E6%AF%94%E5%85%B6%E5%AE%83%E8%AF%AD%E8%A8%80%E9%87%8C%E7%9A%84%E7%B1%BB%E5%9E%8B%E8%BD%AC%E6%8D%A2%EF%BC%8C%E4%BD%86%E6%98%AF%E4%B8%8D%E8%BF%9B%E8%A1%8C%E7%89%B9%E6%AE%8A%E7%9A%84%E6%95%B0%E6%8D%AE%E6%A3%80%E6%9F%A5%E5%92%8C%E8%A7%A3%E6%9E%84%E3%80%82%20%E5%AE%83%E6%B2%A1%E6%9C%89%E8%BF%90%E8%A1%8C%E6%97%B6%E7%9A%84%E5%BD%B1%E5%93%8D%EF%BC%8C%E5%8F%AA%E6%98%AF%E5%9C%A8%E7%BC%96%E8%AF%91%E9%98%B6%E6%AE%B5%E8%B5%B7%E4%BD%9C%E7%94%A8%E3%80%82%20TypeScript%E4%BC%9A%E5%81%87%E8%AE%BE%E4%BD%A0%EF%BC%8C%E7%A8%8B%E5%BA%8F%E5%91%98%EF%BC%8C%E5%B7%B2%E7%BB%8F%E8%BF%9B%E8%A1%8C%E4%BA%86%E5%BF%85%E9%A1%BB%E7%9A%84%E6%A3%80%E6%9F%A5%E3%80%82))。这意味着程序员需要自行保证断言的正确性，否则可能在运行时产生错误。类型断言应在确有把握且需要绕过编译器推断时使用。  

> 注意：如果你在使用 JSX 的 .tsx 文件，只有 `as` 语法可用，避免与 JSX 语法冲突。

### 类型守卫 (Type Guard)

类型守卫用于在**运行时**细化（narrow）联合类型或 `any/unknown` 类型，从而在特定代码分支中获得更加确定的类型。常见的类型守卫包括：

- **`typeof` 守卫**：通过检查基本类型来缩小范围。例：`if (typeof x === "string") { ... }` 分支中，`x`被视为字符串类型。 ([高级类型 · TypeScript中文网 · TypeScript——JavaScript的超集](http://www.tslang.cn/docs/handbook/advanced-types.html#:~:text=match%20at%20L359%20%E8%BF%99%E4%BA%9B,%E3%80%82%20%E4%BD%86%E6%98%AFTypeScript%E5%B9%B6%E4%B8%8D%E4%BC%9A%E9%98%BB%E6%AD%A2%E4%BD%A0%E4%B8%8E%E5%85%B6%E5%AE%83%E5%AD%97%E7%AC%A6%E4%B8%B2%E6%AF%94%E8%BE%83%EF%BC%8C%E8%AF%AD%E8%A8%80%E4%B8%8D%E4%BC%9A%E6%8A%8A%E9%82%A3%E4%BA%9B%E8%A1%A8%E8%BE%BE%E5%BC%8F%E8%AF%86%E5%88%AB%E4%B8%BA%E7%B1%BB%E5%9E%8B%E4%BF%9D%E6%8A%A4%E3%80%82))
- **`instanceof` 守卫**：通过判断对象是否某构造函数的实例来缩小类型。例：`if (pet instanceof Fish) { pet.swim(); }` 分支中，`pet`被视为`Fish`类型。 ([高级类型 · TypeScript中文网 · TypeScript——JavaScript的超集](http://www.tslang.cn/docs/handbook/advanced-types.html#:~:text=))
- **属性检查**：利用`in`操作符检查属性存在与否，也可作为类型守卫。例：`if ("fly" in pet) { pet.fly(); }` 可以区分 `pet` 是否为会飞的类别。
- **自定义类型守卫**：使用返回类型谓词的函数来自定义守卫。例如：

  ```ts
  function isFish(pet: Fish | Bird): pet is Fish {
    return (pet as Fish).swim !== undefined;
  }
  // 使用:
  let pet: Fish | Bird = getPet();
  if (isFish(pet)) {
    pet.swim();  // pet在此处被缩小为Fish
  } else {
    pet.fly();   // pet在此处被缩小为Bird
  }
  ```

  `isFish` 函数的返回类型`pet is Fish`就是类型谓词，表示当返回真时输入参数`pet`应视为`Fish`类型 ([高级类型 · TypeScript中文网 · TypeScript——JavaScript的超集](http://www.tslang.cn/docs/handbook/advanced-types.html#:~:text=TypeScript%E9%87%8C%E7%9A%84%20%E7%B1%BB%E5%9E%8B%E4%BF%9D%E6%8A%A4%20%E6%9C%BA%E5%88%B6%E8%AE%A9%E5%AE%83%E6%88%90%E4%B8%BA%E4%BA%86%E7%8E%B0%E5%AE%9E%E3%80%82%20%E7%B1%BB%E5%9E%8B%E4%BF%9D%E6%8A%A4%E5%B0%B1%E6%98%AF%E4%B8%80%E4%BA%9B%E8%A1%A8%E8%BE%BE%E5%BC%8F%EF%BC%8C%E5%AE%83%E4%BB%AC%E4%BC%9A%E5%9C%A8%E8%BF%90%E8%A1%8C%E6%97%B6%E6%A3%80%E6%9F%A5%E4%BB%A5%E7%A1%AE%E4%BF%9D%E5%9C%A8%E6%9F%90%E4%B8%AA%E4%BD%9C%E7%94%A8%E5%9F%9F%E9%87%8C%E7%9A%84%E7%B1%BB%E5%9E%8B%E3%80%82%20%E8%A6%81%E5%AE%9A%E4%B9%89%E4%B8%80%E4%B8%AA%E7%B1%BB%E5%9E%8B%E4%BF%9D%E6%8A%A4%EF%BC%8C%E6%88%91%E4%BB%AC%E5%8F%AA%E8%A6%81%E7%AE%80%E5%8D%95%E5%9C%B0%E5%AE%9A%E4%B9%89%E4%B8%80%E4%B8%AA%E5%87%BD%E6%95%B0%EF%BC%8C%E5%AE%83%E7%9A%84%E8%BF%94%E5%9B%9E%E5%80%BC%E6%98%AF%E4%B8%80%E4%B8%AA,%E7%B1%BB%E5%9E%8B%E8%B0%93%E8%AF%8D%EF%BC%9A))。在调用处，TypeScript 据此自动完成类型缩小。

通过类型守卫，TypeScript 能够在**条件判断的不同分支**中推断出更加具体的类型（这一过程称作**类型缩小**/narrowing），让联合类型的使用更加安全和便利。

## 3. 函数与泛型

### 函数的类型

在 TypeScript 中，为函数声明参数和返回值类型能提升代码健壮性。函数参数类型和返回类型都可以在函数签名中指定：

```ts
function multiply(a: number, b: number): number {
  return a * b;
}
```

若函数没有返回任何值（过程函数），其返回类型应标注为`void`。参数也可以设置**默认值**或**可选**：带有默认值的参数会自动获得对应类型，可选参数则使用`?`标记。例如：

```ts
function greet(name: string, greeting: string = "Hello", age?: number): string {
  if (age !== undefined) {
    return `${greeting}, ${name}. You are ${age} years old.`;
  }
  return `${greeting}, ${name}.`;
}
```

上例中，`greeting` 有默认值 `"Hello"`，因此调用时可省略该参数；`age` 被标记为可选，调用时可以不传。TypeScript 会根据默认值推断 `greeting` 为 `string` 类型（即使未显式标注），并强制可选参数必须在必需参数后面。

**函数类型**本身也可以作为一种类型注解。例如可以用表达式`(param1: Type1, param2: Type2) => ReturnType`表示函数签名类型：

```ts
let compute: (x: number, y: number) => number;
compute = multiply;            // 可以，将实现匹配签名的函数赋给该函数类型变量
```

这里 `compute` 变量被声明为一个接受两个数字并返回数字的函数类型，因此可以将 `multiply` 赋给它。也可以使用接口定义函数类型，例如：

```ts
interface StringProcessor {
  (input: string, upperCase: boolean): string;
}
```

上述接口描述了一个函数签名——接受字符串和布尔值，返回字符串。任何符合这个签名的函数都可以赋给该接口类型的变量。

TypeScript 还支持**函数重载**(Overload)：为同一函数提供多个声明，以适应不同参数组合。但重载实现需要单一函数，根据运行时参数判断分支，稍复杂，这里不深入展开。

### 泛型（Generics）

**泛型**允许我们定义在多种类型上均适用的组件。通过在函数、类、接口等定义中引入**类型参数**，可以编写参数化的代码，增强复用性 ([泛型 · TypeScript中文网 · TypeScript——JavaScript的超集](http://www.tslang.cn/docs/handbook/generics.html#:~:text=%E5%9C%A8%E5%83%8FC))。泛型的一个典型例子是**泛型函数**：

```ts
function identity<T>(value: T): T {
  return value;
}
```

上述 `identity` 函数引入了类型参数 `<T>`，可以视作“占位符”类型。调用时可由传入的值推断出 `T` 的具体类型，也可手动指定。例如：

```ts
let output1 = identity<string>("TypeScript");  // 明确指定T为string
let output2 = identity(42);                   // 未指定T，编译器根据参数42推断T为number
// output1 的类型为 string，output2 的类型为 number
```

与使用 `any` 不同，泛型在保留类型信息的同时实现了通用化：传入什么类型，返回的还是对应的类型，不会丢失类型准确性 ([泛型 · TypeScript中文网 · TypeScript——JavaScript的超集](http://www.tslang.cn/docs/handbook/generics.html#:~:text=%E6%88%91%E4%BB%AC%E6%8A%8A%E8%BF%99%E4%B8%AA%E7%89%88%E6%9C%AC%E7%9A%84%20))。因此 `identity` 函数对于字符串返回字符串，对于数字则返回数字。

泛型不仅可用于函数，还可以用于**接口**和**类**。例如，TypeScript 内置的 `Array<T>` 就是一个泛型接口，表示元素类型为 `T` 的数组；再比如：

```ts
interface Pair<T, U> {
  first: T;
  second: U;
}
let p: Pair<string, number> = { first: "age", second: 30 };
```

上例中接口 `Pair<T, U>` 有两个类型参数，用于定义属性 `first` 和 `second` 的类型。使用时，需要为 T 和 U 指定具体类型（如 `string` 和 `number`）。

**泛型约束**：有时我们希望限制类型参数的取值范围，这可以通过 extends 关键字对类型参数设定**约束**。 ([泛型 · TypeScript中文网 · TypeScript——JavaScript的超集](http://www.tslang.cn/docs/handbook/generics.html#:~:text=%E4%B8%BA%E6%AD%A4%EF%BC%8C%E6%88%91%E4%BB%AC%E5%AE%9A%E4%B9%89%E4%B8%80%E4%B8%AA%E6%8E%A5%E5%8F%A3%E6%9D%A5%E6%8F%8F%E8%BF%B0%E7%BA%A6%E6%9D%9F%E6%9D%A1%E4%BB%B6%E3%80%82%20%E5%88%9B%E5%BB%BA%E4%B8%80%E4%B8%AA%E5%8C%85%E5%90%AB%20,%E5%85%B3%E9%94%AE%E5%AD%97%E6%9D%A5%E5%AE%9E%E7%8E%B0%E7%BA%A6%E6%9D%9F%EF%BC%9A))例如：

```ts
interface Lengthwise { length: number; }
function loggingIdentity<T extends Lengthwise>(arg: T): T {
  console.log(arg.length);  // T被约束为包含length属性的类型
  return arg;
}
```

这里类型参数 `T` 被约束为 extends 自接口 `Lengthwise`，因此只有那些带有 `length` 属性的类型才能用作 `loggingIdentity` 的类型参数。调用 `loggingIdentity("hello")` 是允许的（字符串有`length`），但如果传入不含 `length` 属性的对象则会编译错误。通过约束，泛型函数内部可以安全地假定 `arg.length` 存在，从而利用类型参数的特定属性或方法。

**泛型工具类型**：许多类型运算本身也可定义为泛型的形式。事实上，TypeScript 提供了一系列预定义的**泛型工具类型**（Utility Types），方便我们对已有类型进行变换，如后文将介绍的 `Partial<T>`、`Pick<T, K>` 等就是利用泛型定义的类型工具。

泛型的强大之处在于，它让组件**不仅适用于单一类型**，还能在保证类型安全的前提下适用于多种类型，提高了代码的灵活性和可重用性。

## 4. 类与面向对象编程

TypeScript 对**类（Class）**的支持基于 ES6 的 class 语法，并在此基础上添加了**类型注解**和一些关键字，以更好地支持面向对象编程。TypeScript 的类可以定义属性和方法、支持继承和实现接口等，并提供了访问修饰符来控制成员可见性。

### 类的定义与继承

使用 `class` 关键字可以定义类。例如：

```ts
class Animal {
  name: string;  // 定义属性并指定类型
  constructor(name: string) {
    this.name = name;
  }
  move(distance: number = 0) {
    console.log(`${this.name} moved ${distance}m.`);
  }
}
```

上例定义了一个 `Animal` 类，具有一个字符串属性`name`和一个方法`move`。构造函数`constructor`在创建实例时被调用，用传入的 `name` 初始化属性。TypeScript 要求类的每个实例属性在使用前都已被初始化（要么在声明时赋值，要么在构造函数中赋值）。

**继承（Inheritance）**使用`extends`关键字。比如定义 `Dog` 类继承自 `Animal`：

```ts
class Dog extends Animal {
  constructor(name: string) {
    super(name);        // 调用父类构造函数
  }
  bark() {
    console.log("Woof! Woof!");
  }
}
```

以上 `Dog` 类继承了 `Animal` 的属性和方法。`super(...)` 用于调用父类的构造函数初始化继承的部分。现在 `Dog` 实例既可以调用 `bark()` 也可以调用继承来的 `move()` 方法：

```ts
const dog = new Dog("Buddy");
dog.bark();            // 输出 "Woof! Woof!"
dog.move(10);          // 输出 "Buddy moved 10m."
```

### 修饰符：public、private、protected 与 readonly

TypeScript 类中，成员（属性和方法）默认都是**public（公有）** ([类 · TypeScript中文网 · TypeScript——JavaScript的超集](http://www.tslang.cn/docs/handbook/classes.html#:~:text=%E5%9C%A8%E4%B8%8A%E9%9D%A2%E7%9A%84%E4%BE%8B%E5%AD%90%E9%87%8C%EF%BC%8C%E6%88%91%E4%BB%AC%E5%8F%AF%E4%BB%A5%E8%87%AA%E7%94%B1%E7%9A%84%E8%AE%BF%E9%97%AE%E7%A8%8B%E5%BA%8F%E9%87%8C%E5%AE%9A%E4%B9%89%E7%9A%84%E6%88%90%E5%91%98%E3%80%82%20%E5%A6%82%E6%9E%9C%E4%BD%A0%E5%AF%B9%E5%85%B6%E5%AE%83%E8%AF%AD%E8%A8%80%E4%B8%AD%E7%9A%84%E7%B1%BB%E6%AF%94%E8%BE%83%E4%BA%86%E8%A7%A3%EF%BC%8C%E5%B0%B1%E4%BC%9A%E6%B3%A8%E6%84%8F%E5%88%B0%E6%88%91%E4%BB%AC%E5%9C%A8%E4%B9%8B%E5%89%8D%E7%9A%84%E4%BB%A3%E7%A0%81%E9%87%8C%E5%B9%B6%E6%B2%A1%E6%9C%89%E4%BD%BF%E7%94%A8%20%60public%20%60%E6%9D%A5%E5%81%9A%E4%BF%AE%E9%A5%B0%EF%BC%9B%E4%BE%8B%E5%A6%82%EF%BC%8CC,%E3%80%82))——在任何地方都可以访问。但可以通过修饰符来改变成员的可见性和可访问性：

- **public**：公有成员，默认修饰符。类的实例、子类以及类外部都能访问。
- **private**：私有成员，只能在**类内部**访问，实例和子类均不能访问 ([类 · TypeScript中文网 · TypeScript——JavaScript的超集](http://www.tslang.cn/docs/handbook/classes.html#:~:text=%E5%BD%93%E6%88%90%E5%91%98%E8%A2%AB%E6%A0%87%E8%AE%B0%E6%88%90%20))。试图在类外部访问私有成员会造成编译错误。例如上面的 `Animal` 类中如果将 `name` 声明为`private`，则在类外部 `new Animal(...).name` 将是非法的。
- **protected**：受保护成员，类似私有，但**对子类可见** ([类 · TypeScript中文网 · TypeScript——JavaScript的超集](http://www.tslang.cn/docs/handbook/classes.html#:~:text=%E7%90%86%E8%A7%A3%20)) ([类 · TypeScript中文网 · TypeScript——JavaScript的超集](http://www.tslang.cn/docs/handbook/classes.html#:~:text=%E6%B3%A8%E6%84%8F%EF%BC%8C%E6%88%91%E4%BB%AC%E4%B8%8D%E8%83%BD%E5%9C%A8%20,%E6%B4%BE%E7%94%9F%E8%80%8C%E6%9D%A5%E7%9A%84%E3%80%82))。即本类内部和继承的子类中可以访问，类的实例则不能访问。受保护成员常用于允许子类使用但不希望公开给外部的属性/方法。
- **readonly**：只读修饰符，表示属性只能在初始化时被赋值，一旦完成赋值便不可更改 ([类 · TypeScript中文网 · TypeScript——JavaScript的超集](http://www.tslang.cn/docs/handbook/classes.html#:~:text=readonly%E4%BF%AE%E9%A5%B0%E7%AC%A6))。`readonly` 可以与上述三个可见性修饰符同时使用（如 `public readonly`）。

示例：

```ts
class Person {
  public name: string;
  private secret: string;
  protected age: number;
  readonly id: number;
  
  constructor(name: string, age: number, id: number, secret: string) {
    this.name = name;
    this.age = age;
    this.id = id;
    this.secret = secret;
  }
}
class Employee extends Person {
  constructor(name: string, age: number, id: number, secret: string) {
    super(name, age, id, secret);
    console.log(this.age);    // ✅ 可以访问受保护的 age
    // console.log(this.secret); // ❌ 无法访问私有的 secret
  }
}
const p = new Person("Alice", 30, 1001, "secretCode");
console.log(p.name);    // ✅ 公有属性可访问
console.log(p.id);      // ✅ 只读属性可访问但不可修改
// p.age;  // ❌ 报错，受保护属性不能在类外访问
// p.secret; // ❌ 报错，私有属性不能在类外访问
```

上例中，`name` 为公有属性，`secret` 为私有属性仅 `Person` 内可见，`age` 为受保护属性对子类 `Employee` 可见，`id` 为只读属性（可读不可写）。访问修饰符可以帮助我们封装内部实现细节，只暴露必要的接口。

> **注意**：TypeScript 的 `private`/`protected` 是在编译时检查的。编译后的 JavaScript 并没有真正的私有作用域限制（ES2022 引入的 `#私有属性` 除外），因此这些修饰符更多是用于静态检查和代码可读性上的约定。

### 抽象类 (Abstract Class)

抽象类用于被其他类继承，作为公共基类，**不能直接实例化**。通过在类声明前加`abstract`定义抽象类 ([类 · TypeScript中文网 · TypeScript——JavaScript的超集](http://www.tslang.cn/docs/handbook/classes.html#:~:text=%E6%8A%BD%E8%B1%A1%E7%B1%BB))。抽象类中可以包含具体实现的成员，也可以包含没有实现的**抽象方法**。抽象方法只声明签名，不提供方法体，并且必须被非抽象的子类实现 ([类 · TypeScript中文网 · TypeScript——JavaScript的超集](http://www.tslang.cn/docs/handbook/classes.html#:~:text=%E6%8A%BD%E8%B1%A1%E7%B1%BB%E4%B8%AD%E7%9A%84%E6%8A%BD%E8%B1%A1%E6%96%B9%E6%B3%95%E4%B8%8D%E5%8C%85%E5%90%AB%E5%85%B7%E4%BD%93%E5%AE%9E%E7%8E%B0%E5%B9%B6%E4%B8%94%E5%BF%85%E9%A1%BB%E5%9C%A8%E6%B4%BE%E7%94%9F%E7%B1%BB%E4%B8%AD%E5%AE%9E%E7%8E%B0%E3%80%82%20%E6%8A%BD%E8%B1%A1%E6%96%B9%E6%B3%95%E7%9A%84%E8%AF%AD%E6%B3%95%E4%B8%8E%E6%8E%A5%E5%8F%A3%E6%96%B9%E6%B3%95%E7%9B%B8%E4%BC%BC%E3%80%82%20%E4%B8%A4%E8%80%85%E9%83%BD%E6%98%AF%E5%AE%9A%E4%B9%89%E6%96%B9%E6%B3%95%E7%AD%BE%E5%90%8D%E4%BD%86%E4%B8%8D%E5%8C%85%E5%90%AB%E6%96%B9%E6%B3%95%E4%BD%93%E3%80%82%20%E7%84%B6%E8%80%8C%EF%BC%8C%E6%8A%BD%E8%B1%A1%E6%96%B9%E6%B3%95%E5%BF%85%E9%A1%BB%E5%8C%85%E5%90%AB%20,%E5%85%B3%E9%94%AE%E5%AD%97%E5%B9%B6%E4%B8%94%E5%8F%AF%E4%BB%A5%E5%8C%85%E5%90%AB%E8%AE%BF%E9%97%AE%E4%BF%AE%E9%A5%B0%E7%AC%A6%E3%80%82))。例如：

```ts
abstract class Shape {
  abstract getArea(): number;             // 抽象方法，不提供实现
  printArea() {
    console.log(`Area: ${this.getArea()}`);
  }
}
class Circle extends Shape {
  radius: number;
  constructor(radius: number) { 
    super(); 
    this.radius = radius; 
  }
  getArea(): number {                    // 实现抽象方法
    return Math.PI * this.radius ** 2;
  }
}
const shape = new Circle(5);
shape.printArea();    // 输出圆的面积
// const bad = new Shape();  // ❌错误: 抽象类不能被实例化 ([类 · TypeScript中文网 · TypeScript——JavaScript的超集](http://www.tslang.cn/docs/handbook/classes.html#:~:text=let%20department%3A%20Department%3B%20%2F%2F%20%E5%85%81%E8%AE%B8%E5%88%9B%E5%BB%BA%E4%B8%80%E4%B8%AA%E5%AF%B9%E6%8A%BD%E8%B1%A1%E7%B1%BB%E5%9E%8B%E7%9A%84%E5%BC%95%E7%94%A8,printName))
```

`Shape` 是抽象类，定义了抽象方法 `getArea`，以及具体方法 `printArea`。子类 `Circle` 必须实现 `getArea` 方法才能完整定义。抽象类允许我们在基类中声明“接口契约”并提供部分实现，由子类完成具体细节。这样一来，使用抽象类引用（如 `Shape` 类型的变量）时，可以调用在抽象类中实现的方法（如 `printArea`），多态地执行不同子类的实现。

### 类实现接口 与 参数属性

类可以使用`implements`关键字来**实现接口**，确保类提供接口要求的属性和方法。这在需要某些类满足特定契约时很有用。例如：

```ts
interface Printable {
  print(): void;
}
class Article implements Printable {
  title: string;
  constructor(title: string) { this.title = title; }
  print() {
    console.log(this.title);
  }
}
```

`Article` 类声明实现 `Printable` 接口，因此必须提供一个 `print()` 方法，否则编译器会报错。通过接口，能保证不同类之间遵循统一的规范。

此外，TypeScript 提供了**参数属性**的简便写法：在构造函数参数前直接加修饰符（如 `public`、`private`、`readonly`），可以**同时**将参数声明为成员并赋值，省去在构造函数中逐一赋值的冗余。例如：

```ts
class Person {
  constructor(public name: string, private age: number) {
    // 编译后自动生成 this.name = name; this.age = age;
  }
}
```

上述写法直接在构造函数参数中定义了`name`（公有）和`age`（私有）成员并赋值，简洁明了。

## 5. 类型实用工具 (Utility Types)

TypeScript 内置了一些常用的**泛型工具类型**，用来基于现有类型生成新类型，在日常开发中非常实用 ([TypeScript 中文网: 文档 - 工具类型](https://ts.nodejs.cn/docs/handbook/utility-types.html#:~:text=)) ([TypeScript 中文网: 文档 - 工具类型](https://ts.nodejs.cn/docs/handbook/utility-types.html#:~:text=%60Record))。以下介绍几种常见的工具类型：

- **`Partial<T>`**：构造一个新类型，将类型 `T` 的所有属性设为可选（`?`） ([TypeScript 中文网: 文档 - 工具类型](https://ts.nodejs.cn/docs/handbook/utility-types.html#:~:text=%E6%9E%84%E9%80%A0%E4%B8%80%E4%B8%AA%E5%B0%86%20))。换言之，`Partial<T>` 描述了一个「可以只包含 T 的一部分属性」的类型。 ([TypeScript 中文网: 文档 - 工具类型](https://ts.nodejs.cn/docs/handbook/utility-types.html#:~:text=%E6%9E%84%E9%80%A0%E4%B8%80%E4%B8%AA%E5%B0%86%20))例如：

  ```ts
  interface Person { name: string; age: number; }
  type PartialPerson = Partial<Person>;
  // PartialPerson 等价于 { name?: string; age?: number }
  let p: PartialPerson = { name: "Alice" };  // 只提供部分属性也是合法的
  ```

- **`Required<T>`**：与 `Partial` 相反，构造一个新类型，将 `T` 的所有属性变为必需（去除可选标记） ([TypeScript 中文网: 文档 - 工具类型](https://ts.nodejs.cn/docs/handbook/utility-types.html#:~:text=))。若某属性原本就是可选，在 `Required<T>` 中会变为必须存在。

- **`Readonly<T>`**：构造一个新类型，将 `T` 的所有属性设为只读（`readonly`） ([TypeScript 中文网: 文档 - 工具类型](https://ts.nodejs.cn/docs/handbook/utility-types.html#:~:text=))。只读属性只能在初始化时赋值，此后无法修改。这通常用于不可变数据结构，例如将对象冻结后用 `Readonly<T>` 描述其类型。

- **`Record<Keys, Type>`**：构造一个对象类型，其属性键为 `Keys`，属性值类型为 `Type` ([TypeScript 中文网: 文档 - 工具类型](https://ts.nodejs.cn/docs/handbook/utility-types.html#:~:text=%E6%9E%84%E9%80%A0%E4%B8%80%E4%B8%AA%E5%AF%B9%E8%B1%A1%E7%B1%BB%E5%9E%8B%EF%BC%8C%E5%85%B6%E5%B1%9E%E6%80%A7%E9%94%AE%E4%B8%BA%20))。其中 `Keys` 通常是联合类型或字面量类型，表示一组属性名。例如：

  ```ts
  type Weekday = "Mon" | "Tue" | "Wed" | "Thu" | "Fri";
  type Schedule = Record<Weekday, string>;
  // 等价于 { Mon: string; Tue: string; ...; Fri: string }
  let plan: Schedule = {
    Mon: "Work", Tue: "Study", Wed: "Gym", Thu: "Work", Fri: "Party"
  };
  ```

- **`Pick<T, K>`**：从类型 `T` 挑选一组属性 `K`，构造一个新类型 ([TypeScript 中文网: 文档 - 工具类型](https://ts.nodejs.cn/docs/handbook/utility-types.html#:~:text=%E9%80%9A%E8%BF%87%E4%BB%8E%20))。`K` 可以是单个属性名或属性名的联合。`Pick` 会**保留**所选属性。例：

  ```ts
  interface Person { name: string; age: number; gender: string; }
  type PersonName = Pick<Person, "name">;
  // PersonName 等价于 { name: string }
  type PersonNameGender = Pick<Person, "name" | "gender">;
  // PersonNameGender 等价于 { name: string; gender: string }
  ```

- **`Omit<T, K>`**：与 `Pick` 相反，从类型 `T` 中**移除**指定的属性 `K`，构造新类型 ([TypeScript 中文网: 文档 - 工具类型](https://ts.nodejs.cn/docs/handbook/utility-types.html#:~:text=%E9%80%9A%E8%BF%87%E4%BB%8E%20,%E7%9B%B8%E5%8F%8D%E3%80%82))。即保留 `T` 中除 `K` 之外的所有属性 ([TypeScript 中文网: 文档 - 工具类型](https://ts.nodejs.cn/docs/handbook/utility-types.html#:~:text=%60Omit))。例：

  ```ts
  interface Person { name: string; age: number; gender: string; }
  type PersonNoAge = Omit<Person, "age">;
  // PersonNoAge 等价于 { name: string; gender: string }
  ```

  可以看出，`Omit<Person, "age">` 的效果相当于选取了 `name` 和 `gender`，所以`Omit<T, K>`实际上是对`Pick`的补充（`Omit<T, K>`等价于`Pick<T, Exclude<keyof T, K>>`）。

以上工具类型都是通过泛型和映射类型实现的，为常见的类型转换提供了便利。例如 `Partial` 常用于函数返回一个对象的更新值时，将未提供的字段标记为可选；`Pick`/`Omit` 常用于从大型接口中选择或排除部分属性用于其他场景；`Record` 则可用来快速定义键值映射的对象类型。

除了上述这些，TypeScript 还提供了诸如 `Required<T>`、`Readonly<T>`、`Exclude<UnionType, ExcludedMembers>`、`Extract<Type, Union>`、`NonNullable<Type>` 等更多实用工具类型，帮助我们在类型层面完成各种变换和计算 ([TS 里几个常用的内置工具类型（Record、Partial - CSDN博客](https://blog.csdn.net/qq_43869822/article/details/121664818#:~:text=TS%20%E9%87%8C%E5%87%A0%E4%B8%AA%E5%B8%B8%E7%94%A8%E7%9A%84%E5%86%85%E7%BD%AE%E5%B7%A5%E5%85%B7%E7%B1%BB%E5%9E%8B%EF%BC%88Record%E3%80%81Partial%20%E3%80%81%20Required%20%E3%80%81,%E3%80%81%20Extract%20%E3%80%81%20Omit%EF%BC%89%E7%9A%84%E4%BD%BF%E7%94%A8%20%E5%8E%9F%E5%88%9B)) ([TS 几个内置工具类型（Partial & Required & Readonly ... - 稀土掘金](https://juejin.cn/post/6905928813452984327#:~:text=TS%20%E5%87%A0%E4%B8%AA%E5%86%85%E7%BD%AE%E5%B7%A5%E5%85%B7%E7%B1%BB%E5%9E%8B%EF%BC%88Partial%20%26%20Required%20%26,%E4%BD%9C%E7%94%A8%EF%BC%9A%E7%94%9F%E6%88%90%E4%B8%80%E4%B8%AA%E6%96%B0%E7%B1%BB%E5%9E%8B%EF%BC%8C%E8%AF%A5%E7%B1%BB%E5%9E%8B%E4%B8%8ET%20%E6%8B%A5%E6%9C%89%E7%9B%B8%E5%90%8C%E7%9A%84%E5%B1%9E%E6%80%A7%EF%BC%8C%E4%BD%86%E6%98%AF%E6%89%80%E6%9C%89%E5%B1%9E%E6%80%A7%E7%9A%86%E4%B8%BA%E5%8F%AF%E9%80%89%E9%A1%B9))。它们都是全局可用的，充分利用这些工具类型可以大大提高复杂类型处理的灵活性和便利性。

## 6. 类型推断与类型兼容性

### 类型推断

前文提及，TypeScript 会在没有明确标注类型时尝试**推断类型**。这不仅适用于变量初始化和函数返回值，也适用于更复杂的情境：

- **最优通用类型**：当把多个不同但相关的类型放入同一数组字面量时，TypeScript 会推断出它们的**联合类型**或**更通用的父类型**作为数组元素类型。例如：`[new Error(), new Date()]` 会被推断为 `(Error | Date)[]`。
- **上下文类型**：TypeScript 还会利用**使用上下文**来推断。例如给一个函数类型的参数传入匿名函数时，会根据期望的函数签名自动推断出参数的类型：

  ```ts
  const names = ["Alice", "Bob", "Eve"];
  // forEach 回调期望 (value: string) => void
  names.forEach(value => {
    // 在此上下文中，value 被推断为 string
    console.log(value.toUpperCase());
  });
  ```

  无需显式声明，`value` 被推断为字符串，因为 `names` 是字符串数组，`forEach` 的回调参数据此推断为 `string`。

- **泛型推断**：调用泛型函数时，不传类型参数也可根据实参推断类型参数。例如前述的 `identity(42)` 调用，编译器从参数 `42` 推断出 `T` 为 `number`。再如 `Promise.resolve("test")` 会推断出返回的 Promise 类型是 `Promise<string>`。

类型推断让代码更简洁，但在复杂情况下也可能推断出比预期更宽泛的类型，此时可以通过**手动添加类型注解**或**类型断言**来引导编译器。

### 类型兼容性

TypeScript 的类型兼容性遵循**结构兼容**原则。这意味着判断两个类型是否兼容，不看它们的名字或继承关系，而是看其结构（成员）是否兼容。 ([类 · TypeScript中文网 · TypeScript——JavaScript的超集](http://www.tslang.cn/docs/handbook/classes.html#:~:text=TypeScript%E4%BD%BF%E7%94%A8%E7%9A%84%E6%98%AF%E7%BB%93%E6%9E%84%E6%80%A7%E7%B1%BB%E5%9E%8B%E7%B3%BB%E7%BB%9F%E3%80%82%20%E5%BD%93%E6%88%91%E4%BB%AC%E6%AF%94%E8%BE%83%E4%B8%A4%E7%A7%8D%E4%B8%8D%E5%90%8C%E7%9A%84%E7%B1%BB%E5%9E%8B%E6%97%B6%EF%BC%8C%E5%B9%B6%E4%B8%8D%E5%9C%A8%E4%B9%8E%E5%AE%83%E4%BB%AC%E4%BB%8E%E4%BD%95%E5%A4%84%E8%80%8C%E6%9D%A5%EF%BC%8C%E5%A6%82%E6%9E%9C%E6%89%80%E6%9C%89%E6%88%90%E5%91%98%E7%9A%84%E7%B1%BB%E5%9E%8B%E9%83%BD%E6%98%AF%E5%85%BC%E5%AE%B9%E7%9A%84%EF%BC%8C%E6%88%91%E4%BB%AC%E5%B0%B1%E8%AE%A4%E4%B8%BA%E5%AE%83%E4%BB%AC%E7%9A%84%E7%B1%BB%E5%9E%8B%E6%98%AF%E5%85%BC%E5%AE%B9%E7%9A%84%E3%80%82))例如：

```ts
interface Point { x: number; y: number; }
function logPoint(pt: Point) { console.log(`(${pt.x}, ${pt.y})`); }

let obj = { x: 10, y: 20, z: 30 };
logPoint(obj);  // OK，多余的 z 属性会被忽略，只要结构上至少具有 x 和 y 即可
```

`logPoint` 期望一个 `Point` 类型参数，但我们传入的对象多了个 `z` 属性。因为 TypeScript 按结构检查，`obj` 至少具有所需的 `x` 和 `y` 属性且类型匹配，所以额外的属性不影响赋值兼容性（通过变量传入时是允许的，直接字面量传入则会触发额外属性检查）。这种机制使得 TypeScript 的类型系统比一些传统面向对象语言更为弹性。

**类类型的兼容性**也是结构化的。两个类的实例只要拥有兼容的属性结构，就可以相互赋值，即使它们在继承关系上毫无关联。但当类中含有私有或受保护成员时，兼容性会受到限制：只有当来源和目标对象**是同一声明的类**实例时，私有/受保护成员才被认为兼容 ([类 · TypeScript中文网 · TypeScript——JavaScript的超集](http://www.tslang.cn/docs/handbook/classes.html#:~:text=TypeScript%E4%BD%BF%E7%94%A8%E7%9A%84%E6%98%AF%E7%BB%93%E6%9E%84%E6%80%A7%E7%B1%BB%E5%9E%8B%E7%B3%BB%E7%BB%9F%E3%80%82%20%E5%BD%93%E6%88%91%E4%BB%AC%E6%AF%94%E8%BE%83%E4%B8%A4%E7%A7%8D%E4%B8%8D%E5%90%8C%E7%9A%84%E7%B1%BB%E5%9E%8B%E6%97%B6%EF%BC%8C%E5%B9%B6%E4%B8%8D%E5%9C%A8%E4%B9%8E%E5%AE%83%E4%BB%AC%E4%BB%8E%E4%BD%95%E5%A4%84%E8%80%8C%E6%9D%A5%EF%BC%8C%E5%A6%82%E6%9E%9C%E6%89%80%E6%9C%89%E6%88%90%E5%91%98%E7%9A%84%E7%B1%BB%E5%9E%8B%E9%83%BD%E6%98%AF%E5%85%BC%E5%AE%B9%E7%9A%84%EF%BC%8C%E6%88%91%E4%BB%AC%E5%B0%B1%E8%AE%A4%E4%B8%BA%E5%AE%83%E4%BB%AC%E7%9A%84%E7%B1%BB%E5%9E%8B%E6%98%AF%E5%85%BC%E5%AE%B9%E7%9A%84%E3%80%82))。简单来说，带私有成员的实例只能赋值给**同一个类**或其子类的实例。

**函数类型兼容性**遵循“**参数**要**兼容**目标函数参数，**返回值**要**兼容**目标函数返回类型”的原则。需要注意的是，函数参数的比较是**双向协变**的（strictFunctionTypes 选项关闭时），一般而言允许目标函数的参数类型是源函数参数类型的**超集**（即源函数可以接受更少或更具体的参数），这样赋值后调用依然安全。但如果开启了严格函数类型检查（默认在 strict 模式下开启），则采取函数参数的**逆变**检查，更加严谨，防止潜在类型错误。

**`any` 与 `unknown`**在兼容性上有特殊规定：

- `any` 类型可以与任意类型互相兼容赋值（既能赋给别人也能被赋给任意类型），完全跳过类型检查。
- `unknown` 类型则更为严格：任何类型的值都能赋给 `unknown`（因为它可以是任何类型的一种），但 `unknown` 类型的值**只能**赋给 `unknown` 或 `any` ([[TypeScript] 使用 unknown 类型代替 any 类型 - Meowu's Web Blog](https://fullstackbb.com/typescript/typescript-unknown-as-top-type/#:~:text=%E6%89%80%E4%BB%A5%E4%BB%8E%20,%E7%B1%BB%E5%9E%8B%E3%80%82))。这保证了我们不会在未经检查时将 `unknown` 用在确定类型的位置。例如：

  ```ts
  let data: unknown = getValueFromAPI();
  let str: string = data;      // ❌错误，不能将unknown赋给string
  if (typeof data === "string") {
    str = data;                // ✅经过类型守卫，data可视为string
  }
  ```

  通过这种机制，`unknown` 强迫我们对其进行类型缩小后才能使用，从而提供了比 `any` 更安全的类型保护。

- **`never`** 类型属于所有类型的**子类型**：`never`值可以赋给任何类型变量（因为赋值情况永不会发生）；反过来，没有任何非`never`类型的值可以赋给`never`类型变量（除了抛异常或无限循环产生的`never`本身）。通常不需要手动使用`never`，它多出现于函数无法正常结束推断的返回类型或不可能的分支中，用于完整性检查。

总结而言，TypeScript 的类型兼容性整体上是**宽松的结构类型系统**，这带来了高度的灵活性。理解它的兼容规则有助于我们预测哪些赋值是允许的，哪些会报错，从而更好地利用类型系统进行抽象和代码重用。

## 7. 模块系统与声明文件

### 模块系统 (Modules)

TypeScript 支持与 ES6 相同的模块语法，通过 `import` 和 `export` 来组织代码。一个文件中凡是使用了顶级的 `import`或`export`语句，那么它被视为一个**模块**；没有使用的话则被视为**全局脚本**（其声明会合并到全局命名空间）。模块可以让我们将代码拆分到不同文件，并控制各部分的作用域。

**导出 (export)**：可以使用 `export` 导出变量、函数、类、类型、接口等，以便其它模块导入使用。例如：

```ts
// utils.ts
export function add(a: number, b: number): number {
  return a + b;
}
export const VERSION: string = "1.0";
```

这里 `utils.ts` 模块导出了函数 `add` 和常量 `VERSION`。还可以使用 `export default` 导出默认值，一个模块只能有一个默认导出：

```ts
// logger.ts
export default function log(message: string) {
  console.log("[LOG]", message);
}
```

**导入 (import)**：在另一个文件中使用导出内容，需要通过 `import` 引入。例如：

```ts
// main.ts
import { add, VERSION } from "./utils";
import log from "./logger";

console.log("Version:", VERSION);
log(`1 + 2 = ${add(1, 2)}`);
```

上述 `main.ts` 分别用了命名导入语法和默认导入语法，从相对路径的模块中引入了所需成员。

TypeScript 的模块在编译为 JavaScript 时，可以根据配置输出为多种模块格式（如 CommonJS、ESNext、AMD 等）。常见情况下：

- 在构建后端 Node.js 项目时，通常设置 `"module": "CommonJS"`，输出 CommonJS 模块（使用 `require` 导入导出）。
- 在构建前端项目或使用支持 ES 模块的运行时时，设置 `"module": "ESNext"` 或 `"ES2015"`，输出为 ES Module 格式的代码（使用 `import/export` 语法，需要打包工具或支持的环境来执行）。

**模块解析**：TypeScript 默认采用类似 Node.js 的解析策略加载模块。对于相对路径模块，按照给定路径查找 `.ts`、`.tsx`、`.d.ts`、`.js` 等对应文件；对于非相对的模块导入（如导入第三方库），则在 `node_modules` 目录中寻找该包的类型声明文件或实现。可以通过 `tsconfig.json` 的 `"baseUrl"` 和 `"paths"` 配置来调整模块解析根路径或重定向模块路径。

**命名空间 vs 模块**：历史上，TypeScript 还提供过基于 `namespace` 关键字的内部模块机制（有时称作“命名空间”）。命名空间可以把一组相关对象包裹在一个全局名称下，避免命名冲突。然而在 ES6 模块出现并被广泛采用后，**官方更推荐使用模块**来组织代码，而命名空间主要用于封装全局脚本的场景。简单来说，如果在使用模块化的构建系统，那么请使用 `import/export`；只有在不便采用模块的环境下（比如直接用 `<script>` 引用多个文件）才考虑使用命名空间。

### 第三方声明文件 (Declaration Files)

在使用第三方库时，为了让 TypeScript 获得该库的类型信息，需要**声明文件**（以 `.d.ts` 为后缀的文件）。声明文件为 JavaScript 库提供静态类型描述，相当于告诉 TypeScript “这个库的API有哪些，以及它们的类型签名”。

**获取声明文件的方式**：

1. **官方内置**：一些主流库自带 TypeScript 支持，在其 npm 包中已经包含了 `.d.ts` 文件。安装这些库后，TypeScript 编译器会自动读取库自带的类型声明。
2. **DefinitelyTyped 社区提供 (@types)**：很多纯 JavaScript 库没有内置声明，但社区在 [DefinitelyTyped](https://github.com/DefinitelyTyped/DefinitelyTyped) 项目中为其编写了声明文件。可以通过 npm 安装这些社区维护的声明包，名称格式一般为`@types/库名` ([声明文件 - TypeScript 入门教程](https://ts.xcatliu.com/basics/declaration-files#:~:text=,dev.%20%E5%8F%AF%E4%BB%A5%E5%9C%A8))。例如 jQuery 的声明文件包是 `@types/jquery`。安装方式:

   ```bash
   npm install --save-dev @types/jquery
   ```

   安装后，TypeScript 会自动包含 `node_modules/@types` 下的声明 ([声明文件 · TypeScript 入门教程](https://ts.xcatliu.com/basics/declaration-files#:~:text=%E6%88%91%E4%BB%AC%E5%8F%AF%E4%BB%A5%E7%9B%B4%E6%8E%A5%E4%B8%8B%E8%BD%BD%E4%B8%8B%E6%9D%A5%E4%BD%BF%E7%94%A8%EF%BC%8C%E4%BD%86%E6%98%AF%E6%9B%B4%E6%8E%A8%E8%8D%90%E7%9A%84%E6%98%AF%E4%BD%BF%E7%94%A8%20))。这样就无需手动引用，直接使用对应库的全局变量或导出模块即可获得类型提示 ([声明文件 · TypeScript 入门教程](https://ts.xcatliu.com/basics/declaration-files#:~:text=,%E4%B8%BE%E4%BE%8B%EF%BC%9A))。

3. **手动编写**：如果某库没有可用的声明文件，我们可以自己编写一个 `.d.ts` 文件。可以使用`declare module`为模块声明，也可以使用`declare function`/`declare class`/`declare var`等声明全局变量的类型。手动写声明文件需要仔细按照库的 API 定义类型，如果库接口复杂可能比较耗时。不过，这在类型系统层面为库提供了正确使用的文档，有助于开发。社区有丰富的[编写声明文件指南](https://www.typescriptlang.org/docs/handbook/declaration-files/introduction.html)可供参考。

例如，假设我们有一个全局脚本库向外暴露了全局变量`Library`，我们可以创建一个简易声明文件`library.d.ts`：

```ts
declare namespace Library {
  function doSomething(): void;
  const version: string;
}
```

将该 `.d.ts` 文件包含在项目中（确保 tsconfig 的编译范围包含它），那么在其他 TypeScript 文件中就可以安全地使用全局 `Library.doSomething()` 等，而不会有编译错误，并享受类型检查。

对于通过模块导入的库，可以使用 `declare module "库名"` 的语法编写模块的声明。在 Node.js 环境，还可以用 `declare global` 扩展全局变量声明等，复杂场景下建议查阅官方声明文件手册。

总之，声明文件为使用第三方库提供了类型保障。在实际项目中，**优先选择**已有的官方或社区提供的声明文件（通过 @types 获取）；在没有可用声明时，再考虑手动编写。在得到正确的声明文件支持后，TypeScript 就能像检查自有代码一样检查第三方库的调用，极大降低集成出错的风险。

## 8. 配置与工具链

### TypeScript 编译配置（tsconfig.json）

TypeScript 项目通常包含一个 **`tsconfig.json`** 文件，用于配置编译选项。这个文件位于项目根目录，表示该目录是一个 TypeScript 项目 ([tsconfig.json · TypeScript中文网 · TypeScript——JavaScript的超集](http://www.tslang.cn/docs/handbook/tsconfig-json.html#:~:text=%E5%A6%82%E6%9E%9C%E4%B8%80%E4%B8%AA%E7%9B%AE%E5%BD%95%E4%B8%8B%E5%AD%98%E5%9C%A8%E4%B8%80%E4%B8%AA%20,%E4%B8%80%E4%B8%AA%E9%A1%B9%E7%9B%AE%E5%8F%AF%E4%BB%A5%E9%80%9A%E8%BF%87%E4%BB%A5%E4%B8%8B%E6%96%B9%E5%BC%8F%E4%B9%8B%E4%B8%80%E6%9D%A5%E7%BC%96%E8%AF%91%EF%BC%9A))。`tsconfig.json` 指定了要编译的源码文件、所需的编译选项等信息。使用 `tsc --init` 可以在当前目录下生成一个基本的 tsconfig.json 模板。

一个典型的 `tsconfig.json` 内容例如：

```json
{
  "compilerOptions": {
    "target": "ES6",                   /* 将 TypeScript 编译输出为 ES2015 (ES6) 版本的 JavaScript */
    "module": "CommonJS",              /* 使用 CommonJS 模块规范（适用于 Node.js） */
    "strict": true,                    /* 开启所有严格类型检查选项 */
    "outDir": "./dist",                /* 将编译后的文件输出到 dist 目录 */
    "esModuleInterop": true,           /* 兼容处理 CommonJS 默认导出，与 ES Module 和谐共存 */
    "skipLibCheck": true               /* 跳过库声明文件的检查，以加快编译速度 */
  },
  "include": [ "src/**/*" ],           /* 指定要编译的 TS 源码文件目录模式 */
  "exclude": [ "node_modules", "dist" ]/* 排除不需要编译的目录 */
}
```

上面的配置做了如下事情：

- **target**：指定编译输出的 ECMAScript 版本。本例设置为 ES6（即 ES2015）。可选值如`ES5`、`ES2018`、`ES2020`等，默认为`ES3`（非常老的版本）。选择较新的 target 可以使用更新的 JS 特性，但需要运行环境支持或经过转译。
- **module**：指定模块化规范。本例选用 CommonJS，适合 Node.js 环境。如果是前端项目并且使用打包器，可以设置为`ESNext`或`ES2015`以使用 ES Module，再由打包器处理。
- **strict**：开启**严格模式**，它包含了一系列严格的编译选项（如`noImplicitAny`, `strictNullChecks`, `strictFunctionTypes`等）。开启后，TypeScript 会对隐式的 any 类型、`null/undefined` 检查等进行更严格校验，能有效减少 bug，通常**推荐设为 true**。
- **outDir**：指定编译后输出的目录。本例将所有编译生成的 `.js` 文件放入项目下的 `dist` 文件夹，以与源码分离。
- **esModuleInterop**：开启 ECMAScript 模块互操作性，它会为 CommonJS 模块默认导出提供兼容的导入方式。这通常用于允许你用默认导入语法 `import foo from "foo"` 来引入一个 module.exports = 的库，而不需使用命名导入。
- **skipLibCheck**：跳过对声明文件（*.d.ts）的类型检查。设为 true 可以减少编译时间，因为大量第三方声明文件的检查通常不是必须的（它们假定是正确的）。一般项目可以安全地开启它来提升性能。

还有其他常用的 `compilerOptions` 如：

- **lib**：指定要包含的JS库环境声明，比如 DOM、ESNext 等。默认会根据 target 自动引入相应`lib`，如 target 为 ES6 则包含 ES6 的内置 API 类型声明。
- **sourceMap**：是否生成 source map 文件，设为 true 可以生成 `.map` 文件用于调试 TypeScript 源码。
- **declaration**：是否生成声明文件 (`.d.ts`)，设为 true 则会为每个 .ts 输出对应的 .d.ts，可用于提供给别的项目引用你的代码库。
- **removeComments**：是否移除输出代码中的注释，true 则不会在生成的 JS 中保留注释。
- **baseUrl** / **paths**：配合模块解析使用，设置模块导入的基础路径和路径别名映射，方便在代码中使用绝对路径或别名来导入模块。
- **resolveJsonModule**：允许导入 .json 文件。
- **experimentalDecorators**：启用对实验性的装饰器语法的支持（常用于框架，如 Angular）。

`include` 和 `exclude` 字段则定义了编译的文件范围。通常我们 `include` 项目 src 目录下的 **.ts / .tsx 文件，`exclude` 掉 `node_modules`、打包输出目录、测试文件等无需编译的部分。也可以使用 `"files"` 列出具体要编译的文件列表。

完整的编译选项列表可以参考官方文档或使用 `tsc --help` 查看 ([tsconfig.json · TypeScript中文网 · TypeScript——JavaScript的超集](http://www.tslang.cn/docs/handbook/tsconfig-json.html#:~:text=%E7%BB%86%E8%8A%82))。合理配置 `tsconfig.json` 能帮助定制编译行为、适配不同运行环境需求，是使用 TypeScript 的重要一步。

### 开发工具链整合

TypeScript 的编译器 (`tsc`) 可以独立使用，也可以很方便地集成到各种构建工具和开发环境中：

- **命令行编译**：直接运行 `tsc` 命令即可按照 tsconfig.json 配置编译项目。如需持续监听文件变化，使用 `tsc --watch`。
- **构建工具集成**：诸如 Webpack、Rollup、Parcel 等打包器都有 TypeScript 支持插件（如 `ts-loader`、`@rollup/plugin-typescript` 等），可以在构建过程中完成 TS 编译。利用这些工具可以将 TypeScript 与其他资源一起打包，并支持热更新等开发功能 ([一些你需要掌握的tsconfig.json 常用配置项](https://zhuanlan.zhihu.com/p/570939192#:~:text=%E5%A4%A7%E5%AE%B6%E5%A5%BD%EF%BC%8C%E6%88%91%E6%98%AF%E5%89%8D%E7%AB%AF%E8%A5%BF%E7%93%9C%E5%93%A5%E3%80%82%20tsconfig,init%E3%80%82))。
- **Babel 转译**：也可使用 Babel 来转译 TypeScript（需配合 `@babel/preset-typescript`），这种方式只做语法层转换不做类型检查，通常在已有 Babel 流水线中引入 TS 支持，但仍需要搭配 `tsc --noEmit` 做类型检查以保障安全。
- **测试框架**：大部分测试框架（如 Jest、Mocha）都支持 TypeScript，通过配置预处理器或直接支持 TS 编写测试。
- **IDE 编辑器支持**：主流编辑器如 VS Code、WebStorm 等对 TypeScript 提供一流支持。VS Code 内置 TypeScript 语言服务，可在编码时实时类型检查、自动补全、跳转定义等。配合编辑器，即使不手动运行编译器，也能及时发现错误、提高开发效率。
- **ts-node**：这是一个 TypeScript 执行器，允许直接运行 TypeScript 文件而无需预编译（在内部自动先编译再运行）。对于脚本或后端应用开发调试很方便。但在生产环境一般还是编译出 JS 再运行更稳妥。

综上，TypeScript 已与现代前端/后端工程紧密集成。从编辑器即时反馈，到构建流水线的类型检查，再到运行和测试，都有完善的工具链支持。配置好合适的选项并利用这些工具，能够充分发挥 TypeScript 在大型项目中的价值，使开发过程更高效、代码更健壮。

---

以上内容涵盖了 TypeScript 从入门到进阶的重要知识点，包括基础类型概念、类型系统特性、函数与泛型、面向对象支持、实用的类型工具、类型推断和兼容机制，以及模块与配置工具链等方方面面。掌握这些内容，可以帮助有一定 JavaScript 基础的开发者系统地学习和应用 TypeScript，在日常开发中利用类型系统提高代码的健壮性和可维护性。今后可结合实践不断深入，对更加高级的类型技巧（如条件类型、映射类型等）和最新特性进行探索，持续提升 TypeScript 开发技能。相信通过类型的约束与辅助，您将在大型项目中写出更健壮、自文档化的代码，在开发效率和代码质量上都更上一层楼。 ([TypeScript 中文手册 - TypeScript 中文手册](https://typescript.bootcss.com/#:~:text=TypeScript%E5%85%B7%E6%9C%89%E7%B1%BB%E5%9E%8B%E7%B3%BB%E7%BB%9F%EF%BC%8C%E4%B8%94%E6%98%AFJavaScript%E7%9A%84%E8%B6%85%E9%9B%86%E3%80%82%20%E5%AE%83%E5%8F%AF%E4%BB%A5%E7%BC%96%E8%AF%91%E6%88%90%E6%99%AE%E9%80%9A%E7%9A%84JavaScript%E4%BB%A3%E7%A0%81%E3%80%82%20TypeScript%E6%94%AF%E6%8C%81%E4%BB%BB%E6%84%8F%E6%B5%8F%E8%A7%88%E5%99%A8%EF%BC%8C%E4%BB%BB%E6%84%8F%E7%8E%AF%E5%A2%83%EF%BC%8C%E4%BB%BB%E6%84%8F%E7%B3%BB%E7%BB%9F%E5%B9%B6%E4%B8%94%E6%98%AF%E5%BC%80%E6%BA%90%E7%9A%84%E3%80%82)) ([基础类型 · TypeScript中文网 · TypeScript——JavaScript的超集](http://www.tslang.cn/docs/handbook/basic-types.html#:~:text=TypeScript%E6%94%AF%E6%8C%81%E4%B8%8EJavaScript%E5%87%A0%E4%B9%8E%E7%9B%B8%E5%90%8C%E7%9A%84%E6%95%B0%E6%8D%AE%E7%B1%BB%E5%9E%8B%EF%BC%8C%E6%AD%A4%E5%A4%96%E8%BF%98%E6%8F%90%E4%BE%9B%E4%BA%86%E5%AE%9E%E7%94%A8%E7%9A%84%E6%9E%9A%E4%B8%BE%E7%B1%BB%E5%9E%8B%E6%96%B9%E4%BE%BF%E6%88%91%E4%BB%AC%E4%BD%BF%E7%94%A8%E3%80%82))

