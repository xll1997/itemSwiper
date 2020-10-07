<!--
 * @Descripttion: 轮播
 * @version: 
 * @Date: 2020-08-31 
-->
<!-- 
  使用方法：
  caseSwiperData: Array
 -->
<template>
  <div>
    <div class="con clearfix">
      <div class="flImg fl">
        <img
          src="@/assets/authDetailsXq/caseImg.png"
          alt=""
        />
      </div>
      <div class="swiper fr">
        <div class="frTop">
          <v-touch
            v-on:swipeleft="onSwipeLeft"
            v-on:swiperight="onSwipeRight"
            tag="div"
          >
            <div class="conLi">
              <ul>
                <li
                  @touchend="touchEnd(index)"
                  :class="{ active: isActiveConIndex === index }"
                  v-for="(item, index) in caseSwiperData[caseSwiperIndex]"
                >
                  <i></i> <span>{{ item.time }}</span> {{ item.con }}
                </li>
              </ul>
            </div>
          </v-touch>
        </div>
        <div class="frBottom clearfix">
          <div class="fl"><span>MORE</span></div>
          <div class="fr">
            <i
              @touchend="touchEndLi(Iindex)"
              :class="{ active: caseSwiperIndex === Iindex }"
              v-for="(Liitem, Iindex) in caseSwiperData.length"
            >
              <div class="outer one"></div>
              <div class="outer two"></div>
              <div class="outer three"></div>
              <div class="outer fore"></div>
              <b></b>
            </i>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  components: {},
  props: {
    caseSwiperData: Array
  },
  data() {
    return {
      caseSwiperIndex: 0, // 轮播索引
      isActiveConIndex: 0, // 轮播内容索引
      timer: null //定时器
    }
  },
  computed: {
    //上一张
    prevIndex() {
      if (this.caseSwiperIndex == 0) {
        return this.caseSwiperData.length - 1
      } else {
        return this.caseSwiperIndex - 1
      }
    },
    //下一张
    nextIndex() {
      if (this.caseSwiperIndex == this.caseSwiperData.length - 1) {
        return 0
      } else {
        return this.caseSwiperIndex + 1
      }
    }
  },
  created() {},
  mounted() {
    this.runInv()
  },
  methods: {
    gotoPage(index) {
      this.caseSwiperIndex = index
    },
    //定时器
    runInv() {
      this.timer = setInterval(() => {
        this.gotoPage(this.nextIndex)
      }, 3000)
    },
    // 轮播内容
    touchEnd(index) {
      this.isActiveConIndex = index
      // clearInterval(this.timer) //清除自动轮播
    },
    // 轮播小点
    touchEndLi(index) {
      this.caseSwiperIndex = index
    },
    onSwipeLeft() {
      //左滑动
      // console.log('左滑动')
      this.gotoPage(this.nextIndex)
    },
    onSwipeRight() {
      //右滑动
      // console.log('右滑动')
      this.gotoPage(this.prevIndex)
    }
  }
}
</script>

