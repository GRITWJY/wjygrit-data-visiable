<template>
  <div class="app-container">
    请输入订单号:
    <el-select v-model="trackinput" placeholder="测试中:请选择" size="small" @change="findata">
      <el-option
        v-for="item in inputs"
        :key="item"
        :label="item"
        :value="item">
      </el-option>
    </el-select>

<!--    <el-input-->
<!--      prefix-icon="el-icon-search"-->
<!--      size="small"-->
<!--      v-model="trackinput"-->
<!--      @keyup.enter.native="findata"-->
<!--      class="trackinput"/>-->
    <div class="sanhuobox">
      <div style="margin: 10px 0 10px 10px">
        <span style="font-weight: bolder;">散货名称:{{goodsInfo.name}}</span>
        <span style="float: right; min-width: 160px ">订单号: {{goodsInfo.Id}}</span>
      </div>
      <div style="margin: 20px 0 10px 10px">
        <span style="font-weight: bolder">途径港口: {{goodsInfo.port}}</span>
        <span style="float: right; min-width: 160px">货代:{{goodsInfo.huodai}} </span>
      </div>
    </div>

    <el-steps :active="stepcount" style="margin-top: 20px;">
      <el-step class="stepbox" v-for="goodstep in stepdata" :key="goodstep.index">
        <template slot="description">
          <div class="title">{{goodstep.steptitle}}时间:  {{goodstep.time}}</div>
          <div class="info" v-if="goodstep.imgsrc === undefined ">
            <span class="infotitle">{{goodstep.steptitle}}</span>
            <div class="info-info">进场类型: {{goodstep.type}}</div>
            <p class="info-info">编号/航次: {{goodstep.number}}</p>
          </div>
          <div class="info2" v-else>
            <el-col style="max-width: 60%; max-height: 100%;">
              <img :src=goodstep.imgsrc  style="max-height: 100%; max-width: 100%">
            </el-col>
            <el-col class="info2-txtinfo">
              <p class="title1">操作人员: {{goodstep.people}}</p>
              <p class="title2">备注:
                <span class="txt">{{goodstep.info}}</span>
              </p>
            </el-col>
          </div>
        </template>
      </el-step>


      <!--      <el-step class="stepbox">-->
      <!--        <template slot="description">-->
      <!--          <div class="title">入港时间:  2021-04-14 11:00</div>-->
      <!--          <div class="info">-->
      <!--            <span class="infotitle">入港</span>-->
      <!--            <div class="info-info">进场类型: </div>-->
      <!--            <p class="info-info">编号/航次: </p>-->
      <!--          </div>-->
      <!--        </template>-->
      <!--      </el-step>-->
      <!--      <el-step class="stepbox">-->
      <!--        <template slot="description">-->
      <!--          <div class="title">装货开始时间: 2021-048594</div>-->
      <!--          <div class="info2">-->
      <!--            <el-col style="width: 250px; height: 100%;">-->
      <!--              <img src="../../assets/404_images/404.png" style="width: 100%">-->
      <!--            </el-col>-->
      <!--            <el-col class="info2-txtinfo">-->
      <!--              <p class="title1">操作人员: 张三</p>-->
      <!--              <p class="title2">备注:-->
      <!--              <span class="txt">张三张三张三张三</span>-->
      <!--              </p>-->
      <!--            </el-col>-->
      <!--          </div>-->
      <!--        </template>-->
      <!--      </el-step>-->
      <!--      <el-step  style="width: 450px">-->
      <!--        <template slot="description">-->
      <!--          <div style="text-align:right">开始时间: 2021098594</div>-->
      <!--          <div style="width: 350px; margin-left: 100px; height: 10px; background-color: #99a9bf;"></div>-->
      <!--        </template>-->
      <!--      </el-step>-->
      <!--      <el-step title="步骤 4" style="width: 450px"></el-step>-->
      <!--      <el-step title="步骤 4" style="width: 450px"></el-step>-->
    </el-steps>
  </div>
</template>

<script>

