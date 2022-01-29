<template>
  <div class="inputBox shadow">
    <input type="text" v-model="weeks" placeholder="Type weeks you want to do" v-on:keyup.enter="addTodo">
    <span class="addContainer" v-on:click="setWeeks">
      <i class="addBtn fas fa-plus" aria-hidden="true"></i>
    </span>
<modal v-if="showModal" @close="showModal = false">
  <h3 slot="header">Alarm</h3>
  <span slot="footer" @click="showModal = false">
  Please insert number
    <i class="closeModalBtn fas fa-times" aria-hidden="true"></i>
  </span>
</modal>
  </div>
</template>

<script>
import Modal from './common/Modal.vue'
export default{
  data(){
    return {
      newTodoItem: '',
      showModal: false
    }
  },
  methods:{
    setWeeks(){
      if(this.weeks != "")
      {
        var value = this.weeks && this.weeks.trim();
        this.$emit('getWinningNumber', value);
        this.clearInput();
      }else{
        this.showModal = !this.showModal;
      }
    },
    clearInput(){
      this.weeks = '';
    }
  },
  components:{
    Modal: Modal
  }
}
</script>

<style scoped>
input:focus{
  outline:none;
}
.inputBox{
  position: absolute;
  width: 184px;
  height: 35px;
  left: 54px;
  top: 102px;
  background: #FFFFFF;
  box-shadow: 0px 4px 4px rgba(0, 0, 0, 0.25);
}
.inputBox input{
  border-style: none;
  font-size:0.9rem;
  position: absolute;
  width: 97px;
  height: 29px;
  left: 223px;
  top: 108px;

  font-family: Roboto;
  font-style: normal;
  font-weight: normal;
  line-height: 14px;
  text-align: center;

  color: #000000;
}
.addContainer{
  float:right;
  background:linear-gradient(to right, #6478fb, #8763fb);
  display:block;
  width:3rem;
  border-radius:0 5px 5px 0;
}
.addBtn{
  color:white;
  vertical-align: middle;
}
</style>
