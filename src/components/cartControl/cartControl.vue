<template>
  <div class="cartcontrol">
    <div class="cart-decrease icon-remove_circle_outline" @click='decreaseCart' v-show="food.count>0"></div>
    <div class="cart-count" v-show="food.count>0">{{food.count}}</div>
    <div class="cart-add icon-add_circle" @click="addCart"></div>
  </div>
</template>

<script>
import Vue from 'vue'
export default {
  props: {
    food: {
      type: Object
    }
  },
  created() {
  },
  methods: {
    addCart(event) {
      if (!event._constructed) {
        return;
      }
      if (!this.food.count) {
        Vue.set(this.food, 'count', 1)
      } else {
        this.food.count++
      }
    },
    decreaseCart() {
      if (!event._constructed) {
        return;
      }
      if (this.food.count) {
        this.food.count--
      }
    }
  }
}
</script>

<style lang="stylus">
  .cartcontrol
    .cart-decrease, .cart-add
      display inline-block
      font-size 24px
      line-height 24px
      padding 6px
      color rgb(0, 160, 220)
    .cart-count
      display inline-block
      vertical-align top
      width: 12px
      padding-top: 6px
      line-height 24px
      text-align center
      font-size 10px
      color rgb(147,153,159)
</style>

