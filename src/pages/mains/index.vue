<template>
  <div>
    <div class="sub_title">
      <div style="width: 100%;height: 20px;">
        <div style="float: left;margin-left: 45%;">上海<img src="../../../static/imgs/down.png" alt="" style="width: 15px;height: 15px;"></div>
        <div style="float: right;"><img src="../../../static/imgs/map_icon.png" style="width: 15px;height: 15px;"/><span style="margin-left: 5px;">附近</span></div>
      </div>
      <div style="margin-top: 10px;">
        <div class="input_sel">
          <div>
            <div style="float: left;font-size: 13px;">
                <p>住<span style="color: #ccc;margin-left: 5px;">06-11</span></p>
                <p>离<span style="color: #ccc;margin-left: 5px;">06-11</span></p>
              </div>
            <div style="float: left;margin-top: 8px;"><img src="../../../static/imgs/down.png" alt="" style="width: 15px;height: 15px;"></div>
            <div style="margin-top: 3px;float: left;color: #ccc;font-size: 19px;">|</div>
            <!-- <div style="float: left;"><img src="../../../static/imgs/filter_line.png" alt="" style="width: 15px;height: 40px;"></div> -->
          </div>
          <div>
            <div style="float: left;margin-left: 5px;margin-top: 9px;"><img src="../../../static/imgs/search.png" alt="" class="img_class"></div>
            <div><input style="height: 40px;padding-left: 3px" type="text" placeholder="关键字/位置/品牌/酒店名"></div>
          </div>          
        </div>
        <div class="input_map">地图</div>
      </div>
    </div>    
    <div class="filter_item" style="border-bottom: 1px solid #ccc;padding-bottom: 2px">
      <div @click="filterItem(item)" v-for="(item, index) in filter_item" :key="index">
        <div>
          <span :class="{click_change: item.active}">{{item.name}}&nbsp;&nbsp;</span>
          <img v-if="!item.active" class="img_class" src="../../../static/imgs/down_san1.png"/>
          <img v-else class="img_class" src="../../../static/imgs/up_san.png"/> |
        </div>
      </div>
      <div style="color: #1296db" @click="likeFli">&nbsp;欢迎度排序<img class="img_class" src="../../../static/imgs/down_san.png"/></div>
    </div>
    <div class="filter_item" style="background: rgb(244, 244, 246);margin-top: 8px;padding: 10px 0">
      <div class="filter_li">低价好评</div>
      <div class="filter_li">位置距离</div>
      <div class="filter_li">酒店类型<img src="../../../static/imgs/down.png" alt="" class="img_class"></div>
      <div class="filter_li">热门品牌<img src="../../../static/imgs/down.png" alt="" class="img_class"></div>
    </div>
    <div>
      <div class="hotel_item" v-for="(item, id) in hotel_item" :key="id" @click="hotelDetail(item.id)">
        <div style="flex: 1.5;">
          <img :src="item.img" alt="" style="display: inline;" mode="scaleToFill">
        </div>
        <div class="hotel_item_R">
          <p>{{item.name}}<span style="font-size: 13px;color: #ccc">{{item.type}}</span></p>
          <p style="color: #1296db;">{{item.score}}分<span>{{item.grade}}</span><span style="font-size: 13px;color: #ccc">  {{item.comment}}条点评</span></p>
          <div style="display: flex; align-items: flex-end">
            <div>
              <p style="font-size: 13px;color: #ccc">距离市中心{{item.distace}}公里</p>
              <div style="display: flex;flex: 1;">
                <div class="item_type">烂漫情侣</div>
                <div class="item_type">烂漫情侣</div>
              </div>
            </div>
            <div style="text-align: right;flex: 1;">
              <p style="font-size: 12px;color: #ccc">C-TYPE<span style="text-decoration:line-through;">${{item.old_prize}}</span></p>
              <p style="font-size: 13px;color: #1296db">OUT PRICE ${{item.new_prize}}</p>
            </div>
          </div>
        </div>
      </div>
    </div>
    <!-- 这里开始弹框 -->
    <!-- <div style="height: 350px;background: yellowgreen;"> -->
      <div v-if="tapState == 'filter'" class="F_model">
        <div class="F_model_T" style="display: flex;height: 380px;">
          <div style="display: flex;flex-direction: column;flex: 1.5;background: rgb(245, 245, 245);overflow-y: scroll">
            <div v-for="(item, iFilter) in arr1" :key="iFilter"
            class="F_model_tl"
            :class="{F_model_tlF: item.border}"
            @click="clickL(item)">{{item.name}}</div>
          </div>
          <div style="display: flex;flex-direction: column;flex: 4;overflow-y: scroll">
            <div v-for="(arrI, idx) in arrItemL" :key="idx">
              <div style="font-size: 15px;padding: 5px;">{{arrI.name}}</div>
              <div style="display: flex;flex-wrap: wrap;font-size: 15px;">
                <div v-for="(item, index) in (arrI.tab ? arrI.arr : arrI.arrSlice)" :key="index"style="width: 60px;height: 30px;background:rgb(237, 245, 251);text-align: center;line-height: 30px;margin:5px;">{{item}}</div>
                <div v-if="arrI.tab" style="width: 60px;height: 30px;background: yellow;text-align: center;line-height: 30px;margin:5px;" @click="arrI.tab = !arrI.tab">收缩</div>
                <div v-else style="width: 60px;height: 30px;background: yellow;text-align: center;line-height: 30px;margin:5px;" @click="arrI.tab = !arrI.tab">更多</div>
                <!-- <div v-if="arrI.arr.length === moreLen" style="width: 60px;height: 30px;background: yellow;text-align: center;line-height: 30px;margin:5px;" @click="ItemDiv(arrI.arr)">收缩</div> -->
              </div>
            </div>  
          </div>
        </div>
        <div class="F_model_B" style="display: flex;">
          <div style="width: 50%;text-align: center;height: 43px;line-height: 43px">清空</div>
          <div style="width: 50%;text-align: center;height: 43px;line-height: 43px;background: rgb(254, 105, 19);"
          @click="sureF">确定</div>
        </div>
      </div>
      <div v-else-if="tapState == 'map'" class="F_model">
        <div class="F_model_T" style="display: flex;height: 380px;">
          <div style="display: flex;flex-direction: column;flex: 1.5;background: rgb(245, 245, 245);overflow-y: scroll">
            <div v-for="(item, iFilter1) in arr2" :key="iFilter1"
            class="F_model_tl"
            :class="{F_model_tlF: item.border}"
            @click="clickL2(item)">{{item.name}}</div>
          </div>
          <div style="display: flex;flex-direction: column;flex: 4;overflow-y: scroll">
            <div v-for="(arrI, idxDist) in arrDistance" :key="idxDist"
            style="display: flex;justify-content: space-between;padding: 5px 10px;border-bottom: 1px solid rgb(235, 235, 235);font-size: 15px"
            :class="{dist_color: arrI.checked}"
            @click="check(arrI)">
              <div>{{arrI.value}}</div>
              <div :hidden="!arrI.checked">✔</div>
            </div>  
          </div>
        </div>
        <div class="F_model_B" style="display: flex;">
          <div style="width: 50%;text-align: center;height: 43px;line-height: 43px">清空</div>
          <div style="width: 50%;text-align: center;height: 43px;line-height: 43px;background: rgb(254, 105, 19);"
          @click="sureF">确定</div>
        </div>
      </div>
      <div v-else-if="tapState == 'price'" class="F_model">
        <div class="F_model_T" style="display: flex;height: 380px;flex-direction: column;padding:0 15px;">
          <div style="display: flex;flex-direction: column;margin-top: 15px;">
            <div style="font-size: 17px;margin-bottom: 15px;">星级(可复选)</div> 
            <div style="display: flex;justify-content: space-around">
              <div v-for="(item, ind) in star" :key="ind" class="star" :class="{star_choose: item.state}" @click=starChoose(item)>
                {{item.name}}
              </div>
            </div>
          </div>
          <div style="display: flex;flex-direction: column;margin-top: 15px;">
            <div style="font-size: 17px;margin-bottom: 15px;">价格</div> 
            <div style="display: flex;flex-direction: column">
              <div style="display: flex;justify-content: space-between">
                <div>￥0</div>
                <div>￥10000</div>
              </div>
              <slider step="1" backgroundColor="rgb(0, 126, 226)" height="3px"></slider>
            </div>
          </div>
        </div>
        <div class="F_model_B" style="display: flex;">
          <div style="width: 50%;text-align: center;height: 43px;line-height: 43px">清空</div>
          <div style="width: 50%;text-align: center;height: 43px;line-height: 43px;background: rgb(254, 105, 19);"
          @click="sureF">确定</div>
        </div>
      </div>
      <div v-else></div>
    <!-- </div> -->
  </div>
