<template>
  <div class="all">
    <my-top/>
    <div class="item">
      <div class="content">
          <div class="middle">
              <ul class="clearfix title">
                  <li class="fll title-select" :class="{active: seletedIndex == 0}"
                        @click="seletedIndex=0">找二手房</li>
                  <li class="fll title-select" :class="{active: seletedIndex == 1}"
                        @click="seletedIndex=1">找新房</li>
                  <li class="fll title-select" :class="{active: seletedIndex == 2}"
                        @click="seletedIndex=2">找租房</li>
                  <li class="fll title-select" :class="{active: seletedIndex == 3}"
                        @click="seletedIndex=3">找学区房</li>
                  <li class="fll title-select" :class="{active: seletedIndex == 4}"
                        @click="seletedIndex=4">找小区</li>
              </ul>
              <div class="map">
                  <input type="text" :placeholder="placeholderText" v-model="searchText">
                  <button id="map-btn1" @click="seach">搜索</button>
                  <button id="map-btn2" v-if="seletedIndex<4" >地图找房</button>
              </div>

              <div class="swipe-bottom" style="height: 30px">

                  <div class="headline-wrap" style="float: left;">
                      <img src="../assets/img/头条.png">
                  </div>

                  <div v-swiper:headlineSwiper="headlineOption"
                       style="line-height: 30px;overflow: hidden;float: left;
                       height: 30px;margin-left: 15px">
                      <div class="swiper-wrapper">
                          <div class="swiper-slide" v-for="(item,index) in headlineData">
                              <nuxt-link to="#" class="swiper-link" key="index"
                              style="font-size: 16px;color: #fff">{{item.title}}</nuxt-link>
                          </div>
                      </div>
                  </div>

              </div>

          </div>

          <div v-swiper:mySwiper="swiperOption" style="height: 100%;overflow: hidden;">
              <div class="swiper-wrapper">
                  <div class="swiper-slide" v-for="banner in banners">
                      <img :src="'http://www.fooju.cn/'+banner.picurl" style="
                      height: 535px;width: 100%;">
                  </div>
              </div>
          </div>


      </div>

        <div class="content-item">
            <div class="seach">
                <div class="seach-1">
                    <img src="../assets/img/seach-1.png">
                    <p id="door">查门店</p>
                    <p id="seek">查优质门店</p>
                </div>
                <div class="seach-1">
                    <img src="../assets/img/seach-2.png">
                    <p id="door">在线委托</p>
                    <p id="seek">有问题我们帮你</p>
                </div>
                <div class="seach-1">
                    <img src="../assets/img/seach-3.png">
                    <p id="door">地图找房</p>
                    <p id="seek">地图找房</p>
                </div>
                <div class="seach-1">
                    <img src="../assets/img/seach-4.png">
                    <p id="door">福局百科</p>
                    <p id="seek">看百科了解更多</p>
                </div>
            </div>
            <div class="house">
                <div class="house-img">
                    <img src="../assets/img/house-1.png">
                </div>
                <div class="house-img">
                    <img src="../assets/img/house-2.png">
                </div>
                <div class="house-img">
                    <img src="../assets/img/house-3.png">
                </div>
            </div>

            <div class="new-house">
                <p id="new-up">
                    <span id="new-up-l">精品新房</span>
                    <a href="" id="new-up-r">更多新房 ></a>

                </p>
                <p id="new-down">在这里为您寻觅一个新家</p>
            </div>
            <div class="good-house-1">
                <div class="house1">
                    <img src="../assets/img/zjbg-1.jpg">
                    <p>
                        <span id="house1-l">呼和浩特亿利生态城</span>
                        <span id="house1-r">0元/平</span>
                    </p>
                </div>
                <div class="house0">
                    <img src="../assets/img/zjbg-2.jpg">
                    <p>
                        <span id="house0-l">盛世国际</span>
                        <span id="house0-r">8800元/平</span>
                    </p>
                </div>
                <div class="house1">
                    <img src="../assets/img/zjbg-3.jpg">
                    <p>
                        <span id="house1-l">荷塘月色</span>
                        <span id="house1-r">8500元/平</span>
                    </p>
                </div>
            </div>

            <div class="second-hand">
                <p id="new-up">
                    <span id="new-up-l">二手优品</span>
                    <a href="" id="new-up-r">更多二手房 ></a>
                </p>
                <p id="new-down">生活因为宽广，才会不断延伸</p>
            </div>
            <div class="good-house-2">
                <div class="house2">
                    <p id="house2-0">118万</p>
                    <div id="img-scale">
                        <img src="../assets/img/zjbg-1.jpg">
                    </div>
                    <p id="house2-l">北辰新领地 三居 可按揭</p>
                    <p id="house2-r">3室2厅2卫 128.80㎡ </p>
                </div>
                <div class="house0">
                    <p id="house2-0">118万</p>
                    <div id="img-scale">
                        <img src="../assets/img/zjbg-2.jpg">
                    </div>
                    <p id="house2-l">北辰新领地 三居 可按揭</p>
                    <p id="house2-r">3室2厅2卫 128.80㎡ </p>
                </div>
                <div class="house2">
                    <p id="house2-0">118万</p>
                    <div id="img-scale">
                        <img src="../assets/img/zjbg-3.jpg">
                    </div>
                    <p id="house2-l">北辰新领地 三居 可按揭</p>
                    <p id="house2-r">3室2厅2卫 128.80㎡ </p>
                </div>
            </div>

            <div class="rent-house">
                <p id="new-up">
                    <span id="new-up-l">精品租房</span>
                    <a href="" id="new-up-r">更多租房 ></a>
                </p>
                <p id="new-down">与其等待，不如坐享繁华</p>
            </div>
            <div class="good-house-3">
                <div class="house3">
                    <div id="img-scale">
                        <img src="../assets/img/zjbg-1.jpg">
                    </div>
                    <p id="house3-t">阳光馨苑小区 出售</p>
                    <p id="house3-b">
                        <span id="house3-b-l">3室2厅2卫 128.80㎡</span>
                        <span id="house3-b-r">1100元/月</span>
                    </p>
                </div>
                <div class="house0">
                    <div id="img-scale">
                        <img src="../assets/img/zjbg-2.jpg">
                    </div>
                    <p id="house3-t">北辰新领地 三居 可按揭</p>
                    <p id="house3-b">
                        <span id="house3-b-l">3室2厅2卫 128.80㎡</span>
                        <span id="house3-b-r">1100元/月</span>
                    </p>
                </div>
                <div class="house3">
                    <div id="img-scale">
                        <img src="../assets/img/zjbg-3.jpg">
                    </div>
                    <p id="house3-t">北辰新领地 三居 可按揭</p>
                    <p id="house3-b">
                        <span id="house3-b-l">3室2厅2卫 128.80㎡</span>
                        <span id="house3-b-r">1100元/月</span>
                    </p>
                </div>
            </div>
        </div>

    </div>

    <my-sidebar/>
    <my-footer/>
  </div>
