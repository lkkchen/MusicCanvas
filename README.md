# MusicCanvas

Use AudioContext to Analysis of the Audio data to synchronize the canvas

## <a href="http://lkkchen.cn:3030/login" onclick="javascript:return false">DEMO URL</a>

![Image text](https://github.com/Studying-Man/MusicCanvas/blob/master/demo.png?raw=true)
# More Functions Coming Soon~

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
# The musicCanvas is a Object,there are some attributes of this:

##musicCanvas.ctx
#### the context of canvas,use it to draw

##musicCanvas.canvas
#### the element of canvas

##musicCanvas.drawing
### It's a Object,is has Event: onDrawing,All you drawing will write in this Event Function
#### Like this:
```js

```
#4 Include the JS in HTML




















