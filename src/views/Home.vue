<template>
  <div class="home">
    <van-swipe ref="lwswi" :autoplay="3000" @change="onChange" class="swi" :style="{width:'100%',height:((screen.width-25)*0.5187+'px')}" >
      <van-swipe-item v-for="(image, index) in images" :key="index">
        <div class='swi-item' >
          <img class="si-img" v-lazy="image" :style="{width:'100%',height:((screen.width-25)*0.5187+'px')}" />
        </div>
      </van-swipe-item>
      <div class="vsi-fixed" slot="indicator">
        <ul class="vsi">
          <li v-for="(image, index) in images" :key="index" :class="{'v-li':true,'active':index===current}" @click="clickto(index)"></li>
        </ul>
      </div>
    </van-swipe>
    <div>
      <div>
        <div class="lw-tab">
          <div :class="{'lt-item':true,active:active==0}" @click="activefn(0)">
            <img src="../assets/hot.png" alt="" class="li-icon">
            <span class="li-span">火热活动</span>
          </div>
          <div :class="{'lt-item':true,active:active==1}" @click="activefn(1)">
            <img src="../assets/history.png" alt="" class="li-icon">
            <span class="li-span">往期活动</span>
          </div>
        </div>
      </div>
      <van-swipe ref="lwtab" @change="tabChange" class="swi"  >
        <van-swipe-item v-for="(val,index) in tabitem" :key="index">
          <div class='tab-item'>
            <div
                    v-for="item in tablist"
                    :key="item"
                    class="ti-child"
            >
              <div class="tc-topic">
                <img class="si-img" v-lazy="'http://gzss.shengjinglvyou03.cn/cs/808/src/35.jpeg'" :style="{width:'100%',height:((screen.width-25)*0.5187+'px')}" />
              </div>
              <div class="tc-bottom">
                <p class="tc-title over2">[花萼子]放假哦挖掘法就偶尔就干了件佛龛就爱我耳机了</p>
                <p class="tc-time">
                  2019-09-29
                </p>
              </div>
            </div>
          </div>
        </van-swipe-item>

        <div slot="indicator">
        </div>
      </van-swipe>
    </div>
  </div>
</template>

<script>

// @ is an alias to /src
export default {
  name: 'home',
  data() {
    const screen=window.screen;
    return {
      tablist:[],
      tabitem:[
        {
          value:'火热活动',
          icon:'../assets/hot.png',
          data:[1,2,3]
        },
        {
          value:'往期活动',
          icon:'../assets/history.png',
          data:[1,2]
        }
      ],
      list: [1,2,3,4],
      loading: false,
      finished: false,
      loading1: false,
      finished1: false,
      screen,
      active:-1,
      current:0,
      images: [
        'http://gzss.shengjinglvyou03.cn/cs/808/src/38.jpeg',
        'http://gzss.shengjinglvyou03.cn/cs/808/src/35.jpeg'
      ]
    }
  },
  mounted(){
    this.tabChange(0);
  },
  methods:{
    activefn(ind){
      this.$refs['lwtab'].swipeTo(ind)
    },
    tabChange(e){
       this.active=e;
       this.tablist=this.tabitem[e].data;
    },
    onChange(e){
      this.current=e;
    },
    clickto(ind){
      this.$refs['lwswi'].swipeTo(ind)
    }
  }
}
</script>
<style lang="less" scoped>

  .over2{
    overflow:hidden;

    text-overflow:ellipsis;

    display:-webkit-box;

    -webkit-box-orient:vertical;

    -webkit-line-clamp:2;
  }
  ul,li{
    padding:0;
    margin:0;
  }
  .lt-item{
    display:flex;
    align-items:center;
  }
  .tc-title{
    text-align:left;
    font-size:15px;
    font-family:Source Han Sans CN;
    font-weight:600;
    color:rgba(33,33,33,1);
    line-height:24px;
  }
  .tc-time{
    font-size:13px;
    font-family:Source Han Sans CN;
    font-weight:400;
    color:rgba(168,171,175,1);
    text-align:right;
    line-height:24px;
  }
  .lw-tab{
    display:flex;
    align-items:center;
    justify-content:space-around;
    width:100%;
    height:50px;
    .active{
      .li-span{
        color:#0D83DD;
      }
    }
    .li-icon{
      width:17px;
      height:19px;
    }
    .li-span{
      font-size:16px;
      color:#A8ABAF;
      padding:0 5px;

    }
  }
  .si-img{
    border-radius:6px;
    overflow:hidden;
  }
  .vsi-fixed{
    position:absolute;
    bottom:0;
    left:0;
    right:0;
    width:100%;
    display:flex;
    justify-content:center;
    align-items:center;
    height:40px;
    .vsi{
      display:flex;
      align-items:center;
      justify-content:center;
      .v-li{
        margin:5px;
        width:8px;
        height:8px;
        border-radius:16px;
        background-color:#fff;
        opacity:.5;
        &.active{
          width:20px;
          opacity:1;
        }
      }
    }
  }
  .swi{
    position:relative;
  }
  .home{
    padding:12.5px;
  }
</style>
