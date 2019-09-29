<template>
  <div class="home">
    <div>
      <div class="my-head">
        <div class="mh-bg" :style="{width:'100%',height:(screen.width*0.469)+'px'}">
          <div class="flex-top">
            <div class="ft-text">我的报名</div>
          </div>
          <div class="flex-bottom">
            <div class="mb-left">
              <img src="../assets/logo.png" alt="" class="ml-icon">
              <span class="mi-name">Gemini</span>
            </div>
            <div class="mb-right">
              <div class="mr-btn">已报名活动：10</div>
            </div>
          </div>
        </div>
      </div>
      <div class="my-body">
        <div class="mb-h">
          <div class="m-h-item mhi-l" :style="{color:active==0?'#0D83DC':''}" @click="set_cur(0)">
            待审核
          </div>
          <div class="m-h-item mhi-i" :style="{color:active==1?'#0D83DC':''}"  @click="set_cur(1)">
            审核通过
          </div>
          <div class="m-h-item mhi-r" :style="{color:active==2?'#0D83DC':''}"  @click="set_cur(2)">
            审核失败
          </div>
        </div>

        <van-swipe ref="lwtab" @change="tabChange" class="data-swip"  >
          <van-swipe-item v-for="(val,index) in tabitem" :key="index" class="ds-item">

            <div class="di-out">
              <div class="di-scroll">
                <div class="di-in">
                  <div class="di-li shadow2" v-for="(item,ind) in tablist" :key="ind">
                    <div class="dl-con">
                      <div class="dl-left">
                        <img class="dl-icon" src="https://happyhn.gdtengnan.com/Public/qimg/small_haibao2.jpg" />
                      </div>
                      <div class="dl-right">
                        <div class="dr-text over2">
                          【活动】三亚过急急急急啊放假啊来我家附件客户反馈啊放假啊来我家附件客户反馈
                        </div>
                        <div class="dr-time">
                          报名时间：2019.0907 03:33:22
                        </div>
                      </div>
                    </div>
                    <div class="dl-btns">
                      <button class="dl-btn orange" v-show="index==2">重新报名</button>
                    </div>
                  </div>
                </div>
              </div>
            </div>
          </van-swipe-item>

          <div slot="indicator">
          </div>
        </van-swipe>
      </div>
    </div>

  </div>
</template>

<script>
  // @ is an alias to /src
  export default {
    name: 'about',
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
          },
          {
            value:'往期活动',
            icon:'../assets/history.png',
            data:[1]
          }
        ],
        list: [1,2,3,4],
        screen,
        active:-1
      }
    },
    mounted(){
      this.tabChange(0);
    },
    methods:{
      set_cur(ind){
        this.$refs['lwtab'].swipeTo(ind)
      },
      tabChange(e){
        this.active=e;
        this.tablist=this.tabitem[e].data;
      }
    },
    components: {
    }
  }
</script>
<style lang="less" scoped>
  /* pages/mya/mya.wxss */
  .shadow2{
    box-shadow:0px 2px 8px 0px rgba(229,229,229,0.42);
  }
  .ft-text{
    color:#fff;
    font-size:19px;
  }
  .flex-bottom{
    display:flex;
    align-items:center;
    justify-content: space-between;
  }
  .mb-left{
    display:flex;
    align-items:center;
  }
  .mr-btn{
    background-color:rgba(255,255,255,.2);
    padding:5px;
    border-radius:6px;
    color:#fff;
    position:relative;
    font-size:15px;
  }
  .ml-icon{
    width:68px;
    height:68px;
    border-radius:50%;

  }
  .mi-name{
    color:#fff;
    font-size:19px;
    padding:0 12.5px;
  }
  .mh-bg{
    display:flex;
    justify-content: space-between;
    padding:20px 12.5px;
    box-sizing:border-box;
    flex-direction: column;

  }
  .mh-bg{
    background: linear-gradient(to left, rgb(82, 195, 252), rgb(48, 166, 239),rgb(25, 148, 230));
  }
  .page{
    background-color:#fff;
  }
  .over2{
    overflow:hidden;

    text-overflow:ellipsis;

    display:-webkit-box;

    -webkit-box-orient:vertical;

    -webkit-line-clamp:2;
  }

  .mb-h{
    display:flex;
    align-items:center;
    height:60px;
  }
  .m-h-item{
    flex:1;
    font-size:16px;
    color:#6A6B6E;
    text-align:center;
  }
  .m-h-item.active{
    color:#2A7AEC;
  }
  .mhi-i{
    border-left:1px solid #eee;
    border-right:1px solid #eee;
    text-align:center;
  }
  .di-li{
    padding:12.5px;
    margin-bottom:12.4px;
  }
  .dl-con{
    display:flex;
  }

  .dl-right{
    flex:1;
    padding:0 12.5px;
    text-align:left;
  }
  .dr-text{
    color:#212121;
    font-size:15px;
    font-weight:800;
    line-height:24px;

  }
  .di-in{
    padding:12.5px;
  }
  .dr-time{
    color:#ACACAC;
    font-size:12px;
    font-weight:400;
    line-height:24px;
  }


  .dl-icon{
    width:106px;
    height:74px;
    border-radius:4px;
  }

  .dl-btns{
    text-align:right;
  }
  .dl-btn{
    border-radius:26px;
    border:1px solid #FFA200;
    color:#FFA200;
    font-size:13px;
    text-align:center;
    padding:0px 10px;
    line-height:2;
    display:inline-block;
    background-color:transparent;

  }
  .dl-btn:active{
    opacity:.7;
  }
  .dl-btn::after{
    border:none;
  }
</style>
