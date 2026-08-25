<template>
  <nav-bar />
  <router-view/>
</template>

<script>
import NavBar from "@/components/TheNav.vue";
export default{
  components:{
    NavBar,
  }
}
</script>
<style>

</style>