</template>

<script>
    import api from '~/mainApi/index'
    import axios from '~/plugins/axios'
    import MySidebar from '../components/sidebar'
    import MyFooter from '~/components/Footer.vue'
    import MyTop from '../components/top'
    export default {
        name:"index",
        components:{
            MyFooter,MyTop,MySidebar
        },
        data(){
            return{
                showMap:"",
                searchText:"",
                swiperOption: {
                    autoplay: false
                },
                headlineOption: {
                    autoplay: true,
                    direction: 'vertical',
                    loop: true
                },
                seletedIndex: 0,
                placeholderText: "输入小区名查找二手房"
            }
        },
        async asyncData() {
            let bannerData =
                await axios.get(api.paramToUrl(api.adLists,{type: 0,position:0}));
            // console.log(bannerData.data);
            let headlineData = await axios.get(api.paramToUrl(api.encyTop, {page_num: 0,page_size:10}))
            return {
                banners: bannerData.data.data,
                headlineData:headlineData.data.datas[0],
            }
        },
        watch: {
            seletedIndex(newValue, oldValue) {
                switch (newValue){
                    case 0:
                        this.placeholderText = "输入小区名查找二手房";
                        break;
                    case 1:
                        this.placeholderText = "输入楼盘名进行搜索";
                        break;
                    case 2:
                        this.placeholderText = "输入小区名可以查找出租的房屋";
                        break;
                    case 3:
                        this.placeholderText = "输入小区名搜索学区房";
                        break;
                    case 4:
                        this.placeholderText = "输入小区名搜索小区";
                        break;
                }
            }
        },
        methods:{
            seach(){
                let selected = this.seletedIndex;
                console.log(selected);
                switch(selected){
                    case 0:
                        this.$router.push({name: "secondSchoolHomesList",query: {q: this.searchText}})
                }
            }
        }
    }
</script>

