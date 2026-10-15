<template>
  <div class="container-fluid px-0 home">
    <div class="position-relative banner">
      <img src="/img/hero.png" width="100%" alt="">
      <div class="row position-absolute h-100 d-grid text-light row justify-content-center" style="top: 0; left: 0;">
        <div class="align-self-center text-center d-none d-md-block  pe-5">
          <h1 style="font-size: 100px">کوپابی</h1>
          <b style="font-size: 38px">باهم برای پیشرفت صنعت زنبور داری</b>
        </div>
        <div class="align-self-center text-end d-md-none pe-5">
          <h1 style="font-size: 80px">کوپابی</h1>
          <b style="font-size: 20px">باهم برای پیشرفت صنعت زنبور داری</b>
        </div>
      </div>
    </div>
    <div class="about">
      <div class="position-relative p-4  text-center">
        <img src="/img/aboutbg.png" class="d-none d-md-block" width="100%" alt="">
        <img src="/img/aboutbgM.png" class="d-md-none" width="100%" alt="">
        <div class="row position-absolute row min-vh-100 d-grid " style="top: 0; right: 0">
          <div class="about row align-self-center col-8 mx-auto">
            <div class="col-md-4 text-center mt-5 mt-md-0">
              <h1>
                کوپابی
              </h1>
              <h2>باهـم برای پیشـرفت صنعـت زنبـورداری</h2>
            </div>
            <div class="col-md-8">
              <p class="text-justify">کوپابی با هدف تولید تغذیه‌ای کامل، استاندارد و ایمن برای زنبور عسل شکل گرفت؛محصولی
                که به‌عنوان جایگزینی
                علمی برای روش‌های سنتی و نمونه‌های وارداتی توسعه یافته است.
                ما با تکیه بر دانش فنی گروه صنایع غذایی آماده لذیذ و پشتوانه علمی پژوهشکده گیاهان دارویی و مواد اولیه
                دانشگاه شهید بهشتی، تولید خود را از سال ۱۴۰۱ به‌صورت نیمه‌صنعتی و تحت کنترل دقیق آغاز کردیم.
              </p>
            </div>
          </div>
        </div>
      </div>
    </div>

    <faq/>
    <articles/>
    <div class="w-100 d-flex justify-content-center my-5 px-5 logos">
      <div class="h-100"><img src="/img/beheshti.png" class="mx-2 mx-md-5 logoss" height="100%"></div>
      <div class="h-100"><img src="/img/Amadehlaziz.png" class="mx-2 mx-md-5 logoss" height="100%"></div>
      <div class="h-100"><img src="/img/etehadieh.png" class="mx-2 mx-md-5 logoss" height="100%"></div>
    </div>
  </div>
</template>

<script>

import {onMounted, ref} from "vue";
import Faq from '@/components/Faq.vue'
import Articles from '@/components/Articles.vue'

export default {
  name: 'HomeView',
  components: {Faq, Articles},
  setup() {

    return {}
  }
}
</script>
<style>

</style>