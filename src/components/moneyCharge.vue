<template>
   <div class="ui bottom attached tab segment" data-tab="second">
        <form class="ui form">
          <slot name="money"></slot>
          <slot name="chargeMoney"></slot>
            <input type="submit" class="ui primary button" value="提交订单">
        </form>
      </div>
</template>

<script>
export default {
  name: 'moneyCharge',
  props:['yajin'],
  data () {
    return {
    
    }
  }
}


</script>

