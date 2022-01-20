### 一、let和const

####     1、let

//声明变量

​    let a;

​    let b,c,d;

​    let e = 100;

​    let f = 521, g = 'iloveyou', h = [];

特点：

1. 变量不能重复声明

2. 块儿级作用域  全局, 函数, eval

3. 不存在变量提升

4. 不影响作用域链

#### 2、const

​    //声明常量

​    const SCHOOL = '尚硅谷';

1. 一定要赋初始值

​    // const A;

2. 一般常量使用大写(潜规则)

​    // const a = 100;

3. 常量的值不能修改

​    // SCHOOL = 'ATGUIGU';

4. 块儿级作用域

​    // {

​    //   const PLAYER = 'UZI';

​    // }

​    // console.log(PLAYER);

5. 对于数组和对象的元素修改, 不算做对常量的修改, 不会报错

​    const TEAM = ['UZI','MXLG','Ming','Letme'];

​    // TEAM.push('Meiko');



### 二、解构赋值

ES6 允许按照一定模式从数组和对象中提取值，对变量进行赋值

1. #### 数组的解构

​    const F4 = ['小沈阳','刘能','赵四','宋小宝'];

​     let [xiao, liu, zhao, song] = F4;

​     console.log(xiao);

​     console.log(liu);

​     console.log(zhao);

​     console.log(song);

2. #### 对象的解构

​     const zhao = {

​      name: '赵本山',

​      age: '不详',

​     xiaopin: function(){

​     console.log("我可以演小品");

​     }

​    };



### 三、模板字符串

​     ES6 引入新的声明字符串的方式 『``』 '' "" 

1. #### 声明

​     let str = `我也是一个字符串哦!`;

​     console.log(str, typeof str);



2. #### 内容中可以直接出现换行符

​    let str = `<ul>

​          <li>沈腾</li>

​          <li>玛丽</li>

​          <li>魏翔</li>

​          <li>艾伦</li>

​          </ul>`;

3. #### 变量拼接

​    let lovest = '魏翔';

​    let out = `${lovest}是我心目中最搞笑的演员!!`;



### 四、简化对象写法

 ES6 允许在大括号里面，直接写入变量和函数，作为对象的属性和方法。

​    这样的书写更加简洁

​    let name = '尚硅谷';

​    let change = function(){

​      console.log('我们可以改变你!!');

​    }



​    const school = {

​      name,

​      change,

​      improve(){

​        console.log("我们可以提高你的技能");

​      }

​    }



### 五、箭头函数

#### 1.ES6 允许使用「箭头」（=>）定义函数。

​    let fn = (a,b) => {

​    return a + b;

​    }

​    //调用函数

​     let result = fn(1, 2);

​     console.log(result);

#### 2.this 是静态的. this 始终指向函数声明时所在作用域下的 this 的值。

eg：

​       function getName(){

​      console.log(this.name);

​    }

​    let getName2 = () => {

​      console.log(this.name);

​    }

#### 3.不能作为构造实例化对象

eg：

​     let Person = (name, age) => {

​       this.name = name;

​       this.age = age;

​     }

​     let me = new Person('xiao',30);

​     console.log(me);

#### 4.不能使用 arguments 变量

eg：

​     let fn = () => {

​     console.log(arguments);

​     }

​    fn(1,2,3);

#### 5.箭头函数的简写

eg：

#####       1) 省略小括号, 当形参有且只有一个的时候

​       let add = n => {

​       return n + n;

​       }

​       console.log(add(9));

#####       2) 省略花括号, 当代码体只有一条语句的时候, 此时 return 必须省略

​       而且语句的执行结果就是函数的返回值

​      let pow = n => n * n;

​      console.log(pow(8));

### 六、参数默认值

​    ES6 允许给函数参数赋值初始值

####     1. 形参初始值 具有默认值的参数, 一般位置要靠后(潜规则)

​     function add(a,c=10,b) {

​     return a + b + c;

​     }

​     let result = add(1,2);

​     console.log(result);

####     2. 与解构赋值结合

​    function connect({host="127.0.0.1", username,password, port}){

​      console.log(host)

​      console.log(username)

​      console.log(password)

​      console.log(port)

​    }

​    connect({

​      host: 'atguigu.com',

​      username: 'root',

​      password: 'root',

​      port: 3306

​    })

### 七、rest参数

