# 作用域链
## 作用域
>   作用域就是变量和函数的可访问范围，控制着变量和函数的可见性与生命周期
### 分类
> 全局作用域 :最外层函数定义的变量拥有全局作用域，即对任何内部函数来说，都是可以访问的：
```
<script>
      var outerVar = "outer";
      function fn(){
         console.log(outerVar);
      }
      fn();  // "outer"
   </script>
```
> 局部作用域 :和全局作用域相反，局部作用域一般只在固定的代码片段内可访问到，而对于函数外部是无法访问的，最常见的例如函数内部
```
<script>
      function fn(){
         var innerVar = "inner";
      }
      fn();
      console.log(innerVar);// ReferenceError: innerVar is not defined
</script>
```
> 注意：函数内部声明变量的时候，一定要使用var命令。如果不用的话，你实际上声明了一个全局变量！
```
 <script>
      var scope = "global";
      function fn(){
         console.log(scope);// undefined
         var scope = "local";
         console.log(scope);// result:local;
      }
      fn();
   </script>
```
## 执行上下文(执行环境)
> 每个执行环境都有一个与之关联的变量对象（variable object, VO），执行环境中定义的所有变量和函数都会保存在这个对象中，解析器在处理数据的时候就会访问这个内部对象

## 作用域链
> 当代码在一个环境中执行时，会创建变量对象的一个作用域链来保证对执行环境有权访问的变量和函数的有序访问。作用域第一个对象始终是当前执行代码所在环境的变量对象(VO)

