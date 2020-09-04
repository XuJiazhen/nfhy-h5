<template>
  <div class="home">
    <div class="page-bar">
      <img src="../assets/images/nfhy-bar-logo.png" alt="Logo" />
      <span class="nfhy-bar-text">香和·南方花园</span>
    </div>

    <v-col cols="12" style="padding: 0;">
      <!-- <v-carousel hide-delimiter-background show-arrows-on-hover delimiter-icon="mdi-minus" cycle height="450">
        <v-carousel-item v-for="(carousel, index) in effects" :key="index" :src="carousel.src" />
      </v-carousel> -->
      <v-tabs centered grow hide-slider v-model="tab" background-color="var(--acid-blue)">
        <v-tab v-for="item in items" :key="item.tab" style="color: #e3e3e3;">{{ item.tab }}</v-tab>
      </v-tabs>

      <v-tabs-items v-model="tab">
        <v-tab-item v-for="item in items" :key="item.tab">
          <v-carousel hide-delimiter-background show-arrows-on-hover delimiter-icon="mdi-minus" height="421">
            <v-carousel-item v-for="(carousel, index) in item.content" :key="index" :src="carousel.src" />
          </v-carousel>
        </v-tab-item>
      </v-tabs-items>
    </v-col>

    <v-col cols="12" class="building" style="padding: 0;">
      <v-tabs centered grow hide-slider background-color="var(--acid-blue)">
        <v-tab id="detail" href="#detail" style="color: #e3e3e3;" @click="onScrollTo">详情</v-tab>
        <v-tab-item value="detail">
          <v-col cols="12">
            <div class="building-title"><span>楼盘详情</span></div>
            <div class="building-info">
              <span class="name">香和·南方花园</span>
              <span class="developer">开发商：洞口香和房地产开发有限责任公司</span>
              <span class="selling-location">售楼处地址：洞口华荣路与文昌南路交汇处</span>
              <span class="price">参考单价：<span>3980</span>元 / m²</span>
              <span class="region">所属区域：城区</span>
            </div>
          </v-col>

          <v-col cols="12">
            <div class="building-title"><span>基本信息</span></div>
            <div class="building-info">
              <span>建筑类型：高层</span>
              <span>物业类型：住宅</span>
              <span>产权年限：70年</span>
              <span>装修标准：毛坯</span>
              <span>容积率：4.5</span>
              <span>绿化率：60%</span>
              <span>建筑面积：121642m²</span>
              <span>占地面积：24857m²</span>
              <span>规划户数：790户</span>
              <span>车位：284</span>
              <span>交通状况：公交12路、汽车总站、汽车东站、洞口高铁站</span>
            </div>
          </v-col>

          <v-col cols="12">
            <div class="building-title"><span>周边配套</span></div>
            <div class="building-info">
              <span>学校：金太阳幼儿园、鳌头幼儿园、城关一校、芙蓉小学、第九中学、第一中学</span>
              <span>医疗：县医院、妇幼保健院</span>
              <span>金融：工商银行、农业银行、建设银行、中国银行、湖南长沙银行</span>
            </div>
          </v-col>

          <v-col cols="12">
            <div class="building-title"><span>销售信息</span></div>
            <div class="building-info">
              <span>最新开盘时间：2019-10-28</span>
              <span>交房时间：2021-9-30</span>
              <span>楼盘地址：洞口华荣路与文昌南路交汇处</span>
            </div>
            <div class="building-intro">
              <span>
                南方花园位于洞口县汽车总站盘，占地约38亩，是洞口县目前在售仅有的围合式布局小区，超百米楼间距，上万平中庭绿化，诠释洞口县改善居住环境得高品质生活。
              </span>
              <span>建筑：12万方纯高层建筑，两梯三户两梯四户纯版式大平层，每个户型均带大阳台；</span>
              <span>布局：超百米楼间距点式楼栋围合式布局，既保障居家隐私条件，也充分满足采光、通风等条件；</span>
              <span>地段：城南核心发展区域，项目2公里范围内覆盖：好又多超市、县医院、裕峰花园酒店、法院、政务中心、汽车总站、高速出口等；</span>
              <span>教育：南方花园分配学校，主要就读芙蓉学校、城关一校，两大名校近在咫尺，自带书香气息，让您的孩子赢在起跑线上；</span>
              <span> 环境：超万平中庭园林景观。</span>
            </div>
          </v-col>
        </v-tab-item>

        <v-tab id="floor" href="#floor" style="color: #e3e3e3;" @click="onScrollTo">户型图</v-tab>
        <v-tab-item value="floor">
          <v-carousel hide-delimiter-background show-arrows-on-hover delimiter-icon="mdi-minus">
            <v-carousel-item v-for="(floor, index) in floors" :key="index" :src="floor.src" contain />
          </v-carousel>
        </v-tab-item>

        <v-tab id="purchase" href="#purchase" style="background-color: #ff5b5c; color: #e3e3e3;" @click="onScrollTo">团购</v-tab>
        <v-tab-item value="purchase">
          <v-col cols="12">
            <div class="form">
              <v-text-field v-model="name" :rules="nameRules" :counter="6" label="姓名" required></v-text-field>
              <v-text-field v-model="phone" :rules="phoneRules" :counter="11" label="电话" type="number" required></v-text-field>
            </div>

            <button class="submit">提交</button>
          </v-col>
        </v-tab-item>
      </v-tabs>
    </v-col>

    <div class="nav-bottom">
      <div class="contact">
        <v-btn class="mr-2" color="var(--acid-blue)" href="tel: 0739-7959999" style="color: #ffffff;" depressed large>
          <v-icon left dark>mdi-message</v-icon>
          置业顾问
        </v-btn>

        <v-btn class="mr-2" color="var(--acid-blue)" href="tel: 0739-7959999" style="color: #ffffff;" depressed large>
          <v-icon left dark>mdi-phone</v-icon>
          联系我们
        </v-btn>
      </div>
    </div>

    <div class="footer">
      <span class="copyright">©{{ new Date().getFullYear() }} nfhy.huijianfc.com</span>
      <span class="record">蜀ICP备140303392号</span>
    </div>
  </div>
