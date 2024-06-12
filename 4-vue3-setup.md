- data(){}、methods:{} 均可以使用，但不建议使用。为了向下兼容
- setup(){} 新增 里面的数据和方法均可直接在模版内使用
```
setup(){
    //表演的舞台
    //准备数据 data
    let name = 'py';
    let age = 21;
    let a = 300;

    //方法 methods
    function sayHello(){
      alert(`My name is ${name}, ${age} ${age === 1  ? 'year' : 'years'} old`);
    }


    //在vue3的配置里去读取vue2的属性
    function test2(){
      console.log(name);
      console.log(age);
      console.log(sayHello);
      console.log(this.vue2);
      console.log(this.test1);
    }


    //返回一个对象
    return {
      name,
      age,
      sayHello,
      test2,
      a
    }
}
```