<style lang="less" scoped>
@number: 20;
@size: 750px / @number;
div {
   width: 100%;
}
.con {
  display: flex;
  height: 100%;

  .flImg {
    width: 265rem / @size;
    // height: 175rem / @size;
    height: 300rem / @size;
    img {
      width: 100%;
      height: 100%;
      // height: 380rem / @size;
      border-radius: 10rem / @size;
      box-shadow: 0 0 10rem / @size rgba(90, 99, 162, 0.5);
    }
  }
  .swiper {
    position: relative;
    flex: 1;
    // height: 100%;
    // width: 100%;
    padding-left: 10rem / @size;
    // box-sizing: border-box;
    // background-color: #f00;
    .frTop {
      position: absolute;
      top: 0;
      font-size: 10rem / @size;
      // background-color: #ff0;
      .conLi {
        li {
          position: relative;
          border-left: 1px solid #053c81;
          // padding-left: 15rem / @size;
          padding-bottom: 10rem / @size;
          color: #666666;
          span {
            margin: 0 10rem / @size;
          }
          i {
            position: absolute;
            left: -6rem / @size;
            top: 50%;
            transform: translate(-15%, -80%);
            display: block;
            width: 10rem / @size;
            height: 10rem / @size;
            border-radius: 50%;
            background-color: #fff;
            border: 1px solid #053c81;
          }
        }
        .active {
          color: #053c81;
          i {
            background-color: #053c81;
          }
        }
      }
    }
    .frBottom {
      position: absolute;
      bottom: 0;
      // width: 90%;
      // background-color: #f00;
      // box-sizing: border-box;
      color: #053c81;
      display: flex;
      .fl {
        // float: left;
        display: inline-block;
        // background-color: #ff0;
        text-align: left;
        height: 25rem / @size;
        font-size: 25rem / @size;
        span {
          position: relative;
          bottom: -10rem / @size;
          padding-left: 25rem / @size;
          // margin: auto 0;
        }
        // line-height: 40rem / @size;
      }
      .fr {
        // float: right;
        display: inline-block;
        // background-color: #f00;
        i {
          position: relative;
          display: inline-block;
          width: 25rem / @size;
          height: 25rem / @size;
          margin-left: 10rem / @size;
          border: 2px solid #666666;
          border-radius: 50%;
          .outer {
            position: absolute;
            left: -5rem / @size;
            top: -8rem / @size;
            width: 40rem / @size;
            height: 40rem / @size;
            transform: rotate(0deg);
            clip: rect(
              0,
              0.544rem,
              0.544rem,
              0
            ); /* 这个clip属性用来绘制半圆，在clip的rect范围内的内容显示出来，使用clip属性，元素必须是absolute的 */
            border-radius: 20rem / @size;
            background-color: #fff;
            // -webkit-animation: an1 2s infinite linear;
          }

          .two {
            position: absolute;
            left: -5rem / @size;
            bottom: -8rem / @size;
            transform: rotate(-180deg);
            background-color: #fff;
            // -webkit-animation: an2 2s infinite linear;
          }
          .three {
            position: absolute;
            left: -5rem / @size;
            bottom: -8rem / @size;
            transform: rotate(-90deg);
            background-color: #fff;
            // -webkit-animation: an2 2s infinite linear;
          }
          .fore {
            position: absolute;
            left: -5rem / @size;
            top: -8rem / @size;
            transform: rotate(90deg);
            background-color: #fff;
            // -webkit-animation: an2 2s infinite linear;
          }

          b {
            position: absolute;
            left: 50%;
            top: 50%;
            transform: translate(-50%, -50%);
            display: inline-block;
            width: 8rem / @size;
            height: 8rem / @size;
            border-radius: 50%;
            background-color: #000;
          }
        }

        // 轮播小点动画
        @-webkit-keyframes an1 {
          0% {
            transform: rotate(0deg);
            // background-color: #fff;
          }
          90% {
            // background-color: #fff;
          }
          100% {
            transform: rotate(90deg);
            background-color: transparent;
          }
        }

        @-webkit-keyframes an2 {
          0% {
            transform: rotate(-180deg);
          }
          90% {
            background-color: #fff;
          }
          100% {
            transform: rotate(-90deg);
            background-color: transparent;
          }
        }

        @-webkit-keyframes an3 {
          0% {
            transform: rotate(-90deg);
          }
          90% {
            background-color: #fff;
          }
          100% {
            transform: rotate(-0deg);
            background-color: transparent;
          }
        }

        @-webkit-keyframes an4 {
          0% {
            transform: rotate(90deg);
          }
          90% {
            background-color: #fff;
          }
          100% {
            transform: rotate(180deg);
            background-color: transparent;
          }
        }

        .active {
          // 第四个
          .one {
            -webkit-animation: an1 2.2s;
            animation-delay: 2s;
            -webkit-animation-delay: 2s; /* Safari 和 Chrome */
            animation-fill-mode: forwards;
          }
          // 第二个
          .two {
            -webkit-animation: an2 1.5s;
            animation-delay: 1s;
            -webkit-animation-delay: 1s; /* Safari 和 Chrome */
            animation-fill-mode: forwards;
          }
          // 第三个
          .three {
            -webkit-animation: an3 1s;
            animation-delay: 1s;
            -webkit-animation-delay: 1s; /* Safari 和 Chrome */
            animation-fill-mode: forwards;
          }
          // 第一个
          .fore {
            -webkit-animation: an4 0.5s;
            animation-fill-mode: forwards;
          }
          b {
            width: 0;
            height: 0;
            border: 8rem / @size solid;
            border-radius: 0%;
            transform: translate(-10%, -50%);
            background-color: transparent;
            border-color: transparent transparent transparent black;
          }
        }
      }
    }
  }
}
</style>
