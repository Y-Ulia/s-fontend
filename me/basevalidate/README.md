# JavaScript检测之basevalidate.js


上篇文章「[JavaScript检测原始值、引用值、属性](http://shijiajie.com/2016/06/20/javascript-maintainable-javascript-validate1/)」中涉及了大量有用的代码范例，为了让大家更方便的使用这些代码，博主特意把这些代码重新整理并托管到 [GitHub](https://github.com/stone0090/base-validate)，项目地址是：[https://github.com/stone0090/base-validate](https://github.com/stone0090/base-validate)，如果 [basevalidate.js](https://github.com/stone0090/base-validate) 对您有帮助，请帮忙在 [GitHub](https://github.com/stone0090/base-validate) 上 [Star](https://github.com/stone0090/base-validate) 该项目，谢谢大家。

[basevalidate.js](https://github.com/stone0090/base-validate) 包含 **14个独立检测方法** 和 **1个综合检测方法**，示例代码如下：（如果大家还有其他需要，请在文章尾部的微信公众号中留言，我尽量为大家实现。）

``` html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>basevalidate test</title>
  <script type="text/javascript" src="basevalidate.js"></script>
  <script>

    var Person = function(){
      this.name = 'stone';
      this.age = 30;
    }

    var person = new Person();
    var nums = [123, 456, 789];

    // 14个独立检测方法
    console.log(baseValidate.isString(null));
    console.log(baseValidate.isNumber(null));
    console.log(baseValidate.isBoolean(null));
    console.log(baseValidate.isUndefined(null));
    console.log(baseValidate.isNull(null));
    console.log(baseValidate.isObject(null));
    console.log(baseValidate.instanceOf(null));
    console.log(baseValidate.isFunction(null));
    console.log(baseValidate.isArray(null));
    console.log(baseValidate.isProperty(null));
    console.log(baseValidate.isOwnProperty(null));
    console.log(baseValidate.isDomProperty(null));
    console.log(baseValidate.isBomProperty(null));
    console.log(baseValidate.isEmpty(null));

    // 1个综合检测方法 baseValidate(value, object)，等价于 baseValidate.validateAll(value ,object)
    console.log(baseValidate('123'));
    console.log(baseValidate(123));
    console.log(baseValidate(true));
    console.log(baseValidate(person, Person));
    console.log(baseValidate(nums));
    console.log(baseValidate('age', person));
    console.log(baseValidate('name', person));
    console.log(baseValidate(alert));
    console.log(baseValidate(document.getElementById));

    // 以下皆为 isEmpty() 方法为 false 的情况
    console.log(baseValidate()); // 不传参数，参数默认为 undefined
    console.log(baseValidate(null));
    console.log(baseValidate(''));
    console.log(baseValidate(0));
    console.log(baseValidate(false));
    console.log(baseValidate({}));
    console.log(baseValidate([]));
    console.log(baseValidate(NaN));
    
  </script>
</head>
<body></body>
</html>
```

测试结果如下：

![](http://7xkhp9.com1.z0.glb.clouddn.com/blog/javascript-maintainable-javascript-basevalidatejs/1.png?imageView2/2/w/830/interlace/1/q/100)

不知道大家有没有发现，其中一个结果好像不太正确，`console.log(baseValidate('name', person))` 为什么会输出 `isBomProperty: true`，这是因为`window` 对象中也有 `name` 属性，所以 `name` 也被认为是 BOM 的属性。


欢迎来到 [石佳劼的博客](http://shijiajie.com)，如有疑问，请在[「原文」评论区](http://shijiajie.com/2016/06/25/javascript-maintainable-javascript-basevalidatejs/#ds-thread) 留言，我会尽量为您解答。

---
![](http://7xkhp9.com1.z0.glb.clouddn.com/blog/other/blog_statement_20160618_01.png?imageView2/2/w/650/interlace/1/q/100)