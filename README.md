# 深拷贝与浅拷贝的区别:
### 简单点来说，就是假设B复制了A，当修改A时，看B是否会发生变化，如果B也跟着变了，说明这是浅拷贝，拿人手短，如果B没变，那就是深拷贝，自食其力。
## JS 中深拷贝的几种实现方法
### 1. 使用递归的方式实现深拷贝

```
//使用递归的方式实现数组、对象的深拷贝
function deepClone1(obj) {
  //判断拷贝的要进行深拷贝的是数组还是对象，是数组的话进行数组拷贝，对象的话进行对象拷贝
  var objClone = Array.isArray(obj) ? [] : {};
  //进行深拷贝的不能为空，并且是对象或者是
  if (obj && typeof obj === "object") {
    for (key in obj) {
      if (obj.hasOwnProperty(key)) {
        if (obj[key] && typeof obj[key] === "object") {
          objClone[key] = deepClone1(obj[key]);
        } else {
          objClone[key] = obj[key];
        }
      }
    }
  }
  return objClone;
}
```

### 2. 通过 JSON 对象实现深拷贝

```
JSON.parse(JSON.stringify(obj))
```

### 3. 通过jQuery的extend方法实现深拷贝

```
var array = [1,2,3,4];
var newArray = $.extend(true,[],array);
```

### 4. Object.assign()拷贝

```
当对象中只有一级属性，没有二级属性的时候，此方法为深拷贝，但是对象中有对象的时候，此方法，在二级属性以后就是浅拷贝
```

##### 了解更多：[https://www.cnblogs.com/echolun/p/7889848.html](https://note.youdao.com/)
