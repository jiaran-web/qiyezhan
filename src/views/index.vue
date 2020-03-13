<template>
<div style="float: left;">
  <div class="main_middle">
    <div class="main_tit main_M_tit">
        <h3>公司简介<i>ABOUT US</i></h3>
          <router-link :to="'/contact'">更多&gt;&gt;</router-link>
      </div>
      <div class="main_M_intr">
        <img src="@/assets/img/intr.jpg" width="140" height="140" alt="公司简介" />
          <p>{{ indexData.comInt}}</p>
      </div>
      <div class="main_tit main_M_tit">
        <h3>产品简介<i>PRODUCTS</i></h3>
          <router-link :to="'/product/list'">更多&gt;&gt;</router-link>
      </div>
      <div class="main_pro_list">
        <div class="main_pro_div">
              <dl v-for="(item,index) in indexProductData" :key="item.id">
                  <dt><router-link :to="'/product/detail/'+item.id"><img src="@/assets/img/1.jpg" width="125" height="125" alt="产品1" /></router-link></dt>
                  <dd><router-link :to="'/product/detail/'+item.id">{{item.title}}</router-link></dd>
              </dl>
         </div>
      </div>
  </div>
  <div class="main_right">
    <div class="main_tit main_R_tit">
        <h3>行业资讯<i>News</i></h3>
          <router-link :to="'/news/list'">更多&gt;&gt;</router-link>
      </div>
      <div class="main_R_flash">
        <ul class="m_R_img">
            <li><router-link :to="'/news/list'"><img width="190" height="190" src="@/assets/img/1.jpg" alt="图" /></router-link></li>
              <li class="m_R_imgCur"><router-link :to="'/news/list'"><img width="190" height="190" src="@/assets/img/intr.jpg" alt="图" /></router-link></li>
              <li><router-link :to="'/news/list'"><img width="190" height="190" src="@/assets/img/contact.jpg" alt="图" /></router-link></li>
          </ul>
          <ul class="m_R_btn">
            <li>1</li>
              <li class="m_R_btnCur">2</li>
              <li>3</li>
          </ul>
      </div>
      <ul class="main_R_news">
          <li v-for="(item,index) in indexNewsData" :key="item.id"><i>&gt;</i><router-link :to="'/news/detail/'+item.id">{{item.title}}</router-link></li>
          
      </ul>
  </div>
</div>
</template>

<script>
import { getIndex } from '@/api/index';

export default {
  data () {
    return {
      indexData: {},
      indexNewsData:{},
      indexProductData:{},
    }
  },
  created(){
    this.getIndex();
  },
  methods: {
    getIndex(){
      var _this = this;
      getIndex({
        params: {
          a: 1
        },
      }).then(function(res){
        console.log(res);
        _this.indexData = res.data.data;
        _this.indexNewsData = res.data.data.data1;
        _this.indexProductData = res.data.data.data2;
      }).catch(function(err){
        console.log(err);
      });
    },
  },
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