export default {
  data() {
    return {
      inputs:[
        '202104061234',
        '202104061235',
        '202104061236'
      ],
      trackinput:'',
      active: 5,
      goodsInfo1:{
        name:'硫磺',
        Id:'20210316142721',
        port:'松滋港',
        huodai:'中远'
      },
      goodsInfo:{},
      stepcount:0,
      stepdata1:[{
        time:"2021-04-14 11:00",
        steptitle:'入港',
        type:'船运',
        number:'汉海一号'
      },{
        time:'2021-04-14 15:00',
        steptitle:'卸货开始',
        imgsrc:"https://wjygrit.oss-cn-beijing.aliyuncs.com/2021/08/09/404.png",
        people:'张三',
        info:'开始卸货硫磺'
      },{
        time:'2021-04-16 15:45',
        steptitle:'装货完成',
        imgsrc:'https://wjygrit.oss-cn-beijing.aliyuncs.com/2021/08/09/607328B9-EAF8-4AC0-AF46-D785D897418F_4_5005_c.jpeg',
        people:'小刘',
        info:'装货硫磺完成'
      },{
        time:"2021-04-14 16:00",
        steptitle:'出港',
        type:'铁路',
        number:'G106'
      }],
      stepdata2:[{
        time:"2021-04-14 11:00",
        steptitle:'入港',
        type:'船运',
        number:'汉海一号'
      },{
        time:'2021-04-14 15:00',
        steptitle:'卸货开始',
        imgsrc:"https://wjygrit.oss-cn-beijing.aliyuncs.com/2021/08/09/404.png",
        people:'张三',
        info:'开始卸货硫磺'
      },{
        time:'2021-04-16 15:45',
        steptitle:'装货完成',
        imgsrc:'https://wjygrit.oss-cn-beijing.aliyuncs.com/2021/08/09/607328B9-EAF8-4AC0-AF46-D785D897418F_4_5005_c.jpeg',
        people:'小刘',
        info:'装货硫磺完成'
      },{
        time:"2021-04-14 16:00",
        steptitle:'出港',
        type:'铁路',
        number:'G106'
      },{
        time:'2021-05-16 17:00',
        steptitle: '到站',
        type: '铁路',
        number: 'G106'
      },{
        time: '2021-05-16 19:00',
        steptitle:'卸货开始',
        imgsrc:"https://wjygrit.oss-cn-beijing.aliyuncs.com/2021/08/09/404.png",
        people: '王五',
        info:'从火车上卸货'
      },{
        time:'2021-05-17 19:00',
        steptitle: '装货完成',
        imgsrc:'https://wjygrit.oss-cn-beijing.aliyuncs.com/2021/08/09/607328B9-EAF8-4AC0-AF46-D785D897418F_4_5005_c.jpeg',
        people: '李四',
        info:'装载货车完成'
      },{
        time:'2021-05-17 20:00',
        steptitle: '出站',
        type: '货运',
        number: '沪AAAAA'
      },{
        time: '2021-05-19 21:00',
        steptitle: '到站',
        type: '货运',
        number: '沪AAAAA'
      },{
        time: '2021-05-19 22:00',
        steptitle:'卸货完成',
        imgsrc:'https://wjygrit.oss-cn-beijing.aliyuncs.com/2021/08/09/607328B9-EAF8-4AC0-AF46-D785D897418F_4_5005_c.jpeg',
        people: '王五',
        info:'目的地卸货'
      }],
      stepdata:[],
    }
  },
  mounted() {
    if (this._isMobile()) {
    } else {
      this.$router.push({path:'/form/index'})
    }
  },
  methods: {
    _isMobile() {
      let flag = navigator.userAgent.match(/(phone|iPhone|ios|Android|BlackBerry|IEMobile|MQQBrowser|JUC|Fennec|wOSBrowser|BrowserNG|WebOS|Symbian|Windows Phone)/i)
      return flag;
    },
    findata(){
      console.log(this.trackinput)
      switch (this.trackinput){
        case '202104061234':
          this.stepdata = this.stepdata1
          this.stepcount = this.stepdata.length
          this.goodsInfo = this.goodsInfo1
          break
        case '202104061235':
          this.stepdata = this.stepdata2
          this.stepcount = this.stepdata.length
          this.goodsInfo = this.goodsInfo1
          break
        case '202104061236':
          this.stepdata = this.stepdata1
          this.stepcount = this.stepdata.length
          this.goodsInfo = this.goodsInfo1
          break
        default:
          break
      }

    },
  },
  created() {
    console.log()
    this.stepcount = this.stepdata.length
  }
}
</script>

<style scoped lang="scss">
.trackinput{
  width: 30%;
  min-width: 200px;
  margin-left: 10px;
}
.el-steps {
  flex-wrap: wrap;
}
/deep/.el-step{
  flex-basis: auto !important;
  max-width: none !important;
}
.sanhuobox{
  padding: 10px;
  margin:  20px 10px 0 10px;
  min-height: 100px;
  background-color: blue;
  border-radius: 25px;
  position: relative;

  span{
    color: white;
    font-weight: 700;
    font-size: 14px;
  }
  .sanhuotxt{
    width: 100%;
    display: flex;
    flex-direction: row;
    justify-content: space-between;
    align-items: center;
  }
}
.stepbox{
  max-width: 450px;
  width: 90%;
  margin-bottom: 30px;
  .title{
    color: black;
    font-weight: bolder;
    font-size: 15px;
    margin-top: 15px;
    margin-bottom: 5px;
    white-space:pre;
  }
  .info{
    max-width:380px;
    height: 100px;
    background-color: white;
    border: 1px solid #99a9bf;
    border-radius: 15px;
    padding: 5px;
    .infotitle{
      color: black;
      font-weight: bolder;
      font-size: 16px
    }
    .info-info {
      color: black;
      font-size: 14px;
      margin-left: 33px;
    }
  }
  .info2{
    width: 350px;
    height: 150px;
    background-color: white;
    .info2-txtinfo{
      max-width: 128px;
      height: 100%;
      background-color: blue;
      border-top-right-radius: 15px;
      border-bottom-right-radius: 15px;
      .title1{
        color: white;
        font-weight: bolder;
        font-size: 16px;
      }
      .title2{
        color: white;
        font-weight: bolder;
        font-size: 16px;
        word-wrap: break-word;
        max-width: 130px;
        .txt{
          font-weight: normal;font-size: 15px;
        }
      }
    }
  }
}
</style>

