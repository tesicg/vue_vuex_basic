<template>
  <div>
    <h1>{{count}}</h1>

    <input type="text" v-model="amount">
    <br><br>
    <button @click="increment">+</button>
    <button @click="decrement">-</button>
    <button @click="reset">R</button>
  </div>
</template>

<script>
import { mapGetters } from 'vuex';
import * as fromCount from './store/modules/count/index';

export default {
  data() {
    return {
      amount: 0
    }
  },
  methods: {
    increment() {
      this.$store.dispatch(fromCount.INCREMENT, this.getAmount);
    },
    decrement() {
      this.$store.dispatch(fromCount.DECREMENT, this.getAmount);
    },
    reset() {
      this.$store.dispatch(fromCount.RESET);
    }
  },
  computed: {
    // count() {
    //   return this.$store.getters.count;
    // },
    ...mapGetters(['count']),
    getAmount() {
      return Number(this.amount) || 1;
    }
  }
}
</script>

<style>
</style>