​     ES6 引入 rest 参数，用于获取函数的实参，用来代替 arguments

​    ES5 获取实参的方式

​    function date(){

​    console.log(arguments);

​     }

​     date('白芷','阿娇','思慧');



​    rest 参数

​    function date(...args){

​    console.log(args);// filter some every map 

​     }

 date('阿娇','柏芝','思慧');



​     rest 参数必须要放到参数最后

​     function fn(a,b,...args){

​      console.log(a);

​      console.log(b);

​      console.log(args);

​     }

​    fn(1,2,3,4,5,6);

### 八、spread扩展运算符

####  1.简介

『...』 扩展运算符能将『数组』转换为逗号分隔的『参数序列』

​    声明一个数组 ...

​    const tfboys = ['易烊千玺','王源','王俊凯'];

​     => '易烊千玺','王源','王俊凯'

​     声明一个函数

​    function chunwan(){

​      console.log(arguments);

​    }

​    chunwan(...tfboys);// chunwan('易烊千玺','王源','王俊凯')

#### 2.应用

#####     1. 数组的合并 

​     const kuaizi = ['王太利','肖央'];

​     const fenghuang = ['曾毅','玲花'];

​     const zuixuanxiaopingguo = kuaizi.concat(fenghuang);

​    const zuixuanxiaopingguo = [...kuaizi, ...fenghuang];

​    console.log(zuixuanxiaopingguo);



#####     2. 数组的克隆

​     const sanzhihua = ['E','G','M'];

​     const sanyecao = [...sanzhihua];//  ['E','G','M']

​     console.log(sanyecao);



#####     3. 将伪数组转为真正的数组

​    const divs = document.querySelectorAll('div');

​    const divArr = [...divs];

​    console.log(divArr);// arguments

### 九、Symbol

#### 1.基本使用

​    //创建Symbol

​    let s = Symbol();

​    // console.log(s, typeof s);

​    let s2 = Symbol('尚硅谷');

​    let s3 = Symbol('尚硅谷');

​    //Symbol.for 创建

​    let s4 = Symbol.for('尚硅谷');

​    let s5 = Symbol.for('尚硅谷');



​    //不能与其他数据进行运算

​    //   let result = s + 100;

​    //   let result = s > 100;

​    //   let result = s + s;



​    // USONB  you are so niubility 

​    // u  undefined

​    // s  string  symbol

​    // o  object

​    // n  null number

​    // b  boolean

#### 2.创建对象属性

​    //向对象中添加方法 up down

​    let game = {

​      name:'俄罗斯方块',

​      up: function(){},

​      down: function(){}

​    };

​    

​    //声明一个对象

​    // let methods = {

​    //   up: Symbol(),

​    //   down: Symbol()

​    // };



​    // game[methods.up] = function(){

​    //   console.log("我可以改变形状");

​    // }



​    // game[methods.down] = function(){

​    //   console.log("我可以快速下降!!");

​    // }



​    // console.log(game);



​    //

​    let youxi = {

​      name:"狼人杀",

[Symbol('say')]: function(){

​        console.log("我可以发言")

​      },

[Symbol('zibao')]: function(){

​        console.log('我可以自爆');

​      }

​    }

​    console.log(youxi)

#### 3.内置属性

​    // class Person{

​    //   static [Symbol.hasInstance](param){

​    //     console.log(param);

​    //     console.log("我被用来检测类型了");

​    //     return false;

​    //   }

​    // }



​    // let o = {};



​    // console.log(o instanceof Person);



​    // const arr = [1,2,3];

​    // const arr2 = [4,5,6];

​    // arr2[Symbol.isConcatSpreadable] = false;

​    // console.log(arr.concat(arr2));

### 十、迭代器

#### 1.迭代器声明使用

​    //声明一个数组

​    const xiyou = ['唐僧','孙悟空','猪八戒','沙僧'];



​    //使用 for...of 遍历数组

​    // for(let v of xiyou){

​    //   console.log(v);

​    // }

​    let iterator = xiyou[Symbol.iterator]();



​    //调用对象的next方法

​    console.log(iterator.next());

​    console.log(iterator.next());

​    console.log(iterator.next());

​    console.log(iterator.next());

​    console.log(iterator.next());



#### 2.迭代器的自定义遍历

