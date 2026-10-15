<template>
  <div class="justify-content-center articles" @scroll="scrollArticles" style="padding-top:0px">
    <div v-for="(item,index) in articles" :key="index" class="w-100 position-relative px-4 article">
      <img v-if="index===activeIndex" src="/img/articlebgactive.png" width="100%" alt="">
      <img v-else src="/img/articlebg.png" width="100%" alt="">
      <div class="w-100 d-flex p-3 position-absolute justify-content-center" style="top: 0;"
           :class="{'flex-row-reverse':index>1}">
        <img :src="item.image" alt="">
        <div class="d-flex position-relative">
          <!--            <img v-if="index===0"  src="/img/articleactive.png" alt="">-->
          <img v-if="index>1" src="/img/articleeven.png" alt="">
          <img v-else src="/img/articleodd.png" alt="">
          <div class="position-absolute d-grid h-100 w-100 px-5 text-center" style="top: 0; right: 0">
            <div class="align-self-center mx-auto px-5">
              <h1>{{ item.title }}</h1>
              <p>{{ item.summary }}</p>
              <div>
                <img v-if="index===activeIndex" src="/img/articleactivemore.png">
                <img v-else src="/img/articlemore.png">
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>
<script >
import {onMounted, ref} from "vue";
export default {

  setup(){


    const articles = [
      {
        id: 1,
        image: '/img/article1.png',
        title: 'راهـکاری نوین برای تغذیه زنبـورهای عسـل',
        summary: 'محصولات ما با هدف بهبـود سلامـت زنبــورها و افـزایـش بهره‌وری تولید، طراحی شده‌اند.'
      },
      {
        id: 2,
        image: '/img/article2.png',
        title: 'نقطـه تـلاقی دانش، صنعت و طبیعـت',
        summary: 'در عسل لذیذ، تلاش می‌کنیم راهـکارهـایی علـمی و کـاربـردی بـرای تـغـذیـه زنـبـور عسـل ارائه دهیم.'
      },
      {
        id: 3,
        image: '/img/article3.png',
        title: 'پیـوند صنـعـت و عـلـم',
        summary: 'همکاری با دانشگاه شهید بهشتی، بستری برای تحقیق، توسعه و بهبود مستمر محصولات ما فراهم کرده است.'
      },
      {
        id: 4,
        image: '/img/article4.png',
        title: 'جـایـی بـرای تـوسـعـه محـصـول در دل طبـیـعـت',
        summary: 'خوراک زنبور عسل کوپابی، پیش از ورود به بازار، در زنبورستان علمـی و تحـت شـرایط واقعی مـورد بررسـی و ارزیابی قرار می‌گیـرد تا از کیفیت، ایمنی و عملکرد قابل اعتماد آن اطمیـنان حـاصـل شــود.'
      },
    ];
    const activeIndex = ref();
    const scrollArticles = () => {
      let cards = document.querySelectorAll('.article');
      let index = 0;
      cards.forEach((card) => {
        let top = card.getBoundingClientRect().top
        if (top >= 150 && top <= 300) {
          console.log(top)
          document.querySelector('.activeArticle')?.classList.remove('activeArticle')
          card.classList.add('activeArticle')
          activeIndex.value = index;
          card.style.marginTop = "-300px"
          if (card.nextElementSibling) {
            card.nextElementSibling.style.marginTop = '-100px'
          }
        }
        index++;

      })

    }
    onMounted(() => {
      window.addEventListener('scroll', scrollArticles)
    })

    return{
     articles, scrollArticles, activeIndex

    }
  }
}
</script>

<style scoped>

</style>