<template>
  <div class="justify-content-center articles px-2 px-md-5" @scroll="scrollArticles" >
    <div v-for="(item,index) in articles" :key="index" class=" w-100 position-relative px-4 article mt-300" :class="{'articlebgactive':index===activeIndex,'articlebg':index!==activeIndex}" >
      <div class="w-100 row py-2 p-md-4 justify-content-center" style="top: 0;" :class="{'flex-row-reverse':index>1}">
        <div class="col-4 px-0"><img  :src="item.image" width="100%" alt=""></div>
        <div class="col-8 px-0 row justify-content-center position-relative">
          <!--            <img v-if="index===0"  src="/img/articleactive.png" alt="">-->
          <img v-if="index>1" src="/img/articleeven.png" width="95%" alt="">
          <img v-else src="/img/articleodd.png" width="95%" alt="">
          <div class="position-absolute d-grid h-100 w-100 px-3 px-md-5 text-center" style="top: 0; right: 0">
            <div class="align-self-center mx-auto  px-md-5 article-text">
              <h1>{{ item.title }}</h1>
              <p>{{ item.summary }}</p>
              <div>
                <img v-if="index===activeIndex" class="article-more-btn" src="/img/articleactivemore.png">
                <img v-else class="article-more-btn" src="/img/articlemore.png">
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
          card.classList.remove('mt-100');
          card.classList.add('mt-300');
          if (card.nextElementSibling) {
            card.nextElementSibling.classList.remove('mt-300')
            card.nextElementSibling.classList.add('mt-100')
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