<template>
  <div class="hello">
      <div id="header">
        <p class="title">测一测</p>
        <p class="title">您是否能成为福布斯风云人物</p>
        <p class="userMes" style="margin-top:.2rem">您现在的投资金额为
          <input ref="input1" class="num" type="number" oninput="if(value.length>5)value=value.slice(0,5)">
          万人民币</p>
        <p class="userMes">您的年龄为
          <input ref="input2" class="num" type="number" oninput="if(value.length>5)value=value.slice(0,5)">
          岁，预测
          <input ref="input3" class="num" type="number" oninput="if(value.length>5)value=value.slice(0,5)">
          年后的财富值</p>
      </div>

      <div id="content">
        <div class="ploy">
          <img src="../../static/images/wenzi_1@2x.png" alt="">
        </div>
        <div class="ranges">
          <p>
            低风险投资占比
            <span>{{this.rangeValue1}}%</span>
            <mt-range
              class="my-range"
              v-model="rangeValue1"
              :min="1"
              :max='100-this.rangeValue3-this.rangeValue5'
              :step="1"
              :bar-height="4">
            </mt-range>
          </p>
          <p>
            复利年化收益率
            <span>{{this.rangeValue2}}%</span>
            <mt-range
              class="my-range"
              v-model="rangeValue2"
              :min="1"
              :max="7"
              :step="1"
              :bar-height="4">
            </mt-range>
          </p>
          <p>      
            中风险投资占比
            <span>{{this.rangeValue3}}%</span>
            <mt-range
              class="my-range"
              v-model="rangeValue3"
              :min="1"
              :max="100-this.rangeValue1-this.rangeValue5"
              :step="1"
              :bar-height="4">
            </mt-range>
          </p>
          <p>  
            复利年化收益率
            <span>{{this.rangeValue4}}%</span>
            <mt-range
              class="my-range"
              v-model="rangeValue4"
              :min="7"
              :max="13"
              :step="1"
              :bar-height="4">
            </mt-range>
          </p>
          <p>         
            高风险投资占比
            <span>{{this.rangeValue5}}%</span>
            <mt-range
              class="my-range"
              v-model="rangeValue5"
              :min="1"
              :max="100-this.rangeValue1-this.rangeValue3"
              :step="1"
              :bar-height="4">
            </mt-range>
          </p>
          <p>
            复利年化收益率
            <span>{{this.rangeValue6}}%</span>
            <mt-range
              class="my-range"
              v-model="rangeValue6"
              :min="13"
              :max="20"
              :step="1"
              :bar-height="4">
            </mt-range>
          </p>
        </div>
      </div>
      <div id="footer">
        <mt-button>开启未来财富之门</mt-button>
      </div>
  </div>
</template>

