<template>
  <div class="home">
    <img
      class="img imgLove"
      src="../../assets/love.gif"
    />
    <span>{{text}}</span>

    <div
      class="box scale"
      id="box"
      v-if="flag"
    >
      <img
        class="imgBox"
        src="../../assets/1.gif"
        alt=""
      >
    </div>
  </div>
</template>

<script>
export default {
  data: () => ({
    text: '',
    flag: false,
    timer: null
  }),
  created () {
    this.start()
  },
  methods: {
    start () {
      // 创建数组
      var arr = []
      var str = '我就是那个普通话不标准黄金身高1.70m的的骗花狂魔fly老师！'
      arr.push(str)
      var newStr = arr.join('')
      var newArr = newStr.split('')
      var i = 0
      this.timer = setInterval(() => {
        if (i === newStr.length) {
          clearInterval(this.timer)
          this.flag = !this.flag
        } else {
          this.text += newArr[i]
          i++
        }
      }, 100)
    }
  }
}
</script>

<style>
.img {
  width: 100rpx;
  height: 100rpx;
}
.imgBox {
  width:100%;
  height: 100%;
  position: absolute;
  z-index: 520;
  transform: rotate(45deg);
  display: block;
}
.box {
  width: 200rpx;
  height: 200rpx;
  background: pink;
  transform: rotate(-45deg);
  position: absolute;
  top: 50%;
  left: 40%;
}
.box:before {
  content: "";
  width: 200rpx;
  height: 200rpx;
  background: pink;
  display: block;
  border-radius: 50%;
  position: absolute;
  top: -100rpx;
  left: 0;
}

.box:after {
  content: "";
  width: 200rpx;
  height: 200rpx;
  background: pink;
  display: block;
  border-radius: 50%;
  position: absolute; /*绝对定位*/
  top: 0;
  left: 100rpx;
}

@-webkit-keyframes ide {
  0% {
    -webkit-transform: scale(1) rotate(-45deg);
  }

  50% {
    -webkit-transform: scale(1.5) rotate(-45deg);
  }
  100% {
    -webkit-transform: scale(1) rotate(-45deg);
  }
}

.scale {
  -webkit-animation: ide 1.2s linear infinite;
}
</style>