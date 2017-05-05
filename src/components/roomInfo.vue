<template>
      <div class="ui bottom attached tab segment active" data-tab="first">
        <div class="ui equal width form">
        <div class="fields">
          <div class="field">
            <label>身份证:</label>
            <input type="text" id="personID">
          </div>
          <div class="field">
            <label>房间号码:</label>
            <input type="text" id="roomNum">
          </div>
          <div class="field">
            <label>房间类型:</label>
            <select class="ui dropdown" id="select">
              <option >标准间</option>
              <option >大床间</option>
              <option >总统间</option>
            </select>
          </div>
           <div class="field">
            <label>房间单价:</label>
            <select class="ui dropdown" id="danjia">
              <option ><span>100</span>/天</option>
              <option ><span>150</span>/天</option>
              <option ><span>200</span>/天</option>
            </select>
          </div>
          <slot name="lastMoney"></slot>
        </div>
      </div>
      <input class="ui primary button" type="submit" @click="pushPersonData">
     </div>
</template>
<script>
export default {
  name: 'roomInfo',
  methods:{
    pushPersonData:function(){
        var id = personID.value
        var num = roomNum.value
        var type = select.value
        var danjia1 = danjia.value
        var obj ={}
        obj.id = id
        obj.num = num
        obj.type = type
        obj.danjia1 = danjia1  
        this.$emit("personData",obj)
    }
   
  }
}
</script>