
# note 我的技术栈 vue，js，jq，uni-app，小程序，element，es6(学习中),react(下一步计划)，git管理
工作学习笔记记录
# es6 class apply call 正在学习...
基础用法 ----->
class NoteA{
    constructor(x,y){
        this.x = x;
        this.y = y;
    }
    value(){
        return `${this.x}:${this.y}`
    }
}
const data = new NoteA(1,2);

class NoteB{
    constructor(x,y){
        this.x = x;
        this.y = y;
    }
    value(){
        return `我是${this.x},今年${this.y}岁`
    }
}
const data1 = new NoteB('fmz','20');
data1.value.apply(data);
data1.value();

===
<!-- var 可以重复声明
    let 统一作用域不能重复声明 否则报错
        作用域 全局/块级
        不会与预解析
 -->
let or const or var 

let letData={
    统一作用域不能重复声明 否则报错,
    作用域 全局/块级,
     不会与预解析
}
const constData={
    常量，
    一旦赋值不可以修改，
    必须赋值，
    块级作用域，
    不会预解析
}

===
# 结构赋值
objecy
let obj={
    a:1,
    b:2
}
let {a,b,c} = obj;
<!-- 赋值变量必须一样，如果接值没有则是undefined -->
array
let array=[1,12,34];
let [x,x] = array;
<!-- 下标一致 -->
<!-- 面试题 快速交换值 -->
let a= 0;
let b= 0;
[a,b]=[b,a];

string
let str = 'hdfjhsjfhs';

=== 
# 展开运算符
array
let arr = [1,2,3,4];
let arr2 = ['a','b',...arr,'c'];
<!-- 剩余参数 -->
let [a,b,...c] = arr;

 object
let obj1 ={a:1,b:2};
let obj2 = {c:3,d:4,...obj1};

赋值，简单深浅拷贝
let obj2 = {...obj};
obj2.a = 10;

===
# set or map
<-- 构造函数，用来构建某一类的对象 对象的实列话 -->
<-- 参数可以是数组,进行自动去重 -->
<-- set 属性 
    size(保留值的个数==length)
    clear()清空返回undefined;
    delete()删除某项,参数不是下标,参数是value(要删除的数值),返回值true/false,删除成功true
    add(),添加,也会自动去重,如果存在不在显示
    has(),查看值是否存在 返回true/false
    -->
let arr  = [1,2,3,4,1];
let s = new Set(arr);
arr = [...s];

<-- Map 参数不能是对象,没有迭代 -->
<-- Map属性
    clear()清空所有值,=>undefined;
    delete(key==数据的key值)删除某一项=>删除成功true/false,
    get(key);获取某一项值=>key对应的value
    has(key)是否包含某一项=>true/false
    set(key,value)设置一个值 key== 数值的key值,value==数据的value值;
    
 -->
let arr2 =[
    [a,1],
    [b,2]
]
let maps= new Map(arr2);
<!--  -->


# 箭头函数
let fn = (...value)=>{
    console.log(value)
};
fn(1,2,3,4)
<-- 
    参数=>返回值
    单个参数括号可以不要,两个以上,或没有参数加上括号,
    扩展this  如果this不是被某个方法调用,而是自调用其this指向全全局windows
    箭头函数没有arguments 可以使用... 扩展运算符,
    this 箭头函数本身没有this,调用箭头函数this时,指向是其声明时,所在的作用域的this
    函数 默认参数值
    (x=1,y=0)
 -->

<!-- new本身是创造符 -->

