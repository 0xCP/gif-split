<template>
  <div class='title'>在线GIF图片帧拆分工具</div>
  <div class=main>
    <div class='drag-wrapper'>111111</div>
    <div class='desc'>选择GIF图像后工具将自动将GIF图像拆分成每一帧静态图片</div>
    <div class='button'>举个例子</div>
  </div>
</template>
<script>
  export default {
    name: 'Index',
  }
</script>
<style scoped>
  .title {
    font-size: 24px;
  }

  .main {
    margin: 100px 0 0 0;
    width: 60vw;
    min-height: 300px;
    display: flex;
    flex-direction: column;
    justify-content: flex-start;
    align-items: center;
    border-radius: 0px;
    background: #ffffff;
    box-shadow: 26px 26px 52px #d9d9d9,
      -26px -26px 52px #ffffff;
  }

  .drag-wrapper {
    margin: 50px 0 0 0;
    width: 90%;
    height: 200px;
    border: 3px dotted #cccccc;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
  }

  .desc {
    margin: 20px 0 0 0;
  }

  .button {
    margin: 20px 0 20px 0;
    background-color: aquamarine;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    width: 200px;
    height: 30px;
  }
</style>