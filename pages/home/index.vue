<template>
  <div class="home">
    <myheader></myheader>
    <div class="continer">
      <div class="section_one">
        <div class="one_left">
          <div v-swiper:mySwiper="swiperOption">
            <div class="swiper-wrapper">
              <div class="swiper-slide" v-for="(banner,index) in banners" :key="index">
                <img :src="banner.src" class="banner_img" />
              </div>
            </div>

            <div class="swiper-pagination swiper-pagination-bullets"></div>
          </div>
        </div>

        <div class="one_right">
          <h2 class="from_title">评估退保成功率</h2>
          <div class="form">
            <myform></myform>
          </div>
        </div>
      </div>
      <div class="section_two">
        <div class="section_header">
          <span class="ch">保险知识</span>
          <div class="eng">Insurance knowledge</div>
        </div>
        <div class="section_inner">
          <div class="knowledge" v-for="(item,index) in insurance_klg" :key="index">
            <div class="klg">
              <img :src="item.img" alt class="knowledge_img" />
              <div class="knowledge_box">
                <h3 class="box_title">{{item.title}}</h3>
                <div class="inner">{{item.iner}}</div>
              </div>
            </div>
          </div>
        </div>
      </div>
      <div class="section_three">
        <div class="section_header">
          <span class="ch">我们的优势</span>
          <div class="eng">Our strengths</div>
        </div>
        <div class="section_inner">
            <ul class="ul_1">
              <li class="li_1">
                <ul class="li_lu1">
                  <li class="li1_li1"> 大数据支持提升成功概率</li>
                  <li class="li1_li2">专业团顾问</li>
                  
                </ul>
              </li>
              <li class="li_2">
                 <ul class="li_lu2">
                  <li class="li2_li2">严格保密制度</li>
                  <li class="li2_li1">极速高效,退保概率搞到98%</li>
                </ul>
              </li>
            </ul>
        </div>
      </div>
      <div class="section_four">
        <div class="section_header">
           <span class="ch">业务范围</span>
          <div class="eng">Scope of business</div>
        </div>
        <div class="section_inner">
          帮助用户及时止损,客户后知后觉,被诱导购买各种类型保险
        </div>
      </div>
      <div class="section_five">
        <div class="section_header">
           <span class="ch">业务办理流程</span>
          <div class="eng">Operation flow</div>
          
        </div>
        <div class="section_inner">
          自动化评估退保->资料录入->大数据支持帮助用户加速退保业务->完成协议->退保完成
        </div>
      </div>
    </div>
    <myfooter></myfooter>
  </div>
</template>

<script>
import myheader from "@/components/header.vue";
import myform from "@/components/form.vue";
import myfooter from "@/components/footer.vue";
export default {
  components: {
    myheader,
    myform,
    myfooter
  },
  data() {
    return {
      form: [
        {
          type: "input"
        },
        {
          type: "select"
        }
      ],
      insurance_klg: [
        //保险知识
        {
          img: require("@/assets/insurace_lkg/1.jpg"),
          title: "你不得不知道的人身保险合同变更小知",
          iner:
            "保险学问千千万，一不小心就受骗。我们为了自己和家人的健康、保障而买一份保险。买完保险，我们不仅要按时交保费，而且要充分了解自己所拥有的权力，充分利用，保障自己。"
        },
        {
          img: require("@/assets/insurace_lkg/2.jpg"),
          title: "你不得不知道的人身保险合同变更小知,我们为了自己和家人的健康",
          iner:
            "保险学问千千万，一不小心就受骗。我们为了自己和家人的健康、保障而买一份保险。买完保险，我们不仅要按时交保费，而且要充分了解自己所拥有的权力，充分利用，保障自己。"
        },
        {
          img: require("@/assets/insurace_lkg/3.jpg"),
          title: "你不得不知道的人身保险合同变更小知",
          iner:
            "保险学问千千万，一不小心就受骗。我们为了自己和家人的健康、保障而买一份保险。买完保险，我们不仅要按时交保费，而且要充分了解自己所拥有的权力，充分利用，保障自己。"
        },
        {
          img: require("@/assets/insurace_lkg/4.jpg"),
          title: "你不得不知道的人身保险合同变更小知",
          iner:
            "保险学问千千万，一不小心就受骗。我们为了自己和家人的健康、保障而买一份保险。买完保险，我们不仅要按时交保费，而且要充分了解自己所拥有的权力，充分利用，保障自己。"
        },
        {
          img: require("@/assets/insurace_lkg/5.jpg"),
          title: "你不得不知道的人身保险合同变更小知",
          iner:
            "保险学问千千万，一不小心就受骗。我们为了自己和家人的健康、保障而买一份保险。买完保险，我们不仅要按时交保费，而且要充分了解自己所拥有的权力，充分利用，保障自己。"
        },
        {
          img: require("@/assets/insurace_lkg/6.jpg"),
          title: "你不得不知道的人身保险合同变更小知",
          iner:
            "保险学问千千万，一不小心就受骗。我们为了自己和家人的健康、保障而买一份保险。买完保险，我们不仅要按时交保费，而且要充分了解自己所拥有的权力，充分利用，保障自己。"
        },
        {
          img: require("@/assets/insurace_lkg/7.jpg"),
          title: "你不得不知道的人身保险合同变更小知",
          iner:
            "保险学问千千万，一不小心就受骗。我们为了自己和家人的健康、保障而买一份保险。买完保险，我们不仅要按时交保费，而且要充分了解自己所拥有的权力，充分利用，保障自己。"
        },
        {
          img: require("@/assets/insurace_lkg/8.jpg"),
          title: "你不得不知道的人身保险合同变更小知",
          iner:
            "保险学问千千万，一不小心就受骗。我们为了自己和家人的健康、保障而买一份保险。买完保险，我们不仅要按时交保费，而且要充分了解自己所拥有的权力，充分利用，保障自己。"
        }
      ],
      banners: [
        {
          src: require("@/assets/IMG_1983.JPG")
        },
        {
          src: require("@/assets/IMG_1977.JPG")
        },
        {
          src: require("@/assets/IMG_1974.JPG")
        }
      ],
      swiperOption: {
        loop: true,
        autoplay: true,
        centeredSlides: true,
        spaceBetween: 30,
        pagination: {
          el: ".swiper-pagination",
          dynamicBullets: true
        },
        on: {
          slideChange() {
            console.log("onSlideChangeEnd", this);
          },
          tap() {
            console.log("onTap", this);
          }
        }
      }
    };
  }
};
</script>

<style lang='scss' scoped>
@import "./index.scss";
</style>