<style scoped lang="less">
  *{
    padding: 0;
    margin: 0;
  }
  button{
      outline: none;
      cursor: pointer;
  }
  a{
    text-decoration: none;
  }
 .all{
  .item {
      .middle{
          height: 180px;
          width: 1050px;
          z-index: 998;
          /*position:absolute;*/
          /*left:0; right:0;*/
          /*margin:auto;*/
          position: absolute;
          left: 48%; top: 75%;
          transform: translate(-50%, -50%);
          .title{
              .title-select{
                  position: relative;
                  display: inline;
                  color: #fff;
                  font-size: 16px;
                  padding: 25px 20px 25px 0;
                  margin: 0 5px 0 0;
                  cursor: pointer;
              }
          }
          .title .active::after {
              content: "";
              display: block;
              position: absolute;
              bottom: 0;
              left: 35%;
              transform: translateX(-50%);
              border: 10px solid transparent;
              border-bottom: 10px solid #fff;
          }
          .title .active{
              font-weight: 600;
          }
          .map{
              input{
                  outline:none;
                  padding-left: 15px;
                  height: 60px;
                  margin-bottom: 2px;
                  width: 720px;
                  border-radius: 3px;
                  border: none;
              }
              #map-btn1{
                  margin:  0;
                  height: 58px;
                  width: 140px;
                  border: none;
                  background: brown;
                  font-size: 18px;
                  color: white;
                  border-radius: 3px;
              }
              #map-btn2{
                  margin:  0 5px;
                  height: 58px;
                  width: 140px;
                  border: none;
                  background: blueviolet;
                  font-size: 18px;
                  color: white;
                  border-radius: 3px;
              }
          }
          .swipe-bottom{
              font-size: 18px;
              margin-top: 78px;
              color: white;
          }
      }
      .swiper-wrapper {
          position: relative;
          height: 535px;
          width: 100%;
      }

      .content-item{
          width: 1100px;
          margin: 0 auto;
          .seach {
              display: table;
              padding-top: 50px;
              height: 190px;
              margin: 0 auto;
              .seach-1 {
                  cursor: pointer;
                  display: table-cell;
                  text-align: center;
                  padding: 0 40px;
                  width: 200px;
                  margin: 0 40px;
                  #door {
                      font-size: 20px;
                      margin: 16px 0 0 0;
                  }
                  #seek {
                      color: #555;
                      font-size: 14px;
                      margin: 5px 0;
                  }
              }
          }
          .house {
              display: table;
              clear: both;
              height: 280px;
              margin: 10px auto;
              .house-img{
                  display: table-cell;
                  text-align: center;
                  img {
                      width: 300px;
                      height: 225px;
                      margin-right:100px ;
                  }
              }
          }
          .new-house {
              margin: 0;
              #new-up {
                  margin-bottom: 15px;
                  #new-up-l {
                      font-weight: bold;
                      font-size: 30px;
                  }
                  #new-up-r {
                      color: #aaa;
                      float: right;
                      font-size: 16px;
                      line-height: 34px;
                  }
              }
              #new-down {
                  margin: 0 0 0 0;
                  color: #7f828b;
              }
          }
          .good-house-1 {
              height: 320px;
              margin: 10px auto 0 auto;
              .house1 {
                  overflow: hidden;
                  float: left;
                  height: 255px;
                  width: 337px;
                  img {
                      height: 255px;
                      width: 337px;
                      transition: all 0.6s;
                  }
                  img:hover{
                      transform:scale(1.1);//设置缩放比例
                  }
                  p {
                      position: relative;
                      width: 337px;
                      height: 26px;
                      font-size: 16px;
                      line-height: 26px;
                      background-color: rgba(0, 0, 0, 0.5);
                      color: white;
                      margin-top: -30px;
                      #house1-l {
                          margin-left: 10px;
                      }
                      #house1-r {
                          position: absolute;
                          right: 10px;
                      }
                  }
              }
              .house0 {
                  overflow: hidden;
                  float: left;
                  height: 255px;
                  width: 337px;
                  margin: 0 44px;
                  img {
                      height: 255px;
                      width: 337px;
                      transition: all 0.6s;
                  }
                  img:hover{
                      transform:scale(1.1);//设置缩放比例
                  }
                  p {
                      position: relative;
                      width: 337px;
                      height: 26px;
                      line-height: 26px;
                      font-size: 16px;
                      background-color: rgba(0, 0, 0, 0.5);
                      color: white;
                      margin-top: -30px;
                      #house0-l {
                          margin-left: 10px;
                      }
                      #house0-r {
                          position: absolute;
                          right: 10px;
                      }
                  }
              }
          }
          .second-hand {
              margin: 0;
              #new-up {
                  margin-bottom: 15px;
                  #new-up-l {
                      font-weight: bold;
                      font-size: 30px;
                  }
                  #new-up-r {
                      color: #aaa;
                      float: right;
                      font-size: 16px;
                      line-height: 34px;
                  }
              }
              #new-down {
                  margin: 0 0 0 0;
                  color: #7f828b;
              }
          }
          .good-house-2 {
              height: 380px;
              margin-top: 10px;
              .house2 {
                  position: relative;
                  float: left;
                  height: 300px;
                  width: 340px;
                  margin: 0;
                  #img-scale{
                      overflow: hidden;
                      width: 340px;
                      height: 255px;
                      img {
                          height: 255px;
                          width: 340px;
                          transition: all 0.6s;
                      }
                      img:hover{
                          transform:scale(1.1);//设置缩放比例
                      }
                  }
                  #house2-0 {
                      position: absolute;
                      top: 14px;
                      left: 0;
                      z-index: 998;
                      line-height: 45px;
                      padding-left: 8px;
                      color: white;
                      font-size: 20px;
                      width: 92px;
                      height: 45px;
                      background: red;
                  }
                  #house2-l {
                      clear: both;
                      margin: 10px 0;
                  }
                  #house2-r {
                      color: #7f828b;
                      font-size: 14px;
                      margin: 10px 0;
                  }

              }
              .house0 {
                  position: relative;
                  float: left;
                  height: 300px;
                  width: 340px;
                  margin: 0 40px;
                  #img-scale{
                      overflow: hidden;
                      width: 340px;
                      height: 255px;
                      img {
                          height: 255px;
                          width: 340px;
                          transition: all 0.6s;
                      }
                      img:hover{
                          transform:scale(1.1);//设置缩放比例
                      }
                  }
                  #house2-0 {
                      position: absolute;
                      top: 14px;
                      left: 0;
                      z-index: 998;
                      line-height: 45px;
                      padding-left: 8px;
                      color: white;
                      font-size: 20px;
                      width: 92px;
                      height: 45px;
                      background: red;
                  }
                  #house2-l {
                      clear: both;
                      margin: 10px 0;
                  }
                  #house2-r {
                      color: #7f828b;
                      font-size: 14px;
                      margin: 10px 0;
                  }

              }
          }
          .rent-house {
              margin: 0;
              #new-up {
                  margin-bottom: 15px;
                  #new-up-l {
                      font-weight: bold;
                      font-size: 30px;
                  }
                  #new-up-r {
                      color: #aaa;
                      float: right;
                      font-size: 16px;
                      line-height: 34px;
                  }
              }
              #new-down {
                  margin: 0 0 0 0;
                  color: #7f828b;
              }
          }
          .good-house-3 {
              height: 380px;
              margin-top: 10px;
              .house3 {
                  position: relative;
                  float: left;
                  height: 295px;
                  width: 340px;
                  margin: 0;
                  #img-scale{
                      width: 340px;
                      height: 255px;
                      overflow: hidden;
                      img {
                          height: 255px;
                          width: 340px;
                          transition: all 0.6s;
                      }
                      img:hover{
                          transform:scale(1.1);//设置缩放比例
                      }
                  }
                  #house3-0 {
                      font-size: 20px;
                      position: absolute;
                      top: 14px;
                      line-height: 45px;
                      padding-left: 8px;
                      color: white;
                      width: 92px;
                      height: 45px;
                      background: red;
                  }
                  #house3-t {
                      clear: both;
                      margin: 10px 0;
                  }
                  #house3-b {
                      position: relative;
                      color: #7f828b;
                      font-size: 14px;
                      margin: 10px 0 10px 1px;
                      #house3-b-r {
                          color: red;
                          position: absolute;
                          right: 2px;
                      }
                  }
              }
              .house0 {
                  position: relative;
                  float: left;
                  height: 295px;
                  width: 340px;
                  margin: 0 40px;
                  #img-scale{
                      width: 340px;
                      height: 255px;
                      overflow: hidden;
                      img {
                          height: 255px;
                          width: 340px;
                          transition: all 0.6s;
                      }
                      img:hover{
                          transform:scale(1.1);//设置缩放比例
                      }
                  }
                  #house3-0 {
                      font-size: 20px;
                      position: absolute;
                      top: 14px;
                      line-height: 45px;
                      padding-left: 8px;
                      color: white;
                      width: 92px;
                      height: 45px;
                      background: red;
                  }
                  #house3-t {
                      clear: both;
                      margin: 10px 0;
                  }
                  #house3-b {
                      position: relative;
                      color: #7f828b;
                      font-size: 14px;
                      margin: 10px 0 10px 1px;
                      #house3-b-r {
                          color: red;
                          position: absolute;
                          right: 2px;
                      }
                  }
              }
          }
      }

  }
}

</style>





