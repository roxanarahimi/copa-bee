<template >
  <div class="position-relative" @mousemove="cursorShadow($event)">
    <nav-bar />
    <router-view/>
    <the-footer />
  </div>

</template>

<script>
import NavBar from "@/components/TheNav.vue";
import TheFooter from "@/components/TheFooter.vue";
export default{
  components:{
    TheFooter,
    NavBar,
  },
  setup(){
    const cursorShadow = (e) => {
      let shadow = document.querySelector('.cursor-shadow')

      if (!shadow) {
        shadow = document.createElement('div')
        shadow.className = 'cursor-shadow'
        document.getElementsByTagName('body')[0].appendChild(shadow)
      }

      const rect = e.currentTarget.getBoundingClientRect()

      shadow.style.left = `${e.clientX - rect.left}px`
      shadow.style.top = `${e.clientY - rect.top}px`
    }

    return{
      cursorShadow
    }
  }
}
</script>
<style>

</style>