​    const banji = {

​      name: "终极一班",

​      stus: [

​        'xiaoming',

​        'xiaoning',

​        'xiaotian',

​        'knight'

​      ],

​      [Symbol.iterator]() {

​        //索引变量

​        let index = 0;

​        //

​        let _this = this;

​        return {

​          next: function () {

​            if (index < _this.stus.length) {

​              const result = { value: _this.stus[index], done: false };

​              //下标自增

​              index++;

​              //返回结果

​              return result;

​            }else{

​              return {value: undefined, done: true};

​            }

​          }

​        };

​      }

​    }

​    //遍历这个对象 

​    for (let v of banji) {

​      console.log(v);

​    }

### 十一、生成器

#### 1.生成器函数

​    //生成器其实就是一个特殊的函数

​    //异步编程  纯回调函数  node fs  ajax mongodb

​    //函数代码的分隔符

​    function * gen(){

​      // console.log(111);

​      yield '一只没有耳朵';

​      // console.log(222);

​      yield '一只没有尾部';

​      // console.log(333);

​      yield '真奇怪';

​      // console.log(444);

​    }



​    let iterator = gen();

​    console.log(iterator.next());

​    console.log(iterator.next());

​    console.log(iterator.next());

​    console.log(iterator.next());



#### 2.生成器函数参数

​    function * gen(arg){

​      console.log(arg);

​      let one = yield 111;

​      console.log(one);

​      let two = yield 222;

​      console.log(two);

​      let three = yield 333;

​      console.log(three);

​    }



​    //执行获取迭代器对象

​    let iterator = gen('AAA');

​    console.log(iterator.next());

​    //next方法可以传入实参

​    console.log(iterator.next('BBB'));

​    console.log(iterator.next('CCC'));

​    console.log(iterator.next('DDD'));

#### 3.生成器函数实例

​    // 异步编程  文件操作 网络操作(ajax, request) 数据库操作

​    // 1s 后控制台输出 111  2s后输出 222  3s后输出 333 

​    // 回调地狱

​    // setTimeout(() => {

​    //   console.log(111);

​    //   setTimeout(() => {

​    //     console.log(222);

​    //     setTimeout(() => {

​    //       console.log(333);

​    //     }, 3000);

​    //   }, 2000);

​    // }, 1000);



​    function one(){

​      setTimeout(()=>{

​        console.log(111);

​        iterator.next();

​      },1000)

​    }



​    function two(){

​      setTimeout(()=>{

​        console.log(222);

​        iterator.next();

​      },2000)

​    }



​    function three(){

​      setTimeout(()=>{

​        console.log(333);

​        iterator.next();

​      },3000)

​    }



​    function * gen(){

​      yield one();

​      yield two();

​      yield three();

​    }



​    //调用生成器函数

​    let iterator = gen();

​    iterator.next();



#### 4.生成器函数实例2

​    //模拟获取  用户数据  订单数据  商品数据 

​    function getUsers(){

​      setTimeout(()=>{

​        let data = '用户数据';

​        //调用 next 方法, 并且将数据传入

​        iterator.next(data);

​      }, 1000);

​    }



​    function getOrders(){

​      setTimeout(()=>{

​        let data = '订单数据';

​        iterator.next(data);

​      }, 1000)

​    }



​    function getGoods(){

​      setTimeout(()=>{

​        let data = '商品数据';

​        iterator.next(data);

​      }, 1000)

​    }



​    function * gen(){

​      let users = yield getUsers();

​      let orders = yield getOrders();

​      let goods = yield getGoods();

​    }



​    //调用生成器函数

​    let iterator = gen();

​    iterator.next();

### 十二、Promise

#### 1.Promise基本语法

​    //实例化 Promise 对象

​    const p = new Promise(function(resolve, reject){

​      setTimeout(function(){

​        //

​        // let data = '数据库中的用户数据';

​        // resolve

​        // resolve(data);



​        let err = '数据读取失败';

​        reject(err);

​      }, 1000);

​    });



​    //调用 promise 对象的 then 方法

​    p.then(function(value){

​      console.log(value);

​    }, function(reason){

​      console.error(reason);

​    })



#### 2.Promise封装读取文件

##### //1. 引入 fs 模块

const fs = require('fs');



##### //2. 调用方法读取文件

// fs.readFile('./resources/为学.md', (err, data)=>{

//   //如果失败, 则抛出错误

//   if(err) throw err;

//   //如果没有出错, 则输出内容

