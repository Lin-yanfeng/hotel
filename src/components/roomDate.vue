<template>
   <div class="ui bottom attached tab segment" data-tab="third">
        <form class="ui form">
          <dl  class="inline fields">
            <dt>
              <label for="">
                订房天数：
              </label>
            </dt>
            <dd>
              <input type="number" :value="days" id="totalDays">
            </dd>
          </dl>
          <dl  class="inline fields">
            <dt>
              <label for="">
                已住天数：
              </label>
            </dt>
            <dd>
              <input type="number" v-model="hasDays" id="haveDays">
            </dd>
          </dl>
          <dl  class="inline fields">
            <dt>
              <label for="">
                剩余天数：
              </label>
            </dt>
            <dd>
              <input type="number" :value="days-hasDays" id="chargeDays" disabled>
            </dd>
          </dl>
          <input type="submit" class="ui primary button" value="结算" @click="pushData">
        </form>
      </div>
</template>

<script>
export default {
  name: 'roomDate',
  data () {
    return {
      days:10,
      hasDays:5
    }
  },
  methods:{
      pushData:function(){
        var day1 = totalDays.value
        var day2  = haveDays.value
        var day3  = chargeDays.value
        var obj ={}
        obj.day1 = day1 
        obj.day2 = day2 
        obj.day3 = day3 
        this.$emit("daysData",obj)
      }
  }
}


</script>

