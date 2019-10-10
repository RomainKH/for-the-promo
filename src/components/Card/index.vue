<template>
     <div class="card">
       <div class="img">
           <img v-bind:src="image" alt="">
       </div>
       <div class="content">
           <p>{{text}}</p>
       </div>
     </div>
</template>

<script>
export default {
  name: 'Card',
  props:  {
    text: String,
    image: String
  }
}
</script>
<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
    @import "style.scss";
</style>
