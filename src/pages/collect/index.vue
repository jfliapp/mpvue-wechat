<template>
  <div style="background: rgb(245, 245, 245);min-height: 500px;">
    <div style="display: flex;justify-content: space-between;height:30px;background: white;padding: 20px;border-bottom: 1px solid #ccc;">
      <div>全部城市 (2)</div>
      <div>></div>
    </div>
    <div style="display: flex;flex-direction: column;">
      <div style="display: flex;padding: 20px;height: 91px;background: white;border-bottom: 1px solid #ccc;font-size: 15px;"
      v-for="item in arrCollect" :key="item.id">
        <div style="height:91px;flex:1;">
          <img :src="item.img" alt="" style="width: 91px;height:91px">
        </div>
        <div style="display: flex;flex-direction: column;justify-content: space-between;padding-left: 10px;flex:3;">
          <div>{{item.name}}</div>
          <div>{{item.type}}</div>
          <div style="display: flex;font-size: 13px;justify-content: space-between;color:rgb(0, 126, 226);">
            <div style="display: flex;flex-direction: column">
              <div>{{item.score}}分 {{item.grade}} {{item.comment}}条点评</div>
              <div>{{item.distance}} {{item.place}}</div>
            </div>
            <div style="display: flex;flex-direction: column;text-align: right">
              <div style="color: #ccc">C-TRIP
                <span style="text-decoration:line-through;">{{item.price_old}}</span>
              </div>
              <div>OUR PRICE {{item.price_new}}</div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
  import img from '../../../static/imgs/hotel_item.png'
  export default {
    data () {
      return {
        arrCollect: [
          {
            id: 1,
            img: img,
            name: '上海市小南国花园酒店',
            type: '五星级',
            score: 4.9,
            grade: '卓越',
            comment: 15648,
            distance: '上海',
            place: '江湾/五角场',
            price_old: 120,
            price_new: 99
          },
          {
            id: 2,
            img: img,
            name: '上海市小南国花园酒店',
            type: '五星级',
            score: 4.9,
            grade: '卓越',
            comment: 15648,
            distance: '上海',
            place: '江湾/五角场',
            price_old: 120,
            price_new: 99
          }
        ]
      }
    }
  }
</script>
