<template>
  <div id="app">
    <h1> 酒店信息管理</h1>
    <div class="ui list">
    <div class="item">
      <i class="user icon"></i>
      <div class="content">身份证:<span>{{myid}}</span> </div>
    </div>
    <div class="item">
      <i class="home icon"></i>
      <div class="content">房间号码:<span>{{mynum}}</span>  </div>
    </div>
    <div class="item">
      <i class="rocket icon"></i>
      <div class="content">
         房间类型:<span>{{myType}}</span> 
      </div>
    </div>
    <div class="item">
      <i class="yen icon"></i>
      <div class="content">
        押金:<span>{{yajin}}</span> 
      </div>
  </div>
</div>
    <div class="ui top attached tabular menu">
    <a class="item active" data-tab="first">订单信息</a>
    <a class="item" data-tab="second">金额管理</a>
    <a class="item" data-tab="third">订房日期</a>
    </div>
    <roomInfo @personData="data">
          <div class="field" slot="lastMoney">
            <label>押金:</label>
            <input type="number" :value="yajin" disabled>
          </div>
    </roomInfo>
    <moneyCharge>
         <dl  class="inline fields" slot="money">
            <dt>
                <label for="">
                &nbsp;&nbsp;&nbsp;押金：&nbsp;&nbsp;&nbsp;&nbsp;
                </label>
              </dt>
              <dd>
                <input type="number" :value="yajin">
              </dd>
         </dl>
         <dl class="inline fields" slot="chargeMoney">
              <dt>
                <label for="">
                  剩余金额：
                </label>
              </dt>
              <dd>
                <input type="number" :value="sum" disabled>
              </dd>
            </dl>
    </moneyCharge>
    <roomDate @daysData="dayData">
    </roomDate>
  </div>
</template>

<script>
import roomTab from './components/roomTab'
import roomInfo  from './components/roomInfo'
import moneyCharge from './components/moneyCharge'
import roomDate from './components/roomDate'
import jQuery from './assets/js/jquery.min.js'
import semantic from './assets/js/semantic.min.js'
window.jQuery = window.$ = $
setTimeout(function(){
  $('.menu .item')
  .tab()
},0)
export default {
  name: 'app',
  components:{
    roomTab,
    roomInfo,
    moneyCharge,
    roomDate
  },
  data(){
    return {
       myid:"",
       mynum:"",
       myType:"",
       yajin:"",
       tDay:"",
       hDay:"",
       cDay:"",
       sum:"",
       danmoney:""
    }  
  },
  methods:{
    data:function(data){
      this.myid = data.id
      this.mynum = data.num
      this.myType = data.type
      this.yajin = parseInt(data.danjia1)
    },
    dayData:function(days){
      var totalDay = days.day1
      var hasDay = days.day2
      var chargeDay = days.day3
      var sumMoney = parseInt(this.yajin) *parseInt(chargeDay)  + parseInt(this.yajin)
      this.sum = sumMoney
    }
  }
}
</script>

<style>
@import "./assets/css/semantic.min.css";
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
form{
  width:50%;
}
</style>
