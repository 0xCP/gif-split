<template>
  <div class='title'>在线GIF图片帧拆分工具</div>
  <div class=main>
    <div class='drag-wrapper'>111111</div>
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
    width: 90%;
    height: 200px;
    border: 3px dotted #cccccc;
  }
</style>