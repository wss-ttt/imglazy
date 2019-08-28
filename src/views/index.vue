<template>
  <div class="wrapper">
    <button @click="getData">请求数据</button>
    <ul>
      <li v-for="(item,index) in list" :key="index">
        <!-- <img :src="imgProxy(item.image)" alt /> -->
        <img v-lazy="imgProxy(item.image)" alt />
      </li>
    </ul>
  </div>
</template>

<script>
import { imgProxy } from '@/utils/index.js'
export default {
  components: {},
  props: {},
  data() {
    return {
      list: []
    }
  },
  watch: {},
  computed: {},
  methods: {
    imgProxy,
    getData() {
      this.$http({
        url: '/api/4/news/latest',
        method: 'get'
      }).then(({ data }) => {
        this.list = data.top_stories
      })
    }
  },
  created() {},
  mounted() {}
}
</script>
<style scoped>
ul,
li {
  margin: 0;
  list-style-type: none;
}
ul li img {
  width: 120px;
  height: 120px;
}
</style>