### 九宫格

##设计要求

每次随机生成3个颜色

点击按钮一，使3个颜色随机上到九宫格的3个格子上，每秒变化一次

点击按钮二，九宫格复原

##设计思想

随机获取方块位置
function shine() {//获取随机方块
    var box1 = Math.floor(Math.random() * box.length);
    var box2 = Math.floor(Math.random() * box.length);
    var box3 = Math.floor(Math.random() * box.length);
    //判断方块是否是同一个
    if (box1==box2) {
        box1=Math.floor(Math.random() * box.length);
    } else if(box2==box3){
        box2=Math.floor(Math.random() * box.length);
    }else if(box1==box3){
        box3=Math.floor(Math.random() * box.length);
    }
    //颜色赋值
    box[box1].style.backgroundColor = 'rgb' + colors();
    box[box2].style.backgroundColor = 'rgb' + colors();
    box[box3].style.backgroundColor = 'rgb' + colors();
}

随机获取颜色
function colors() {//随机获取颜色
    var rgb;
    var r = Math.floor(Math.random() * 256);
    var g = Math.floor(Math.random() * 256);
    var b = Math.floor(Math.random() * 256);
    rgb = '(' + r + ',' + g + ',' + b + ')';
    return rgb;
}


将颜色赋值到方块上
    box[box1].style.backgroundColor = 'rgb' + colors();
    box[box2].style.backgroundColor = 'rgb' + colors();
    box[box3].style.backgroundColor = 'rgb' + colors();


点击事件设置：点击按钮一，使其变化
  function start() {//开始
    clearInterval(time);//结束之前的定时器
    time = setInterval(function () {
        //循环获取颜色
        for (var i = 0; i < box.length; i++) {
            box[i].style.backgroundColor = '';
        }
        shine();
    }, 2000);
}
              
             点击按钮二，停止变化
  function stop() {//结束
    clearInterval(time);
    for (var i = 0; i < box.length; i++) {
        box[i].style.backgroundColor = '';
    }
}  
**注意**：使用定时器要即使释放，以免形成内存泄漏
