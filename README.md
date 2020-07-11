# transform3D
## 三要素
### perspective  
  景深，3D变换中模拟我们的视角，元素在 Z轴 的距离
### transform-style: perserve-3d
  元素3D变换时，是否保留子元素的3D变换（元素内部是否建成3D空间）。
### 变换函数
  rotate3d()  translate3d() scale3d() （skew没有Z轴变换）
  
## 其他
### transform-origin: center center 0;
3D原点或基点默认值 center center 0 对应 x轴  y轴  z轴


 /* backface-visibility: visible|hidden; */
 
html结构：
<pre>
    <div id="wrap">
        <div class="box">
            <div>1</div>
            <div>2</div>
            <div>3</div>
            <div>4</div>
            <div>5</div>
            <div>6</div>
        </div>
    </div>
</pre>
 样式：
 <style>
        @keyframes rotate {
            from {
                transform: rotateY(0deg);
            }

            to {
                transform: rotateY(360deg);
            }
        }

        #wrap {
            position: relative;
            width: 200px;
            height: 200px;
            padding: 200px;
            font: 120px/200px "微软雅黑";
            border: 1px solid black;
            color: blanchedalmond;
            margin: 100px auto;
            font-weight: 600;
            /* 景深，模拟我们的视角，元素在z轴的距离 */
            /* perspective一般放在3d整体的父元素上，作为我们的视角 */
            perspective: 400px;

        }

        .box {
            position: relative;
            width: 200px;
            height: 200px;
            animation: 10s rotate infinite linear;
            transform-style: preserve-3d;
            /* 围绕中心点旋转 */
            transform-origin: center center -100px;
            /* transform-origin: cneter center 0;  默认情形下，围绕面3旋转 */

        }

        .box div {
            position: absolute;
            height: 200px;
            width: 200px;
            text-align: center;
            border: 1px solid black;
            opacity: 0.5;
        }

        .box div:nth-child(1) {
            left: 0px;
            top: -200px;
            border-color: blue;
            background-color: blue;
            transform-origin: bottom;
            transform: rotateX(90deg);
        }

        .box div:nth-child(2) {
            left: -200px;
            top: 0px;
            border-color: blueviolet;
            background-color: blueviolet;
            transform-origin: right;
            transform: rotateY(-90deg);
        }

        .box div:nth-child(3) {
            left: 0;
            top: 0;
            border-color: brown;
            background-color: brown;
            /* transform: rotateX(-90deg);
            transform-origin: top center; */
        }

        .box div:nth-child(4) {
            left: 200px;
            top: 0px;
            border-color: burlywood;
            background-color: burlywood;
            transform-origin: left;
            transform: rotateY(90deg);
        }

        .box div:nth-child(5) {
            left: 0px;
            top: 200px;
            border-color: cadetblue;
            background-color: cadetblue;
            transform-origin: top;
            transform: rotateX(-90deg)
        }

        .box div:nth-child(6) {
            left: 0px;
            top: 0px;
            border-color: chartreuse;
            background-color: chartreuse;
            /* 面3的对面，z轴上位移； 旋转180deg，从外表面看文字是正的 */
            transform: translateZ(-200px) rotateY(180deg);
        }
    </style>

