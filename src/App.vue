
<template>
  <div id="app">
    <LottoHeader></LottoHeader>
    <LottoInput v-on:getWinningNumber="getWinningNumber"></LottoInput>
    <LottoResult v-bind:propsdata="winningNumList"></LottoResult>
    <LottoSummary v-bind:propsdata="winningNumTimes"></LottoSummary>
  </div>
</template>


<script>
export default {
  components:{
    'LottoHeader' : LottoHeader,
    'LottoInput' : LottoInput,
    'LottoResult' : LottoResult,
    'LottoSummary' : LottoSummary
  },
  data(){
    return{
      winningNumTimes:[],
      winningNumList:[],
      weeks: 1
    }
  },
  methods:{
    getWinningNumber(weeks){
      /* update winningNumTimes and winningNumList */
      console.log(weeks);
      axios.get('https://www.dhlottery.co.kr/common.do?method=getLottoNumber&drwNo=1000')
      .then(function(response){
        console.log(response);
      });
    }
  },
  created(){

  }
}
import LottoHeader from './components/LottoHeader.vue'
import LottoInput from './components/LottoInput.vue'
import LottoResult from './components/LottoResult.vue'
import LottoSummary from './components/LottoSummary.vue'
import axios from "axios";
</script>

<style>
body{
  text-align: center;
  background-color: #f6f6f8;
}
input{
  border-style: groove;
  width: 200px;
}
button{
  border-style: groove;
}
.shadow{
  box-shadow: 5px 10px 10px rgba(0,0,0,0.03)
}
</style>
