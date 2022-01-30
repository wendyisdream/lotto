<template>
  <div class="inputBox shadow">
    <input type="text" v-model="weeks" placeholder=" Type weeks" v-on:keyup.enter="setWeeks">
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
  width: 183px;
  height: 35px;
  left: 96px;
  top: 101px;

  background: #FFFFFF;
  box-shadow: 0px 4px 4px rgba(0, 0, 0, 0.25);
}
.inputBox input{
  border-style: none;
  font-size: 0.9rem;
}
.addContainer{
  position:fixed;
  width: 37px;
  height: 35px;
  left: 242px;
  top: 99px;

  background: linear-gradient(to right, #FF99aa, #FE3394);
  display: block;
  border-radius:0 5px 5px 0;
}
.addBtn{
  color:white;
  vertical-align: middle;
}
</style>