</template>
<script>
  import img from '../../../static/imgs/hotel_item.png'

  export default {
    name: 'main',
    data () {
      return {
        color_change: true,
        moreLen: 0,
        star: [
          {
            id: 1,
            value: 2,
            state: false,
            name: '二星及以下/舒适'
          },
          {
            id: 2,
            value: 3,
            state: false,
            name: '三星/舒适'
          },
          {
            id: 3,
            value: 4,
            state: false,
            name: '四星/舒适'
          },
          {
            id: 4,
            value: 5,
            state: false,
            name: '五星以上/舒适'
          }
        ],
        arrDistance: [
          {
            id: 1,
            name: 'All',
            value: '全城',
            checked: true
          },
          {
            id: 2,
            name: 'CHN',
            value: '中国',
            checked: false
          },
          {
            id: 3,
            name: 'USA',
            value: '美国',
            checked: false
          },
          {
            id: 4,
            name: 'JPN',
            value: '日本',
            checked: false
          }
        ],
        arr1: [
          {
            id: 1,
            name: '高端连锁',
            border: true
          },
          {
            id: 2,
            name: '中端连锁',
            border: false
          },
          {
            id: 3,
            name: '快捷连锁',
            border: false
          }
        ],
        arr2: [
          {
            id: 1,
            name: '距离',
            border: true
          },
          {
            id: 2,
            name: '商业区',
            border: false
          },
          {
            id: 3,
            name: '中国区',
            border: false
          }
        ],
        arrItemL: [
          {
            name: '高端连锁',
            idx: 0,
            tab: false,
            arrSlice: ['xx', 'xx', 'xx', 'xx', 'xx', 'xx', 'xx'],
            arr: ['xx', 'xx', 'xx', 'xx', 'xx', 'xx', 'xx', 'xx', 'xx', 'xx', 'xx', 'xx', 'xx', 'xx', 'xx', 'xx', 'xx', 'xx', 'xx', 'xx']
          },
          {
            name: '中端连锁',
            idx: 1,
            tab: true,
            arrSlice: ['xx', 'xx', 'xx', 'xx', 'xx', 'xx', 'xx'],
            arr: ['xx', 'xx', 'xx', 'xx', 'xx', 'xx', 'xx', 'xx', 'xx', 'xx', 'xx', 'xx', 'xx', 'xx', 'xx']
          },
          {
            name: '快捷连锁',
            idx: 2,
            tab: false,
            arrSlice: ['xx', 'xx', 'xx', 'xx', 'xx', 'xx', 'xx'],
            arr: ['xx', 'xx', 'xx', 'xx', 'xx', 'xx', 'xx', 'xx', 'xx', 'xx', 'xx', 'xx']
          }
        ],
        filter_item: [
          {
            name: '筛选',
            idex: 0,
            state: 'filter',
            active: false
          },
          {
            name: '位置距离',
            idex: 1,
            state: 'map',
            active: false
          },
          {
            name: '星级/价格',
            state: 'price',
            idex: 2,
            active: false
          }
        ],
        hotel_item: [
          {
            id: 1,
            img: img,
            name: 'xx酒店(上海店)',
            type: '高档行',
            score: 4.8,
            comment: 11103,
            grade: '优秀',
            distace: 2.7,
            old_prize: 120,
            new_prize: 80
          },
          {
            id: 2,
            img: img,
            name: 'xx酒店(上海店)',
            type: '高档行',
            score: 4.9,
            comment: 11103,
            grade: '优秀',
            distace: 2.7,
            old_prize: 120,
            new_prize: 80
          }
        ]
      }
    },
    computed: {
      tapState () {
        let sta = this.filter_item.find((item) => {
          return item.active
        })
        if (sta === undefined) {
          return 'xx'
        }
        return sta.state
      }
    },
    mounted () {
      this.ItemArr()
    },
    methods: {
      hotelDetail (id) {
        wx.navigateTo({
          url: '/pages/detail/main?id=' + id
        })
      },
      ItemArr () {
        console.log('对数组进行处理')
        this.arrItemL.forEach((ele) => {
          console.log(ele.arr.length)
          if (ele.arr.length > 8) {
            ele.sat = false
            ele.S = ele.arr.slice(0, 7)
          }
          console.log(ele)
        })
      },
      clickL (item) {
        let id = item.id
        this.arr1.map((item) => {
          if (id === item.id) {
            item.border = true
          } else {
            item.border = false
          }
        })
      },
      clickL2 (item) {
        let id = item.id
        this.arr2.map((item) => {
          if (id === item.id) {
            item.border = true
          } else {
            item.border = false
          }
        })
      },
      filterItem (item) {
        let Index = item.idex
        this.filter_item.map((item1) => {
          if (Index === item1.idex) {
            item1.active = !item1.active
          } else {
            item1.active = false
          }
        })
      },
      check (item) {
        console.log(item)
        let distId = item.id
        this.arrDistance.map((item) => {
          if (distId === item.id) {
            item.checked = !item.checked
          } else {
            item.checked = false
          }
        })
      },
      starChoose (item) {
        console.log(item)
        let distId = item.id
        this.star.map((item) => {
          if (distId === item.id) {
            item.state = !item.state
          }
        })
      },
      sureF () {
        this.filter_item.map((item1) => {
          item1.active = false
        })
      }
    }
  }
