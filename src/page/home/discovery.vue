<template lang="html">
  <div class="discovery">
    <!-- 头部 -->
    <div class="discovery_header">
    <mt-search  cancel-text="取消" placeholder="搜索感兴趣的内容"></mt-search>
    <a href="#"><span class="qr_code"><img src="../../assets/qr.png"></span></a>
    </div>
    <swiper :options="swiperOption" ref="mySwiper" class="discovery-all">
      <!-- slides -->
      <swiper-slide data-hash="discovery/content"><div class="nav_blank"></div><discovery-content></discovery-content></swiper-slide>
      <swiper-slide data-hash="discovery/community"><div class="nav_blank"></div><discovery-community></discovery-community></swiper-slide>
      <swiper-slide data-hash="discovery/focus"><div class="nav_blank"></div><discovery-focus></discovery-focus></swiper-slide>
      <div class="swiper-pagination swiper-pagination-bullets" slot="pagination"></div>
    </swiper>


  </div>
</template>
<script>
import Content from '../../components/discovery/content'
import Community from '../../components/discovery/community'
import Focus from '../../components/discovery/focus'
export default {
  components: {
    'discovery-content': Content,
    'discovery-community': Community,
    'discovery-focus': Focus
  },
   data() {
      return {
        selected: '发现',
        swiperOption: {
          // some swiper options/callbacks
          // 所有的参数同 swiper 官方 api 参数
          // ...
          initialSlide :0,
          slideToClickedSlide: true,
          direction : 'horizontal',
          autoHeight:true,
          scrollbar: {
            el: '.swiper-scrollbar'
          },
          hashNavigation: {
            // watchState: true,
          },
          pagination: {
            el: '.swiper-pagination',
            clickable: true,

            renderBullet(index, className) {
              var discoveryArr= ['内容','社区','关注'];
              return `<span class="${className} swiper-pagination-bullet-custom">${discoveryArr[index]}</span>`;

            }
          }
        }
      }
    },
    computed: {
      swiper() {
        return this.$refs.mySwiper.swiper
      }
    },
     mounted() {
    }

}
</script>

<style lang="stylus" scoped>
.discovery
  margin-bottom 40px
.discovery_header
  position fixed
  top 0
  z-index 1000
.qr_code
  position fixed
  right .3rem
  top .24rem
  width .6rem
  height .6rem
  background-color #fefefe
  z-index 1000
  display inline-block
.qr_code>img
  width 100%
  height 100%
.discovery-all
  position relative
.nav_blank
  width 100%
  height 70px
.swiper-pagination-bullets
  position fixed
  top 42px
  width 10rem
  height 30px
  z-index 1000
  text-align center
  line-height 30px
  font-size 14px
  color #000
.swiper-wrapper
  background-color red

</style>
<style>
/* 自定义导航 */
.swiper-pagination-bullet-custom {
    width: 3rem;
    height: 30px;
    background: #fefefe;
    border-radius: 0;
 }
 .swiper-pagination-bullet-custom.swiper-pagination-bullet-active {
    color: #FE5858;
    border-bottom: .01rem solid #FE5858
 }
 .swiper-slide {
   text-align: center
 }
</style>