//   console.log(data.toString());

// });



##### //3. 使用 Promise 封装

const p = new Promise(function(resolve, reject){

  fs.readFile("./resources/为学.mda", (err, data)=>{

​    //判断如果失败

​    if(err) reject(err);

​    //如果成功

​    resolve(data);

  });

});



p.then(function(value){

  console.log(value.toString());

}, function(reason){

  console.log("读取失败!!");

});



#### 3.Promise封装AJAX

​    // 接口地址: https://api.apiopen.top/getJoke

​    const p = new Promise((resolve, reject) => {

​      //1. 创建对象

​      const xhr = new XMLHttpRequest();



​      //2. 初始化

​      xhr.open("GET", "https://api.apiopen.top/getJoke");



​      //3. 发送

​      xhr.send();



​      //4. 绑定事件, 处理响应结果

​      xhr.onreadystatechange = function () {

​        //判断

​        if (xhr.readyState === 4) {

​          //判断响应状态码 200-299

​          if (xhr.status >= 200 && xhr.status < 300) {

​            //表示成功

​            resolve(xhr.response);

​          } else {

​            //如果失败

​            reject(xhr.status);

​          }

​        }

​      }

​    })

​    

​    //指定回调

​    p.then(function(value){

​      console.log(value);

​    }, function(reason){

​      console.error(reason);

​    });



#### 4.Promise-then方法

​    //创建 promise 对象

​    const p = new Promise((resolve, reject)=>{

​      setTimeout(()=>{

​        resolve('用户数据');

​        // reject('出错啦');

​      }, 1000)

​    });



​    //调用 then 方法  then方法的返回结果是 Promise 对象, 对象状态由回调函数的执行结果决定

​    //1. 如果回调函数中返回的结果是 非 promise 类型的属性, 状态为成功, 返回值为对象的成功的值



​    // const result = p.then(value => {

​    //   console.log(value);

​    //   //1. 非 promise 类型的属性

​    //   // return 'iloveyou';

​    //   //2. 是 promise 对象

​    //   // return new Promise((resolve, reject)=>{

​    //   //   // resolve('ok');

​    //   //   reject('error');

​    //   // });

​    //   //3. 抛出错误

​    //   // throw new Error('出错啦!');

​    //   throw '出错啦!';

​    // }, reason=>{

​    //   console.warn(reason);

​    // });



​    //链式调用

​    p.then(value=>{

​    }).then(value=>{

​    });



#### 5.Promise-catch方法

​    const p = new Promise((resolve, reject)=>{

​      setTimeout(()=>{

​        //设置 p 对象的状态为失败, 并设置失败的值

​        reject("出错啦!");

​      }, 1000)

​    });



​    // p.then(function(value){}, function(reason){

​    //   console.error(reason);

​    // });



​    p.catch(function(reason){

​      console.warn(reason);

​    });



#### 6.Promise实践-读取多个文件

//引入 fs 模块

const fs = require("fs");



// fs.readFile('./resources/为学.md', (err, data1)=>{

//   fs.readFile('./resources/插秧诗.md', (err, data2)=>{

//     fs.readFile('./resources/观书有感.md', (err, data3)=>{

//       let result = data1 + '\r\n' +data2  +'\r\n'+ data3;

//       console.log(result);

//     });

//   });

// });



//使用 promise 实现

const p = new Promise((resolve, reject) => {

  fs.readFile("./resources/为学.md", (err, data) => {

​    resolve(data);

  });

});



p.then(value => {

  return new Promise((resolve, reject) => {

​    fs.readFile("./resources/插秧诗.md", (err, data) => {

​      resolve([value, data]);

​    });

  });

}).then(value => {

  return new Promise((resolve, reject) => {

​    fs.readFile("./resources/观书有感.md", (err, data) => {

​      //压入

​      value.push(data);

​      resolve(value);

​    });

  })

}).then(value => {

  console.log(value.join('\r\n'));

});



### 十三、set集合

#### 1.set集合使用

​    //声明一个 set

​    let s = new Set();

​    let s2 = new Set(['大事儿','小事儿','好事儿','坏事儿','小事儿']);



​    //元素个数

​    // console.log(s2.size);

​    //添加新的元素

​    // s2.add('喜事儿');

​    //删除元素

​    // s2.delete('坏事儿');

​    //检测

​    // console.log(s2.has('糟心事'));

​    //清空