# Array
<-- 
    类数组 有下标,有length
    Array.from() 把一个类数组转换成一个真正的数值,
            扩展:
            Array.form()自带map函数=>Array.from(arr,()=>{

            },arr);
            最后一个参数改变this指向,如果是箭头函数this指向默认全局,写成普通function可以
    Array.of() 创建array,
    Array.isArray() 检查是不是一个数组
    arr.find((item,index)=>{ 
        检索数组符合的的值,满足要求第一个元素的值=>返回值 具体值/undefined
    });
    arr.findIndex();
    数组扁平化,二位数组转成一位数组;
    arr.flat();扁平化一个多维数组;参数 提取的层数;  如果不确定数组有多少层使用Infinity
    arr.flatMap((item,index)=>{
        只能处理1层
    })
    arr.fill();往数组里面填充/替换,如果只填写一个参数全部替换为参数值
    arr.includes()   检测数组是否包含参数 ,参数2从第几位检索
 -->


<------                          

# 微信小程序项目
---
# 在微信小程序复制文本并打开其它购物小程序并搜索(JD);
<!-- ;获取用户粘贴文本 只要复制，可以在任何写该方法的小程序获取到 -->
wx.getClipboardData()

# 微信小程序跳转
<!-- 需要在app.json 配置 内容是待跳转小程序appid -->
navigateToMiniProgramAppIdList:[];

<!-- 写入需要跳转的方法 -->
navigateToMiniProgram({
    appid:'',
    path:'', 
    <!-- 页面路径加参数 -->
});
<!-- 获取某个小程序的appid
    如JD；JD商城右上角，点击小程序评分，更多信息
    微信公众平台 左上工具生成小程序码 填写appid => 获取更多页面路径=>输入一个访问人员的微信号码=>再次访问=>再点击有上三个点；
    获取参数，分享小程序，进入分享的小程序获取路径即可
 -->
 # 微信小程序分享朋友圈
 <!-- 是可以带参数 方便绑定关系 分销类的项目可以考虑进去-->
 <!-- 用法 这个方法微信文档上有详细  此方法建议写在 onshow -->
 wx.showShareMenu({
      withShareTicket: true,
      menus: ['shareAppMessage', 'shareTimeline'],
      success: (res) => {
        console.log(res)
      }
 });
 <!-- 此方法配合上面使用 当成函数方法 写入page方法里面即可  图标默认不写就是小程序头像-->
  onShareTimeline: function () {
    return {
        title: '分享名字',
        query: "pid=" + wx.getStorageSync('user_id'),
        imageUrl: ''
      }
  },
# 微信小程序坑点，项目问题 正在补充...

# 第一就是页面栈的问题 使用小程序wx.navigation 它会一直添加页面栈，直到加满不能点击跳转页面位置，停在当前页面
解决方法： 使用其它跳转方法,wx.rela... 看文档;

# 第二比较常见 小程序的时间转换格式 ios/android 正则不匹配 
解决方法 ： 安卓获取的时间格式是 - 连接 ：2020-09-01
           ios获取时间的格式是 / 连接 ：2020/09/01；
           new Date(date.replace(/-/g, '/') );

# 第三 textarea 的层级是最高的 （z-index）所以在遮罩层的地方打开遮罩层需要把textarea 隐藏掉

# 第四 https资源问题
    小程序所有的资源必须是安全的,如使用小程序自带的下载视频，图片，展示大图，测试小程序，前提是在https下才可以，否则会出现一些bug，运行失败


# JS H5 项目的问题 正在补充...

ios自带浏览器内核
在使用session 缓存的时候 location 像这种的ios浏览器不识别导致一些数据获取不到



# 使用a标签绑定事件关系
问题：点击a标签刷新页面，一直回退；
原因：herf属性 如果不处理会自己乱搞
解决：javascript:;



# 使用其它CDN 建议把cdn文件下载本地，否则用户需求量太大，每个用户进来一些都会请求cdn 导致页面卡顿，错过浏览程序黄金时段
如：vue,swiper,element,jq,axios



# 微信公众号开发
跟一般H5项目一样 但最终是运行在微信环境下面
需要满足微信的规则 读文档吧；
微信小程序的方法，公众号都可以使用 wx-js-sdk 配合使用 需要后台配合 读文档；


# H5上传文件，使用fromdata;
选择完文件，input 会有文件缓存，上传成功后删除

