<template>
    <h1>当前求和为：{{ sum }}</h1>
    <button @click="sum++">点我+1</button>
    <hr>
    <h2>当前的信息为：{{ msg }}</h2>
    <button @click="msg+='!'">修改信息</button>
    <h2>名字：{{ person.name }}</h2>
    <h2>年龄：{{ person.age }}</h2>
    <button @click="person.name+='~'">修改姓名</button>
    <button @click="person.age++">增长年龄</button>
    <h2>薪资：{{ person.job.j1.salary }}K</h2>
    <button @click="person.job.j1.salary++">涨薪</button>
</template>
  
<script>
import {ref, reactive, watch} from 'vue';
export default {
    name: 'DemoPage',
    // watch: { // vue2写法
    //     // sum(newValue, oldValue) {
    //     //     console.log('sum的值变化了', newValue, oldValue);
    //     // }
    //     sum: {
    //         setImmediate: true, // 立即检测
    //         deep: true, // 深度检测
    //         handler(newValue, oldValue) {
    //             console.log('sum的值变化了', newValue, oldValue);
    //         }
    //     }
    // },
    setup() {
        let sum = ref(0);
        let msg = ref('你好啊！');
        let person = reactive({ // 如果reactive改ref 检测person.value或者{deep:true}
            name: '张三',
            age: 18,
            job: {
                j1: {
                    salary: 20
                }
            }
        });
        // 监视 情况一：监视ref定义的一个响应式数据
        // watch(sum, (newValue, oldValue) => {
        //     console.log('sum的值变化了', newValue, oldValue);
        // }, {
        //     immediate: true
        // });
        // watch(msg, (newValue, oldValue) => {
        //     console.log('sum的值变化了', newValue, oldValue);
        // });
        // 监视 情况二：监视ref所以定义的多个响应式数据
        // watch([sum, msg], (newValue, oldValue) => {
        //     console.log('sum的值变化了', newValue, oldValue);
        // });
        // 情况三：监视reactive定义的一个响应式数据
        // 1、无法正确获取oldValue
        // 2、深度检测是强制性
        // watch(person, (newValue, oldValue) => {
        //     console.log('person变化了', newValue, oldValue);
        // }, {deep: true});
        // 情况四：监视reactive定义的一个属性的响应式数据
        // watch(() => person.age, (newValue, oldValue) => {
        //     console.log('person.age变化了', newValue, oldValue);
        // });
        // 情况五：监视reactive定义的某些属性的响应式数据
        // watch([() => person.age, () => person.name], (newValue, oldValue) => {
        //     console.log('person.age变化了', newValue, oldValue);
        // });
        // 特殊情况 监视对象里面的job
        watch([() => person.job], (newValue, oldValue) => {
            console.log('person.job变化了', newValue, oldValue);
        }, {
            deep: true
        });
        watchEffect(() => {
            // 要指定监视的谁，以及监视的回调
            // watchEffect函数里所依赖的参数变化的时候，就会执行
            // 回调中用到的数据只要发生变化，则直接执行回调
            // computed 注重返回值
            // watchEffect 注重返回过程
            const x1 = sum.value;
            const x2 = parent.age;
            console.log('watchEffect 回调执行了');
        });
        return {
            sum,
            msg,
            person
        }
    }
    }
</script>

<style>
    #app {
        font-family: Avenir, Helvetica, Arial, sans-serif;
        -webkit-font-smoothing: antialiased;
        -moz-osx-font-smoothing: grayscale;
        text-align: center;
        color: #2c3e50;
        margin-top: 60px;
    }
</style>
