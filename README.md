# extract-video-cover
> js提取视频当前帧作为封面

## 用法
```html
// html
<video id="video" src="./video.ogv" controls></video>
<button id="output">截取当前帧</button>
```
```js
// js
(function(){
        var video, output;
        var scale = 0.5; // 缩放图片
        var initialize = function() {
            output = document.getElementById("output");
            video = document.getElementById("video");
            output.addEventListener('click',captureImage);
        };

        var captureImage = function() {
            var canvas = document.createElement("canvas");
            canvas.width = video.videoWidth * scale;
            canvas.height = video.videoHeight * scale;
            canvas.getContext('2d').drawImage(video, 0, 0, canvas.width, canvas.height);

            var img = document.createElement("img");
            img.src = canvas.toDataURL("image/png");

            output.appendChild(img);
        };

        initialize();
    })();
```