​    // s2.clear();

​    // console.log(s2);



​    for(let v of s2){

​      console.log(v);

​    }



#### 2.Set集合实践

​    let arr = [1,2,3,4,5,4,3,2,1];

#####     //1. 数组去重

​    // let result = [...new Set(arr)];

​    // console.log(result);

#####     //2. 交集

​    let arr2 = [4,5,6,5,6];

​    // let result = [...new Set(arr)].filter(item => {

​    //   let s2 = new Set(arr2);// 4 5 6

​    //   if(s2.has(item)){

​    //     return true;

​    //   }else{

​    //     return false;

​    //   }

​    // });

​    // let result = [...new Set(arr)].filter(item => new Set(arr2).has(item));

​    // console.log(result);



#####     //3. 并集

​    // let union = [...new Set([...arr, ...arr2])];

​    // console.log(union);



#####     //4. 差集

​    let diff = [...new Set(arr)].filter(item => !(new Set(arr2).has(item)));

​    console.log(diff);



### 十四、Map

​    //声明 Map

​    let m = new Map();



​    //添加元素

​    m.set('name','尚硅谷');

​    m.set('change', function(){

​      console.log("我们可以改变你!!");

​    });

​    let key = {

​      school : 'ATGUIGU'

​    };

​    m.set(key, ['北京','上海','深圳']);



​    //size

​    // console.log(m.size);

​    //删除

​    // m.delete('name');

​    //获取

​    // console.log(m.get('change'));

​    // console.log(m.get(key));

​    //清空

​    // m.clear();

​    //遍历

​    for(let v of m){

​      console.log(v);

​    }

​    // console.log(m);





### 十五、class类

#### 1.介绍和基本使用

​    //手机

​    function Phone(brand, price){

​      this.brand = brand;

​      this.price = price;

​    }



​    //添加方法

​    Phone.prototype.call = function(){

​      console.log("我可以打电话!!");

​    }



​    //实例化对象

​    let Huawei = new Phone('华为', 5999);

​    Huawei.call();

​    console.log(Huawei);



​    //class

​    class Shouji{

​      //构造方法 名字不能修改

​      constructor(brand, price){

​        this.brand = brand;

​        this.price = price;

​      }



​      //方法必须使用该语法, 不能使用 ES5 的对象完整形式

​      call(){

​        console.log("我可以打电话!!");

​      }

​    }



​    let onePlus = new Shouji("1+", 1999);



​    console.log(onePlus);

#### 2.类的静态成员

​    // function Phone(){



​    // }

​    // Phone.name = '手机';

​    // Phone.change = function(){

​    //   console.log("我可以改变世界");

​    // }

​    // Phone.prototype.size = '5.5inch';



​    // let nokia = new Phone();



​    // console.log(nokia.name);

​    // // nokia.change();

​    // console.log(nokia.size);



​    class Phone{

​      //静态属性

​      static name = '手机';

​      static change(){

​        console.log("我可以改变世界");

​      }

​    }

​    let nokia = new Phone();

​    console.log(nokia.name);

​    console.log(Phone.name);





#### 3.类的继承

##### 1.ES5构造函数的继承

//手机

​    function Phone(brand, price){

​      this.brand = brand;

​      this.price = price;

​    }



​    Phone.prototype.call = function(){

​      console.log("我可以打电话");

​    }



​    //智能手机

​    function SmartPhone(brand, price, color, size){

​      Phone.call(this, brand, price);

​      this.color = color;

​      this.size = size;

​    }



​    //设置子级构造函数的原型

​    SmartPhone.prototype = new Phone;

​    SmartPhone.prototype.constructor = SmartPhone;



​    //声明子类的方法

​    SmartPhone.prototype.photo = function(){

​      console.log("我可以拍照")

​    }

​    SmartPhone.prototype.playGame = function(){

​      console.log("我可以玩游戏");

​    }

​    const chuizi = new SmartPhone('锤子',2499,'黑色','5.5inch');

​    console.log(chuizi);



##### 2.ES6-Class类继承

​    class Phone{

​      //构造方法

​      constructor(brand, price){

​        this.brand = brand;

​        this.price = price;

​      }

​      //父类的成员属性

​      call(){

​        console.log("我可以打电话!!");

​      }

​    }

