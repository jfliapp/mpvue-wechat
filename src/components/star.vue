<template>
  <div>
    <div style="display: flex;width: 150px;justify-content: space-around">
      <div v-for="(item, id1) in starT" :key="id" @click="clickImg(id1+1)" data-sr="starT">
        <block>⭐</block>
      </div>
      <div v-for="(item, id2) in (5-starT)" :key="id" @click="clickImg(id2+1)" data-sr="starF">
        <block><img :src="img" style="width: 20px;height: 20px;"></block>
      </div>
  </div>
  </div>
</template>
<script>
  import img from '../../static/imgs/star.png'
  export default {
    data () {
      return {
        starT: 3,
        img: img
      }
    },
    methods: {
      clickImg (num) {
        console.log(this)
        console.log(num)
      }
    }
  }
</script>