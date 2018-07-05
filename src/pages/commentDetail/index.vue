<template>
  <div style="background:rgb(246, 246, 246);font-size: 15px">
    <div style="height: 20px;line-height: 20px;padding: 20px">上海8090青年求职公寓</div>
    <div style="display: flex;flex-direction: column;background: white;padding: 20px;height: 200px;justify-content: space-around">
      <div style="display: flex;justify-content: space-between;">
        <div>房间卫生</div>
        <div><star/></div>
      </div>
      <div style="display: flex;justify-content: space-between;">
        <div>周边环境</div>
        <div><star/></div>
      </div>
      <div style="display: flex;justify-content: space-between;">
        <div>酒店服务</div>
        <div><star/></div>
      </div>
      <div style="display: flex;justify-content: space-between;">
        <div>设施服务</div>
        <div><star/></div>
      </div>
    </div>
    <div style="margin-top: 10px;height: 70px;background: white;padding: 20px">
      <div style="display: flex;">
        <div style="width:50px;font-size: 11px;height: 30px;line-height: 30px">出游类型</div>
        <div style="width: 300px;display: flex;flex-wrap: wrap;justify-content: flex-start;font-size: 13px;">
          <div v-for="(item,idex) in typeArr" :key="idex" style="background: rgb(237, 245, 251);width: 66px;height: 20px;text-align: center;line-height: 20px;margin: 5px 5px 5px 0;">{{item}}</div>
        </div>
      </div>
    </div>
    <div style="height: 400px">
      <div style="height: 60px;padding: 20px;display: flex;align-items: center">
        <div style="width: 60px;height: 60px;border: 1px dashed black;display: flex;justify-content: center;align-items: center;font-size: 20px;background: white">+</div>
        <div style="width: 250px;font-size: 13px;padding-left: 20px">上传图片可抽奖哦！建议上传设施、周围环境、、外观等细节照片，最多9张</div>
      </div>
      <div style="padding: 20px;">
        <textarea v-model.lazy="textValue" style="background: white;width: 100%;padding: 20px;box-sizing: border-box" placeholder="写点评赚积分免房！您可分享对酒店环境、服务、设施和价格的评论"></textarea>
      </div>
      <div style="display: flex;flex-direction: column;text-align: right;height: 30px;padding-right: 20px;justify-content: space-around">
        <div style="color: #ccc;">至少5个字</div>
        <div style="color: rgb(0, 126, 226)">点评积分规则></div>
      </div>
      <div style="width: 90%;margin: 20px auto;height: 60px;text-align: center;line-height: 60px;color: white;background: rgb(254, 105, 19)">提交</div>
    </div>
  </div>
</template>
<script>
  import star from '@/components/star'
  export default {
    data () {
      return {
        textValue: '',
        typeArr: ['商业出差', '朋友出游', '朋友出游', '朋友出游', '朋友出游', '朋友出游', '其他']
      }
    },
    components: {
      star
    }
  }
</script>