​    class SmartPhone extends Phone {

​      //构造方法

​      constructor(brand, price, color, size){

​        super(brand, price);// Phone.call(this, brand, price)

​        this.color = color;

​        this.size = size;

​      }

​      photo(){

​        console.log("拍照");

​      }



​      playGame(){

​        console.log("玩游戏");

​      }



​      call(){

​        console.log('我可以进行视频通话');

​      }

​    }

​    const xiaomi = new SmartPhone('小米',799,'黑色','4.7inch');

​    // console.log(xiaomi);

​    xiaomi.call();

​    xiaomi.photo();

​    xiaomi.playGame();



##### 3.class里的get和set

​    // get 和 set  

​    class Phone{

​      get price(){

​        console.log("价格属性被读取了");

​        return 'iloveyou';

​      }

​      set price(newVal){

​        console.log('价格属性被修改了');

​      }

​    }

​    //实例化对象

​    let s = new Phone();

​    // console.log(s.price);

​    s.price = 'free';



### 十六、数值扩展

​    //0. Number.EPSILON 是 JavaScript 表示的最小精度

​    //EPSILON 属性的值接近于 2.2204460492503130808472633361816E-16

​    // function equal(a, b){

​    //   if(Math.abs(a-b) < Number.EPSILON){

​    //     return true;

​    //   }else{

​    //     return false;

​    //   }

​    // }

​    // console.log(0.1 + 0.2 === 0.3);

​    // console.log(equal(0.1 + 0.2, 0.3))



​    //1. 二进制和八进制

​    // let b = 0b1010;

​    // let o = 0o777;

​    // let d = 100;

​    // let x = 0xff;

​    // console.log(x);



​    //2. Number.isFinite  检测一个数值是否为有限数

​    // console.log(Number.isFinite(100));

​    // console.log(Number.isFinite(100/0));

​    // console.log(Number.isFinite(Infinity));

​    

​    //3. Number.isNaN 检测一个数值是否为 NaN 

​    // console.log(Number.isNaN(123)); 



​    //4. Number.parseInt Number.parseFloat字符串转整数

​    // console.log(Number.parseInt('5211314love'));

​    // console.log(Number.parseFloat('3.1415926神奇'));



​    //5. Number.isInteger 判断一个数是否为整数

​    // console.log(Number.isInteger(5));

​    // console.log(Number.isInteger(2.5));



​    //6. Math.trunc 将数字的小数部分抹掉  

​    // console.log(Math.trunc(3.5));



​    //7. Math.sign 判断一个数到底为正数 负数 还是零

​    console.log(Math.sign(100));

​    console.log(Math.sign(0));

​    console.log(Math.sign(-20000));



### 十七、对象方法扩展

​    //1. Object.is 判断两个值是否完全相等 

​    // console.log(Object.is(120, 120));// === 

​    // console.log(Object.is(NaN, NaN));// === 

​    // console.log(NaN === NaN);// === 



​    //2. Object.assign 对象的合并

​    // const config1 = {

​    //   host: 'localhost',

​    //   port: 3306,

​    //   name: 'root',

​    //   pass: 'root',

​    //   test: 'test'

​    // };

​    // const config2 = {

​    //   host: 'http://atguigu.com',

​    //   port: 33060,

​    //   name: 'atguigu.com',

​    //   pass: 'iloveyou',

​    //   test2: 'test2'

​    // }

​    // console.log(Object.assign(config1, config2));



​    //3. Object.setPrototypeOf 设置原型对象  Object.getPrototypeof

​    const school = {

​      name: '尚硅谷'

​    }

​    const cities = {

​      xiaoqu: ['北京','上海','深圳']

​    }

​    Object.setPrototypeOf(school, cities);

​    console.log(Object.getPrototypeOf(school));

​    console.log(school);

### 十八、模块化

模块化是指将一个大的程序文件，拆分成许多小的文件，然后将小文件组合起来。

#### 1.模块化的好处 

模块化的优势有以下几点： 
1) 防止命名冲突 
2) 代码复用 
3) 高维护性 

#### 2.模块化规范产品 

ES6 之前的模块化规范有： 
1) CommonJS  =>  NodeJS、Browserify 
2) AMD  =>  requireJS 
3) CMD  =>  seaJS 

#### 3.ES6 模块化语法

模块功能主要由两个命令构成：export 和 import。 
⚫ export 命令用于规定模块的对外接口 
⚫ import 命令用于输入其他模块提供的功能 