<template>
  <div>
    <button type="button" name="button" @click="getMsg">
      RailsからAPIを取得する
    </button>
    <div v-for="(msg, i) in msgs" :key="i">
      {{ msg }}
    </div>
  </div>
</template>

<script lang="ts">
import Vue from 'vue'

type DataType = {
  msgs: any[]
}

export default Vue.extend({
  data(): DataType {
    return {
      msgs: [],
    }
  },
  methods: {
    getMsg() {
      this.$axios.$get('/api/v1/hello').then((res: any) => this.msgs.push(res))
    },
  },
})
</script>
