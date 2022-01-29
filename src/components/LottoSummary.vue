<template>
  <section>
    <transition-group name="list" tag="ul">
      <li v-for="(winningNumTimes, index) in propsdata" :key="winningNumTimes" class="shadow">
          {{ todoItem }}
      </li>
    </transition-group>
  </section>
</template>

<script>
export default{
  props: ['propsdata'],
}
</script>

<style scoped>
.list-enter-active, .list-leave-active{
  transition: all 1s;
}
.list-enter, .list-leave-to{
  opacity:0;
  transform:translateY(30px);
}

ul{
  list-style-type: none;
  padding-left: 0px;
  margin-top: 0;
  text-align: left;
}
li{
  display: flex;
  min-height: 50px;
  height: 50px;
  line-height: 50px;
  margin: 0.5rem 0;
  padding: 0 0.9rem;
  background: white;
  border-radius: 5px;
}
</style>