</template>

<script>
  export default {
    name: 'Home',
    data() {
      return {
        color: '#2a765a',
        tab: null,
        name: '',
        nameRules: [(v) => !!v || '请输入您的姓名'],
        phone: '',
        phoneRules: [(v) => !!v || '请输入手机号', (v) => /^1[3-9]\d{9}$/.test(v) || '请输入正确的手机号'],
        items: [
          {
            tab: '效果图',
            content: [
              { src: require('../assets/images/effect/1.jpg') },
              { src: require('../assets/images/effect/2.jpg') },
              { src: require('../assets/images/effect/3.jpg') },
              { src: require('../assets/images/effect/4.jpg') },
              { src: require('../assets/images/effect/5.jpg') },
              { src: require('../assets/images/effect/6.jpg') },
            ],
          },
          {
            tab: '实景图',
            content: [
              { src: require('../assets/images/scenery/1.jpg') },
              { src: require('../assets/images/scenery/2.jpg') },
              { src: require('../assets/images/scenery/3.jpg') },
              { src: require('../assets/images/scenery/4.jpg') },
            ],
          },
        ],
        floors: [
          { src: require('../assets/images/floor/1.jpg') },
          { src: require('../assets/images/floor/2.jpg') },
          { src: require('../assets/images/floor/3.jpg') },
          { src: require('../assets/images/floor/4.jpg') },
        ],
      };
    },
    methods: {
      onScrollTo(e) {
        const ele = document.querySelector(`#${e.target.id}`);
        const scrollY = window.pageYOffset;
        const eleY = ele.getBoundingClientRect().top;
        const endPosition = scrollY + eleY;

        // +new Date() 隐式类型转换，日期 => 数字（时间戳）
        const startTime = +new Date();
        const duration = 300;

        function run() {
          // 每一帧的时间
          const time = +new Date() - startTime;

          // time / duration 表示滚动 150ms 需要多少帧
          // 以及每一帧在 Y 轴上滚动多少距离
          window.scrollTo(0, scrollY + eleY * (time / duration));
          run.timer = requestAnimationFrame(run);

          // 时间到了则表示滚动到了目标位置，取消动画
          if (time >= duration) {
            window.scrollTo(0, endPosition);
            cancelAnimationFrame(run.timer);
          }
        }

        requestAnimationFrame(run);
      },
    },
  };
</script>

<style lang="scss" scoped>
  .home {
    .page-bar {
      width: 100%;
      background-color: var(--white);
      display: flex;
      justify-content: center;
      align-items: center;
      padding: 0.625rem 0;

      img {
        width: 3.75rem;
        height: 3.75rem;
        object-fit: contain;
        margin-right: 0.3125rem;
      }

      .nfhy-bar-text {
        font-size: 24px;
      }
    }

    .building {
      margin-bottom: 55px;

      .building-title {
        border-left: 10px solid var(--acid-blue);
        border-bottom: 1px solid var(--acid-blue);
        height: 3.125rem;
        display: flex;
        align-items: center;

        span {
          margin-left: 5px;
          font-size: 18px;
          font-weight: bold;
        }
      }

      .building-info,
      .building-intro {
        display: flex;
        flex-direction: column;
        margin-left: 15px;
        padding: 10px 0;
        line-height: 2;
      }

      .submit {
        background-color: var(--acid-blue);
        color: var(--white);
        width: 100%;
        height: 55px;
        border-radius: 3px;
        margin-top: 10px;
      }
    }

    .nav-bottom {
      width: 100%;
      height: 55px;
      position: fixed;
      bottom: 0;
      left: 0;
      background-color: var(--white);
      display: flex;
      justify-content: flex-end;
      align-items: center;
      border-top: 1px solid #e1e4e8;
    }

    .footer {
      width: 100%;
      height: 50px;
      display: flex;
      justify-content: center;
      align-items: center;
      user-select: none;
      border-top: 1px solid #e1e4e8;
      margin-bottom: 55px;

      span.copyright {
        margin-right: 0.625rem;
      }
    }
  }
</style>

<style lang="scss">
  .v-tab--active {
    color: #ffffff !important;
  }
</style>
