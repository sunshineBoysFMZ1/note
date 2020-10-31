# note
工作学习笔记记录
# es6 class apply call 
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

<------                          