</script>
<style scoped>
  /* $blue_color: rgb(0, 126, 226);
  $ccc_color: rgb(244, 244, 246); */
  ::-webkit-scrollbar {
    width: 0;
    height: 0;
    color: transparent;   
  }
  .sub_title{ 
    width: 100%;
    height: 100px;
    padding: 15px;
    /* text-align: center; */
    font-size: 15px;
    box-sizing: border-box;
    background: rgb(0,126,226)
  }
  .img_class {
    width: 10px;
    height: 10px;
  }
  .input_sel {
    float: left;
    width: 80%;
    height: 40px;
    background: white;
    padding-left: 5px;
    box-sizing: border-box;
    border-radius: 10px 10px;
  }
  /* .input_sel input::-webkit-input-placeholder {    
    color: #aab2bd;
    font-size: 12px;
  } */
  .filter_item {
    display: flex; 
    justify-content: space-around;
    font-size: 14px;
    color: rgb(171,171,171);
    height: 30px;
    background: white;
    line-height: 30px;
  }
  .input_map {
    float: right;
    width: 15%;
    height: 40px;
    text-align: center;
    line-height: 40px;
    color: rgb(0, 126, 226);
    background: rgb(210,228,251);
    border: 0.5px solid #ccc;
    border-radius: 10px 10px;
  }
  .filter_li {
    background:white;
    width:20%;
    height: 30px;
    text-align: center;
    color: black;
    line-height: 30px;
    border-radius: 20px 20px;
  }
  .click_change {
    color: rgb(0,126,226);
  }
  .hotel_item {
    display: flex;
    flex-direction: row;
    height: 125px;
    border-bottom: 1px solid #ccc;    
    }
    .hotel_item_R {
      flex: 3;
      background: white;
      padding: 10px;     
  }
  .item_type {
        height: 20px;
        width: 50px;
        border: 0.5px solid rgb(171,171,171);
        border-radius: 5px;
        line-height: 20px;
        text-align: center;
        margin-top: 10px;
        margin-right: 10px;
        font-size: 11px;
        color: rgb(0, 126, 226);
      }
  .F_model {
    height: 400px;
    display: flex;
    flex-direction: column;
    position: fixed;
    top: 22%;width: 100%;
    background: white
  }
  .F_model_tl {
    height: 40px;
    line-height: 40px;
    text-align: center;
    font-size: 17px;
    border-bottom: 2px solid rgb(236, 236, 236);
  }
  .F_model_tlF {
    border-left: 3px solid rgb(0, 72, 145);
    background: white    
  }
  .dist_color {
    color: rgb(0, 126, 226);
  }
  .star {
    height: 43px;
    width: 82px;
    background:rgb(237, 245, 251);
    /* text-align: center; */
    padding: 3px auto;
    font-size: 13px;
  }
  .star_choose {
    border: 1px solid green;
    color: green
  }
</style>