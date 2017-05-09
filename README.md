# MusicCanvas

Use AudioContext to Analysis of the Audio data to synchronize the canvas

## <a href="http://lkkchen.cn:3030/login" onclick="javascript:return false">DEMO URL</a>

![Image text](https://github.com/Studying-Man/MusicCanvas/blob/master/demo.png?raw=true)


# How to Use

#1 Include the JS in HTML
#2 Give a box for the MusicCanvas, like this:
```html
<input type="file" id="ff" accept="audio/mpeg">
<section id="myAcBox" style="margin-left: 200px">

</section>
```

#3 Then write your JS to init the MusicCanvas, like this:

```js
var MC = new initMusicCanvas().init('myAcBox',{needPreNext:true});

//load Music by Select local file, Parameter is input tag id
var musicCanvas = MC.bySelectFile('ff');

//load Music by ArrayBuffer
var musicCanvas = MC.bySelectFile(ArrayBuffer);

```
## The musicCanvas has some attributes:

### musicCanvas.ctx
#### the context of canvas,use it to draw

### musicCanvas.canvas
#### the element of canvas

### musicCanvas.audioApi
#### audioApi has some Events:
```js
musicCanvas.audioApi.addEventListener('loading',function () {
    //when decoding the mp3 or ArrayBuffer
});
musicCanvas.audioApi.addEventListener('playing',function () {
    //when playing
});
musicCanvas.audioApi.addEventListener('ended',function () {
    //when music ended
});
```

### musicCanvas.drawing
#### It's has a Event: onDrawing, All you drawing will write in this Event Callback Function
#### The callback provide a Parameter of Array, the Array has the realtime audio frequency data ,and you can use these data to painting
#### Like this:
```js
var musicCanvas = new initMusicCanvas().init('myAcBox',{needPreNext:true}).bySelectFile('ff');
var canvas = musicCanvas.canvas;
var ctx = musicCanvas.ctx;

musicCanvas.audioApi.addEventListener('loading',function () {
    canvas.width=720;
    canvas.height=405;
});

musicCanvas.drawing.addEventListener('onDrawing',function (dataArray) {
    var cwidth = canvas.width,cheight = canvas.height;
    var mid=0,head=0;
    var len = dataArray.length
    for(var j=600;j<len;j++){
        mid=mid+dataArray[j]
    }
    for(var k=0;k<20;k++){
        head=head+dataArray[k]
    }
    ctx.beginPath();
    ctx.fillStyle='#fee';
    ctx.arc(cwidth/4,cheight/2,head/20*size,0,Math.PI*2);
    ctx.arc(cwidth/2,cheight/2,mid/623*size*3,0,Math.PI*2);
    ctx.closePath();
    ctx.fill();
})
```
![Image text](https://github.com/Studying-Man/MusicCanvas/blob/master/demo2.png?raw=true)

# More Functions Coming Soon~
## Some Problems:
### Ajax file too slowly, use the stream data will be better
### I want to make the drawing is complete control by users, or they can painting by mouse, Not the code we has write done


















