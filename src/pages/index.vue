<template>
    <div>
         <div class="con_item case">
        <CaseSwiper :caseSwiperData="caseSwiperData" />
        </div>
    </div>
</template>

<script>
import CaseSwiper from '../components/caseSwiper'
export default {
    created(){},
    data(){
        return {
       // 检测案例轮播数据
      caseSwiperData: [
        [
          {
            time: '2019-11-10',
            con: '智能机器人冬季大赛开始'
          },
          {
            time: '2019-11-10',
            con: '智能机器人冬季大赛开始'
          },
          {
            time: '2019-11-10',
            con: '智能机器人冬季大赛开始'
          }
        ],
        [
          {
            time: '2019-12-10',
            con: '智能机器人冬季大赛开始'
          },
          {
            time: '2019-12-10',
            con: '智能机器人冬季大赛开始'
          },
          {
            time: '2019-12-10',
            con: '智能机器人冬季大赛开始'
          },
          {
            time: '2019-12-10',
            con: '智能机器人冬季大赛开始'
          }
        ]
      ],
        }
    },
    methods:{},
    components:{
        CaseSwiper
    },
    filters:{},
}
</script>

<style lang="less" scoped>
@number: 20;
@size: 750px / @number;
.con_item {
    width: 100%;
    padding-left: 24rem / @size;
    padding-right: 24rem / @size;
    box-sizing: border-box;
    }
    .case {
    margin-top: 21rem / @size;
    padding-bottom: 23rem / @size;
    background-color: #fff;
  }
</style>
