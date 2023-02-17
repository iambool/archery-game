<template>
<div></div>
</template>

<script setup>
import * as PIXI from 'pixi.js'

function Random(min, max) {
    return Math.round(Math.random() * (max - min)) + min;
}
// 定义一些常量
// 左右两边柱子的x中心坐标
const leftStageCenter = window.innerWidth / 10;
// const rightStageCenter = window.innerWidth / 5 * 4;

// 站台常量
const stageWidth = 120; // 站台横向长度
const stageBarWidth = 10; // 站台支柱粗细
const stageColor = 0x333; // 站台颜色

// 创建个画布
const app = new PIXI.Application({
  width: window.innerWidth,
  height: window.innerHeight,
  backgroundColor: 0xfff2d1,
  resolution: window.devicePixelRatio || 1
});
document.body.appendChild(app.view);

// 来个容器
const container = new PIXI.Container();
app.stage.addChild(container);

// 左边站台 - 横向
const stageLeft = new PIXI.Graphics();
stageLeft.beginFill(stageColor);
const leftStageHeight = Random(400, 600); // 站台高度，也是人站的高度
stageLeft.drawRect(leftStageCenter - stageWidth/2, leftStageHeight, stageWidth, stageBarWidth);
stageLeft.endFill();
container.addChild(stageLeft);

// 左边站台 - 纵向
const stageLeftBar = new PIXI.Graphics();
stageLeftBar.beginFill(stageColor);
stageLeftBar.drawRect(leftStageCenter - stageBarWidth/2, leftStageHeight, stageBarWidth, window.innerHeight);
stageLeftBar.endFill();
container.addChild(stageLeftBar);



// 把咱们那基础图加进来
const baseTexture = PIXI.BaseTexture.from('./IMG_0067.PNG');

// 小人腿拿出来
const legsPic = new PIXI.Texture(baseTexture, new PIXI.Rectangle(120, 262, 110, 120))
const legs = new PIXI.Sprite(legsPic);
//legs.visible = false;
container.addChild(legs);



</script>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

canvas {
  width: 100vw;
  height: 100vh;
  position: fixed;
  top: 0;
  left: 0;
}
</style>
