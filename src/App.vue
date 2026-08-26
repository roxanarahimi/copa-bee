<template>
  <nav-bar />
  <router-view/>
  <the-footer />
</template>

<script>
import NavBar from "@/components/TheNav.vue";
import TheFooter from "@/components/TheFooter.vue";
export default{
  components:{
    TheFooter,
    NavBar,
  }
}
</script>
<style>

</style>