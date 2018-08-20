# list-img-suit 移动端图片列表自适应

移动端常用图片列表自适应
解决了以往的不同尺寸屏幕的兼容性，保证图片盒子为正方形
兼用了不同尺寸比例的图片正常输出，类似于朋友圈的图片列表

代码：
css --- 
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
img {
  display: block
}

.list-img-suit {
  display: flex;
  flex-wrap: wrap;
  padding: 15px;
}
.list-img-suit .item {
  display: flex;
  justify-content: center;
  align-items: center;
  width: 31%;
  height: 110px;
  overflow: hidden;
  margin-left: 3.5%;
  margin-bottom: 3.5%;
}
.list-img-suit .item:nth-child(3n+1) {
  margin-left: 0;
}


html ---
  <div class="list-img-suit" id="imgList">
        <div class="item">
            <img src="https://timgsa.baidu.com/timg?image&quality=80&size=b9999_10000&sec=1535377981&di=a62a249877793453a8d790a0a4341862&imgtype=jpg&er=1&src=http%3A%2F%2Fpic.qiantucdn.com%2F58pic%2F21%2F42%2F11%2F59A58PICcB5_1024.jpg" id="img" class="item-img" alt="">
        </div>
        <div class="item">
            <img src="https://timgsa.baidu.com/timg?image&quality=80&size=b9999_10000&sec=1534783219762&di=3676493e4cd1c7dd169b129a619d8b78&imgtype=0&src=http%3A%2F%2Fimg.article.pchome.net%2F00%2F43%2F87%2F47%2Fpic_lib%2Fs960x639%2Fkuanping025s960x639.jpg" class="item-img" alt="">
        </div>
        <div class="item">
            <img src="https://timgsa.baidu.com/timg?image&quality=80&size=b9999_10000&sec=1534783152941&di=863b2002d6b215a7f31ca5197a74673d&imgtype=0&src=http%3A%2F%2Fc.hiphotos.baidu.com%2Fimage%2Fpic%2Fitem%2Ff636afc379310a5531e980ccba4543a98226103c.jpg" class="item-img" alt="">
        </div>
        <div class="item">
            <img src="https://timgsa.baidu.com/timg?image&quality=80&size=b9999_10000&sec=1534783131991&di=e82defda9a6b48baaf21cf59959c8aa3&imgtype=0&src=http%3A%2F%2Fh.hiphotos.baidu.com%2Fimage%2Fpic%2Fitem%2Fb21c8701a18b87d600b87f290a0828381f30fd0a.jpg" class="item-img" alt="">
        </div>
    </div>


js ---
  // 当页面载入完毕后执行，注：为了能正常获取到img尺寸的写法
    window.onload = function () {
        var id = 'imgList' // 模块id
        boxImgSuit(id)
    };
    // 图片自适应盒子，参数为列表id
    function boxImgSuit(id) {
        var img = document.getElementById(id).getElementsByClassName('item') // 获取doc
        for (var i = 0; i < img.length; i++) {
            var imgHtml = img[i].getElementsByClassName('item-img')[0] // 获取到图片
            var imgHeight = imgHtml.height // 获取到图片高度
            var imgWidth = imgHtml.width // 获取图片宽度
            img[i].style.height = img[i].offsetWidth + 'px' // 配置盒子高度
            var itemHeight = img[i].offsetHeight // 获取图片盒子的高度
            var itemWidth = img[i].offsetWidth // 获取图片盒子宽度
            if (imgWidth > imgHeight) { // 判断图片宽度是否大于高度
                imgHtml.height = itemHeight // 给图片高度 100%
            } else if (imgWidth < imgHeight) { // 判断图片宽度是否小于高度
                imgHtml.width = itemWidth // 给图片宽度 100%
            } else { // 图片是正方形
                imgHtml.height = itemHeight // 给图片高度 100%
                imgHtml.width = itemWidth // 给图片宽度 100%
            }
        }
        // 监听窗口变化
        window.onresize = function () {
            boxImgSuit(id)
        }
    }
