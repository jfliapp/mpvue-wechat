<template>
  <div style="background: rgb(246, 246, 246);">
    <div v-if="login" style="font-size: 13px;height: 15px;line-height: 15px;padding: 20px;background: white">登录后有意想不到事情<span style="color:rgb(0, 126, 226);">更多优惠</span></div>
    <div style="display: flex;flex-direction: column;">
      <div style="display: flex;flex-direction: column;padding: 10px 20px 0;margin-top: 10px;background: white">
        <div style="display: flex;justify-content: center;height: 60px;align-items: center">上海Pagoda君亭设计酒店</div>
        <div style="font-size: 17px;height: 40px;line-height: 40px">创客房（开业特惠）</div>
        <div style="display: flex;flex-direction: column;font-size: 15px;color: #ccc;height: 60px;justify-content: space-around;border-bottom: 1px solid rgb(235, 235, 235);padding-bottom: 10px">
          <div>大床&nbsp;&nbsp;&nbsp;&nbsp;可住2人&nbsp;&nbsp;&nbsp;&nbsp;双份早餐</div>
          <div>25 - 28m&sup2;&nbsp;&nbsp;&nbsp;&nbsp;5 - 12层&nbsp;&nbsp;&nbsp;&nbsp;全部房间WI-FI免费</div>
        </div>
        <div style="display: flex;height: 50px;align-items: center;font-size: 15px;color:#ccc;justify-content: space-between">
          <div style="display: flex;">
            <div>入住： 6月11日</div>
            <div>离店： 6月12日</div>
            <div>&nbsp;&nbsp;一晚</div>
          </div>
          <div style="color: rgb(0, 126, 226);display: flex;align-items: center">修改&nbsp;&nbsp;<img src="../../../static/imgs/right.png" style="width:15px;height: 15px;"></div>
        </div>      
      </div>
      <div style="display: flex;height: 22px;background: rgba(0, 126, 226, 0.05);justify-content: space-between;align-items: center;padding: 20px">
        <div style="color: rgb(0, 126, 226);font-size: 15px;">免费领取</div>
        <div><img src="../../../static/imgs/right.png" style="width:15px;height: 15px;"></div>
      </div>
    </div>
    <div v-if="login" style="display: flex;flex-direction:column;margin-top: 10px;font-size: 17px;height: 300px;">
      <div style="display: flex;">
        <div :class="{loginChang: phone}" style="width: 50%;text-align: center;height:50px;line-height: 50px;" @click="changeLogin(1)">手机动态验证登录</div>
        <div :class="{loginChang: !phone}" style="width: 50%;text-align: center;height:50px;line-height: 50px;" @click="changeLogin(2)">普通登录</div>
      </div>
      <div v-if="phone" style="display: flex;flex-direction: column;height: 180px;justify-content: space-around">
        <div style="display: flex;width: 95%;height: 56px;align-items: center;margin: 0 auto;border: 1px solid rgb(190, 190, 190);border-radius: 8px 8px;">
          <div style="margin-left: 10px;width:75px;">手机号</div>
          <div style="margin-left: 20px"><input type="text" placeholder="手机号"></div>
        </div>
        <div style="display: flex;width: 95%;height: 56px;align-items: center;margin: 0 auto;border: 1px solid rgb(190, 190, 190);border-radius: 8px 8px;">
          <div style="margin-left: 10px;width: 100px;">动态密码</div>
          <div style="margin-left: 20px;width: auto;"><input type="text" placeholder="动态密码"></div>
          <div style="width: 160px;height: 30px;margin-right:10px;text-align: center;line-height: 30px;border:1px solid rgb(0, 126, 226) ;color: rgb(0, 126, 226)">获取动态密码</div>
        </div>
        <!-- <div style="font-size: 20px;color: white;width: 95%;height: 50px;text-align: center;line-height: 56px;margin: 0 auto;border-radius: 8px 8px;background: rgb(255, 107, 20)">登录</div> -->
      </div>
      <div v-else style="display: flex;flex-direction: column;height: 180px;justify-content: space-around">
        <div style="display: flex;width: 95%;height: 56px;align-items: center;margin: 0 auto;border: 1px solid rgb(190, 190, 190);border-radius: 8px 8px;">
          <div style="margin-left: 10px;width:75px;">账号</div>
          <div style="margin-left: 20px"><input type="text" placeholder="账号"></div>
        </div>
        <div style="display: flex;width: 95%;height: 56px;align-items: center;margin: 0 auto;border: 1px solid rgb(190, 190, 190);border-radius: 8px 8px;">
          <div style="margin-left: 10px;width:75px;">密码</div>
          <div style="margin-left: 20px"><input type="text" placeholder="密码"></div>
        </div>
      </div>
      <div style="font-size: 20px;color: white;width: 95%;height: 50px;text-align: center;line-height: 56px;margin: 0 auto;border-radius: 8px 8px;background: rgb(255, 107, 20)"
      @click="loginT">登录</div>
    </div>
    <div v-else>
      <div style="margin-top: 10px;height: 80px;background: white;display: flex;flex-direction: column;justify-content: space-around;font-size: 15px;padding: 20px">
        <div style="display: flex;align-items: center;color: rgb(255, 107, 20)"><img src="../../../static/imgs/great.png" style="width: 30px;height: 30px;">&nbsp;&nbsp;好赞！这么划算的房间都能给你挑到</div>
        <div style="display: flex;align-items: center;color: rgb(0, 126, 226)"><img src="../../../static/imgs/help.png" style="width: 30px;height: 30px;">&nbsp;&nbsp;好赞！这么划算的房间都能给你挑到</div>
      </div>
      <div style="margin-top: 10px;height: 250px;background: white;padding: 0 20px;display: flex;flex-direction: column;justify-content: space-around">
        <div style="height: 30px;line-height: 30px;border-bottom: 1px solid #ccc;display: flex;justify-content: space-between;font-size: 15px">
          <div style="display: flex;">
            <div>房间数</div>
            <div>&nbsp;&nbsp;&nbsp;1间</div>
          </div>
          <div style="display: flex;align-items: center"><img src="../../../static/imgs/down.png" style="width:20px;height: 20px;"></div>
        </div>
        <div style="height: 30px;line-height: 30px;border-bottom: 1px solid #ccc;display: flex;justify-content: space-between;font-size: 15px">
          <div style="display: flex;">
            <div>房间数</div>
            <div>&nbsp;&nbsp;&nbsp;1间</div>
          </div>
          <div style="display: flex;align-items: center"><img src="../../../static/imgs/down.png" style="width:20px;height: 20px;"></div>
        </div>
        <div style="height: 30px;line-height: 30px;border-bottom: 1px solid #ccc;display: flex;justify-content: space-between;font-size: 15px">
          <div style="display: flex;">
            <div>房间数</div>
            <div>&nbsp;&nbsp;&nbsp;1间</div>
          </div>
          <div style="display: flex;align-items: center"><img src="../../../static/imgs/down.png" style="width:20px;height: 20px;"></div>
        </div>
        <div style="height: 30px;line-height: 30px;border-bottom: 1px solid #ccc;display: flex;justify-content: space-between;font-size: 15px">
          <div style="display: flex;">
            <div>房间数</div>
            <div>&nbsp;&nbsp;&nbsp;1间</div>
          </div>
          <div style="display: flex;align-items: center"><img src="../../../static/imgs/down.png" style="width:20px;height: 20px;"></div>
        </div>
        <div style="height: 30px;line-height: 30px;border-bottom: 1px solid #ccc;display: flex;justify-content: space-between;font-size: 15px">
          <div style="display: flex;">
            <div>房间数</div>
            <div>&nbsp;&nbsp;&nbsp;1间</div>
          </div>
          <div style="display: flex;align-items: center"><img src="../../../static/imgs/down.png" style="width:20px;height: 20px;"></div>
        </div>
      </div>
      <div style="margin-top: 10px;height: 100px;background: white;padding: 0 20px;display: flex;flex-direction: column;justify-content: space-around">
        <div style="height: 30px;line-height: 30px;border-bottom: 1px solid #ccc;display: flex;justify-content: space-between;font-size: 15px">
          <div style="display: flex;">
            <div>房间数</div>
            <div>&nbsp;&nbsp;&nbsp;1间</div>
          </div>
          <div style="display: flex;align-items: center"><img src="../../../static/imgs/down.png" style="width:20px;height: 20px;"></div>
        </div>
        <div style="height: 30px;line-height: 30px;border-bottom: 1px solid #ccc;display: flex;justify-content: space-between;font-size: 15px">
          <div style="display: flex;">
            <div>房间数</div>
            <div>&nbsp;&nbsp;&nbsp;1间</div>
          </div>
          <div style="display: flex;align-items: center"><img src="../../../static/imgs/down.png" style="width:20px;height: 20px;"></div>
        </div>
      </div>
      <div style="display: flex;height: 250px;font-size: 15px;padding: 20px;display: flex;flex-direction: column;justify-content: space-around">
        <div style="color: #ccc;height: 80px;border-bottom:1px solid #ccc; ">
          酒店提示：根据《上海市公共场所控制吸烟条例》，从2017年3月1日起，酒店不能安排吸烟房，并禁止室内吸烟。
        </div>
        <div style="color: #ccc;height: 60px;">
          酒店提示：根据《上海市公共场所控制吸烟条例》，从2017年3月1日起，酒店不能安排吸烟房，并禁止室内吸烟。
        </div>
        <div class="hotel_foot_Bottom">
          <span><img style="width:10px ;height: 10px;margin-right: 5px;" src="../../../static/imgs/foot_icon.png" alt=""></span>专业服务 · 全程保障
        </div>
      </div>
      <div style="height: 20px;color: rgb(0, 126, 226);text-align: right;padding: 20px;background: white;line-height: 30px;">
        总计： ￥129.99
      </div>
      <div style="height: 20px;color: white;text-align: center;padding: 20px;background: rgb(9, 187, 7);line-height: 20px;">
        微信支付
      </div>
    </div>
  </div>
</template>
<script>
  import order from '@/components/order'
  export default {
    name: 'order',
    data () {
      return {
        data: 'xx',
        phone: true,
        login: true
      }
    },
    components: {
      order
    },
    mounted () {
      console.log('order')
      wx.setNavigationBarTitle({
        title: '预定房间'
      })
    },
    methods: {
      changeLogin (id) {
        if (id === 1) {
          this.phone = true
        } else {
          this.phone = false
        }
        console.log('get')
      },
      loginT () {
        this.login = false
      }
    }
  }
</script>

<style>
  .loginChang {
    color: rgb(0, 126, 226);
    border-bottom: 2px solid rgb(0, 126, 226);
  }
  .hotel_foot_Bottom {
    width: 100%;
    text-align: center;
    font-size: 12px;
    color: rgb(0, 126, 226);
    height: 50px;
    line-height: 50px;
  }
</style>
