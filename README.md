# list-img-suit 移动端图片列表自适应

移动端常用图片列表自适应
解决了以往的不同尺寸屏幕的兼容性，保证图片盒子为正方形
兼用了不同尺寸比例的图片正常输出，类似于朋友圈的图片列表
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