<script>
export default {
  name: "HelloWorld",
  data() {
    return {
      rangeValue1: 1,
      rangeValue2: 1,
      rangeValue3: 1,
      rangeValue4: 7,
      rangeValue5: 1,
      rangeValue6: 13,
      popupVisible:30,
      sum:'',
    };
  },
  methods:{
      abc(){
        this.sum= this.$refs.input1.value*this.rangeValue1*(Math.pow((1+this.rangeValue2/100),this.$refs.input3.value))+this.$refs.input1.value*this.rangeValue3*(Math.pow((1+this.rangeValue4/100),this.$refs.input3.value))+this.$refs.input1.value* this.rangeValue5*Math.pow((1+this.rangeValue6/100),this.$refs.input3.value)
        if(this.sum<=300){
            if(this.$refs.input2.value>60){ 
              
            }else if(this.$refs.input2.value>19&&this.$refs.input2.value<60){

            }else if(this.$refs.input2.value<=18&&this.$refs.input2.value>0){

            }
        }else if(this.sum<=1000&&this.sum>300){
          if(this.$refs.input2.value>60){

          }else if(this.$refs.input2.value<=60&&this.$refs.input2.value>19){

          }else if(this.$refs.input2.value<=18&&this.$refs.input2.value>0){

          }
        }
      
      }
  },
  updated(){
    // console.log(this)
  },
  mounted(){
    console.log(this)
  }


  // watch:{
  //     rangeValue1 : function(val,oldval){
  //        val<=100-this.rangeValue3-this.rangeValue5
  //       this.rangeValue1 = val
  //     },
  //     rangeValue3 : function(val,oldval){
  //        val<=100-this.rangeValue1-this.rangeValue5
  //         this.rangeValue3 = val
  //     },
  //     rangeValue5 : function(val,oldval){
  //         val<=100-this.rangeValue3-this.rangeValue1
  //          this.rangeValue5 = val
  //     },
  // },
//1212211212121212


  // watch: {
  //   rangeValue1: {
  //     handler: function (n, old) {
  //       if (Number(this.rangeValue1) + Number(this.rangeValue3) + Number(this.rangeValue5) <100) {
  //         n = 100 - Number(this.rangeValue3) - Number(this.rangeValue5)
  //       }
  //     }
  //   },
  //  rangeValue3: {
  //     handler: function (n, old) {
  //       if (Number(this.rangeValue1) + Number(this.rangeValue3) + Number(this.rangeValue5) < 100) {
  //         n = 100 - Number(this.rangeValue1) - Number(this.rangeValue5)
  //       }
  //     }
  //   },
  //   rangeValue5: {
  //     handler: function (n, old) {
  //       if (Number(this.rangeValue1) + Number(this.rangeValue3) + Number(this.rangeValue5) < 100) {
  //         n = 100 - Number(this.rangeValue3) - Number(this.rangeValue1)
  //       }
  //     }
  //   },
}
</script>


<style>
#hello {
  width: 100%;
  height: 100%;
}
#header {
  width: 100%;
  height: 5rem;
  background: url("../../static/images/bg26@2x.png") no-repeat;
  background-size: cover;
  padding: 1.89rem 0.6rem 0;
}
#header .title {
  font-weight: bold;
  font-size: 0.36rem;
  color: white;
}
#header .num {
  width: 0.6rem;
  height: 0.4rem;
  padding-top: 0.1rem;
  border: 0;
  border-bottom: 0.9px solid black;
  outline: none;
  text-align: center;
  background-color: transparent;
}
#header .userMes {
  color: #333;
  font-size: 0.2rem;
  font-weight: bold;
  font-family: "MicrosoftYaHei";
  line-height: 0.55rem;
}
#content {
  width: 100%;
  height: 5rem;
  padding: 0.6rem;
}
#content .ploy img {
  width: 1.98rem;
  height: 0.28rem;
  margin-bottom: 0.2rem;
}
#content .ranges {
  width: 100%;
  height: 4rem;
}
#content p {
    font-size: 0.2rem;
    font-family: '微软雅黑';
  height: .7rem;
  display: flex;
  align-items: center;
  justify-content: space-between;

}
#content .ranges .mt-range {
  width: 4.3rem;
  float: right;
}
#content .ranges span{
  font-weight: normal;
  color: #F1D44C;
}
#content .ranges .mt-range-runway {
  border-radius: .2rem;
  right: -5%;
}
#content .ranges .mt-range-progress {
  background: -o-linear-gradient(left, yellow, orange);
  background: -webkit-linear-gradient(left, yellow, orange);
  border-radius: 10px;
}
#content .ranges .mt-range-thumb {
  width: 0.3rem;
  height: 0.3rem;
  top: 7px;
}
#footer{
  width: 100%;
  padding: 0 0.6rem;
  margin-top: 1rem
}
#footer .mint-button{
  width: 100%;
  border-radius: 2rem;
  background: #F1D44C;
  font-size: .36rem;
  color: #fff;
  font-weight: bold;
  line-height: .2rem
}
</style>
