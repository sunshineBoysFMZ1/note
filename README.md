
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
结构赋值
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
展开运算符
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
set or map
<!-- 构造函数，用来构建某一类的对象 对象的实列话 -->
<!-- 参数可以是数组,进行自动去重 -->
<!-- set 属性 
    size(保留值的个数==length)
    clear()清空返回undefined;
    delete()删除某项,参数不是下标,参数是value(要删除的数值),返回值true/false,删除成功true
    add(),添加,也会自动去重,如果存在不在显示
    has(),查看值是否存在 返回true/false
    -->
let arr  = [1,2,3,4,1];
let s = new Set(arr);
arr = [...s];

<!-- Map 参数不能是对象,没有迭代 -->
<!-- Map属性
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



# object 对象扩展学习
object 创建