# 判断
false                true     
(100 == true ) == (1 == true); 返回 false
100 == true 等于两个不同的类型进行判断
1 == true true和false 和负数进行比较,会把true 隐式转换成1 false 隐式转换为0

# object 对象扩展学习
object 创建
<!-- 对象初始化,或对象字面量 ,以构造函数形式来调用-->
参数 {
    name:value
    ......
}
成对的名称(字符串)与值(任何值),其中名称通过冒号值分割
value 
任何值
<!-- 在javascript中,几乎所有的对象都是object类型的实例,它们都会从object.protitype继承属性和方法 -->
---
Object 构造函数的方法
Object.assing();
<-- 通过复制一个或多个对象来创建一个新的对象
     let obj = {name:1};
     let data = Object.assign({},data);
     alert(data);
     <-- 一个新的对象 
        参数 target 目标对象
             sources 源对象
             返回值目标对象,
        扩展深浅拷贝
        对象合并 若果有相同的属性会进行覆盖
        合并对象,目标对象也会改变
     -->

 -->
 # 待定....
 Object.create();
 <-- 
    方法创建一个新对象,使用现有的对象来提供新创建的对象的__proto__
  -->

Object.defineProperties()
<--
    方法直接在一个对象上定义行的属性或修改现有属性并返还该对象;
    Object.defineProperties(obj, props)
    参数 
    obj:在其上低音或修改属性的对象
    props: # 不理解
    var obj = {};
Object.defineProperties(obj, {
    'property1': {
        value: true,
        writable: true
    },
    'property2': {
        value: 'Hello',
        writable: false
    }
  
});
-->

Object.defineProperty()
<--
    方法会直接在一个对象上定义一个新属性
-->

Object.entries()
<-- 
    返回值是一个数组
    方法返回一个给对象自身可枚举属性的键值对数组,期排列与使用for...in 循环遍历改对象返回的顺序一直
 -->
 Object.freeze()
 <--
    返回值被冻结的对象
    冻结某个对象,一个对象被冻结再也不能被修改,冻结一个对象不能向这个对象添加新的属性,不能删除已有属性
    const obj = {
        prop:1
    };
    Object.freeze(obj);
    obj.prop = 2;
    console.log(obj.prop == 1,obj.prop == 2);
    冻结一个数组
    const arr = [0];
    Object.freeze(arr);
    arr[0] = 1;
    console.log(arr[0] == 1 , arr[0] == 2 );
    被冻结的对象是不可变的,但冻结对象是常量的话 == 浅冻结
    const obj = {
        a:{}
    };
    Object.freeze(obj)
    obj.a.value = 2;
    console.log(obj.a.value+'还是可以赋值成功')
 -->
 Object.fromEntries();
 <--
     方法把键值对列表转换为一个对象。
     const obj = new Map([
         [a,1],
         [b,2]
     ]);
     <-- 
        obj = {a==>1,b==>2}
      -->
     Object.fromEntries(obj);
     console.log(obj=={a:1,b:2})
-->

Object.is()
<-- 
     方法判断两个值是否为同一个值。
     返回值boolean
 -->

Object.keys(obj);
<-- 
    方法会返回一个由一个给定对象的自身可枚举属性组成的数组，数组中属性名的排列顺序和正常循环遍历该对象时返回的顺序一致 。
 -->
 Object.values()
<-- 
     方法返回一个给定对象自身的所有可枚举属性值的数组，值的顺序与使用for...in循环的顺序相同 ( 区别在于 for-in 循环枚举原型链中的属性 )。
 -->

# css transform
<-- 
    属性 rotate() 旋转角度 默认中心位置顺时针
    scale()放大缩小元素 若干只有一个值则宽高一起变化，两个值分别代表宽和高
    translate(x,y)移动元素位置
    skew(x,y)让元素倾斜
    transform-origin 改变元素变形原点
 -->

# css 瀑布布局
<-- 
    column css 属性
    父级添加
    column-count: 4;
    column-gap: 0;

  img 图片高度 auto 
 -->

