<template>
  <div class='title'>在线GIF图片帧拆分工具</div>
  <div class=main>
    <div class='drag-wrapper'>
      <input type="file" @change='uploadImg($event)' ref='img' style="opacity: 0; width: 100%; height: 100%">
    </div>
    <!-- <img v-if='imgSrc' :src='imgSrc' id='img1' key="" style='width: 100%; height: 100%'/> -->
    <!-- <img src="./1.gif" alt="" ref='img1' id='img1' style="height: 100px;"> -->
    <div class='desc' id='desc'>选择GIF图像后工具将自动将GIF图像拆分成每一帧静态图片</div>
    <div class='button' @click="test">举个例子</div>
      <div v-for="item in imgList" :key="item">
    <img :src="item" />
      </div>
  </div>
</template>
<script>
  import SuperGif from 'libgif';

  export default {
    name: 'Index',
    data() {
      return {
        imgList: [],
      }
    },
    methods: {
      onDrag(e) {
        e.stopPropagation()
        e.preventDefault()
      },
      onDrop(e) {
        e.stopPropagation()
        e.preventDefault()
        let files = e.dataTransfer.files
        if (files.length) {
          this.uploadImg(files[0])
        }
      },
      uploadImg(e) {
        let imgfile = this.$refs.img;
        let file = imgfile.files[0];
        console.log(e)
        console.log(file)
        this.imgSrc = window.URL.createObjectURL(file);
        // setTimeout(() => {
        //   this.pre_load_gif()
        // }, 1500)
        // this.pre_load_gif(this.imgSrc)
        let newDiv = document.createElement('img')
        newDiv.src = this.imgSrc
        newDiv.id = 'img1'
        let a = document.getElementById('desc')
        a.appendChild(newDiv)
        this.pre_load_gif(newDiv)

      },
      test() {
        let a = document.getElementById('img1')
        this.pre_load_gif(a)
      },
      pre_load_gif(gif_source) {
        console.log(111)
        // let gif_source = document.getElementById('img1');
        // 新建gif实例
        var rub = new SuperGif({
          gif: gif_source,
        });
        console.log(rub.get_length())
        rub.load(() => {
          // let frame_list = rub.get_frames()
          for (let i = 0; i < rub.get_length(); i++) {
            rub.move_to(i)
            let canvas = rub.get_canvas()
            let dataURL = canvas.toDataURL('image/png')
            // 将每一帧的canvas转换成file对象
            // let cur_file = this.convertCanvasToImage(rub.get_canvas(), gif_source.name.replace('.gif', '') + `-${i}`)
            // console.log(frame_list[i])
            this.imgList.push(dataURL)
          }


          //   let cur_file = this.convertCanvasToImage(rub.get_canvas(), gif_source.name.replace('.gif', '') +
          //     `-${i}`)
          //   img_list.push({
          //     file_name: cur_file.name,
          //     url: URL.createObjectURL(cur_file),
          //     file: cur_file,
          //   })
          // }
          // this.img_list = img_list
        });
      },
      // 将canvas转换成file对象
    convertCanvasToImage(canvas, filename) {
    return this.dataURLtoFile(canvas.toDataURL('image/png'), filename);
},
dataURLtoFile(dataurl, filename) {
    const arr = dataurl.split(',');
    const mime = arr[0].match(/:(.*?);/)[1];
    const bstr = atob(arr[1]);
    var n = bstr.length;
    const u8arr = new Uint8Array(n);
    while (n--) {
        u8arr[n] = bstr.charCodeAt(n);
    }
    return new File([u8arr], filename, {type:mime});
},
    }
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