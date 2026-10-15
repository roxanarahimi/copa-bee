<template>
  <div class="home">
    <div class="position-relative">
      <img src="/img/hero.png" width="100%" alt="">
      <div class="row position-absolute row h-100 d-grid text-light" style="top: 0; left: 100px;">
       <div class="align-self-center text-center">
         <h1 style="font-size: 100px">کوپابی</h1>
         <b style="font-size: 38px">باهم برای پیشرفت صنعت زنبور داری</b>
       </div>
      </div>
    </div>
    <div class="position-relative p-4">
      <img src="/img/aboutbg.png" width="100%" alt="">
      <div class="row position-absolute row h-100 d-grid " style="top: 0; right: 0">
        <div class="about row align-self-center col-8 mx-auto">
          <div class="col-4 text-center">
            <h1>
              کوپابی
            </h1>
            <h2>باهـم برای پیشـرفت صنعـت زنبـورداری</h2>
          </div>
          <div class="col-8">
            <p>کوپابی با هدف تولید تغذیه‌ای کامل، استاندارد و ایمن برای زنبور عسل شکل گرفت؛محصولی که به‌عنوان جایگزینی
              علمی برای روش‌های سنتی و نمونه‌های وارداتی توسعه یافته است.
              ما با تکیه بر دانش فنی گروه صنایع غذایی آماده لذیذ و پشتوانه علمی پژوهشکده گیاهان دارویی و مواد اولیه
              دانشگاه شهید بهشتی، تولید خود را از سال ۱۴۰۱ به‌صورت نیمه‌صنعتی و تحت کنترل دقیق آغاز کردیم.
            </p>
          </div>
        </div>
      </div>
    </div>

  <div class="position-relative ffaq"><!--   @mousemove="cursorShadow($event)"-->
      <img src="/img/faqbg.png" width="100%" style="opacity: 0.3" alt="">
      <div class="position-absolute w-100 " style="top: 0; right: 0;padding-top: 150px;">
        <h1 class="w-100 mb-5 text-center">سـوالات مـتـداول</h1>
        <div class="w-100 mt-5 faqq" >
          <div class="faq-inner d-flex" :style="{Width: width+'%'}">
           <div v-for="(item,index) in faq" :key="index" class="faq" @mouseover="scroll($event)" @mouseleave="scrollBack($event)"> <!---->
              <div class="faq-box bg-white me-4"
                   :class="{'mt-5':index%2===1, 'ms-4':index===0, 'me-0':index===faq.length-1}">
                <h1>{{ item.title }}</h1>
                <p>{{ item.summary }}</p>
              </div>
            </div>
          </div>

        </div>
      </div>

    </div>
    <div class="justify-content-center articles" @scroll="scrollArticles" style="padding-top: 300px">
      <div v-for="(item,index) in articles" :key="index" class="w-100 position-relative px-4 article">
        <img v-if="index===activeIndex" src="/img/articlebgactive.png" width="100%" alt="">
        <img v-else src="/img/articlebg.png" width="100%" alt="">
        <div class="w-100 d-flex p-3 position-absolute justify-content-center"  style="top: 0;" :class="{'flex-row-reverse':index>1}">
          <img :src="item.image" alt="">
          <div class="d-flex position-relative" >
<!--            <img v-if="index===0"  src="/img/articleactive.png" alt="">-->
            <img v-if="index>1" src="/img/articleeven.png" alt="">
            <img v-else src="/img/articleodd.png" alt="">
            <div class="position-absolute d-grid h-100 w-100 px-5 text-center" style="top: 0; right: 0">
             <div class="align-self-center mx-auto px-5">
               <h1>{{item.title}}</h1>
               <p>{{item.summary}}</p>
               <div>
                 <img v-if="index===activeIndex"  src="/img/articleactivemore.png">
                 <img v-else src="/img/articlemore.png" >
               </div>
             </div>
            </div>
          </div>
        </div>
      </div>
    </div>

    <div class="d-flex justify-content-center p-5">
      <div><img src="/img/etehadieh.png" class="mx-5" height="120px"></div>
      <div><img src="/img/beheshti.png" class="mx-5" height="100px"></div>
      <div><img src="/img/Amadehlaziz.png" class="mx-5" height="80px"></div>
    </div>
  </div>
</template>

<script>

import {onMounted, ref} from "vue";

export default {
  name: 'HomeView',
  components: {},
  setup() {
    const faq = [
      {id: 1, title: 'خوراک زنبور کوپابی چه تفاوتی با سایر محصولات بازار دارد؟', summary: 'کوپابی با بافت نیمه‌جامد، مصرف آسان‌تر، ماندگاری بالا و فرمولاسیون علمی، تجربه‌ای متفاوت از تغذیه زنبور عسل فراهم می‌کند.'},
      {id: 2, title: 'خمیر شیرین چیست و چه کاربردی دارد؟', summary: 'خمیر شیرین یک خوراک مکمل برای زنبور عسل است که در زمان کمبود منابع طبیعی، به حفظ سلامت و پایداری کلنی کمک می‌کند.'},
      {id: 3, title: 'بهترین زمان استفاده از کوپابی چه زمانی است؟', summary: 'این محصول برای فصل کمبود شهد، پاییز، زمستان و اوایل بهار طراحی شده است.'},
      {id: 4, title: 'آیا برای استفاده از کوپابی نیاز به افزودن آب وجود دارد؟', summary: 'خیر. کوپابی کاملاً آماده مصرف است و بدون نیاز به رقیق‌سازی در اختیار زنبورها قرار می‌گیرد.'},
    {id: 1, title: 'خوراک زنبور کوپابی چه تفاوتی با سایر محصولات بازار دارد؟', summary: 'کوپابی با بافت نیمه‌جامد، مصرف آسان‌تر، ماندگاری بالا و فرمولاسیون علمی، تجربه‌ای متفاوت از تغذیه زنبور عسل فراهم می‌کند.'},
      {id: 2, title: 'خمیر شیرین چیست و چه کاربردی دارد؟', summary: 'خمیر شیرین یک خوراک مکمل برای زنبور عسل است که در زمان کمبود منابع طبیعی، به حفظ سلامت و پایداری کلنی کمک می‌کند.'},
      {id: 3, title: 'بهترین زمان استفاده از کوپابی چه زمانی است؟', summary: 'این محصول برای فصل کمبود شهد، پاییز، زمستان و اوایل بهار طراحی شده است.'},
      {id: 4, title: 'آیا برای استفاده از کوپابی نیاز به افزودن آب وجود دارد؟', summary: 'خیر. کوپابی کاملاً آماده مصرف است و بدون نیاز به رقیق‌سازی در اختیار زنبورها قرار می‌گیرد.'},
    {id: 1, title: 'خوراک زنبور کوپابی چه تفاوتی با سایر محصولات بازار دارد؟', summary: 'کوپابی با بافت نیمه‌جامد، مصرف آسان‌تر، ماندگاری بالا و فرمولاسیون علمی، تجربه‌ای متفاوت از تغذیه زنبور عسل فراهم می‌کند.'},
      {id: 2, title: 'خمیر شیرین چیست و چه کاربردی دارد؟', summary: 'خمیر شیرین یک خوراک مکمل برای زنبور عسل است که در زمان کمبود منابع طبیعی، به حفظ سلامت و پایداری کلنی کمک می‌کند.'},
      {id: 3, title: 'بهترین زمان استفاده از کوپابی چه زمانی است؟', summary: 'این محصول برای فصل کمبود شهد، پاییز، زمستان و اوایل بهار طراحی شده است.'},
      {id: 4, title: 'آیا برای استفاده از کوپابی نیاز به افزودن آب وجود دارد؟', summary: 'خیر. کوپابی کاملاً آماده مصرف است و بدون نیاز به رقیق‌سازی در اختیار زنبورها قرار می‌گیرد.'},
    {id: 1, title: 'خوراک زنبور کوپابی چه تفاوتی با سایر محصولات بازار دارد؟', summary: 'کوپابی با بافت نیمه‌جامد، مصرف آسان‌تر، ماندگاری بالا و فرمولاسیون علمی، تجربه‌ای متفاوت از تغذیه زنبور عسل فراهم می‌کند.'},
      {id: 2, title: 'خمیر شیرین چیست و چه کاربردی دارد؟', summary: 'خمیر شیرین یک خوراک مکمل برای زنبور عسل است که در زمان کمبود منابع طبیعی، به حفظ سلامت و پایداری کلنی کمک می‌کند.'},
      {id: 3, title: 'بهترین زمان استفاده از کوپابی چه زمانی است؟', summary: 'این محصول برای فصل کمبود شهد، پاییز، زمستان و اوایل بهار طراحی شده است.'},
      {id: 4, title: 'آیا برای استفاده از کوپابی نیاز به افزودن آب وجود دارد؟', summary: 'خیر. کوپابی کاملاً آماده مصرف است و بدون نیاز به رقیق‌سازی در اختیار زنبورها قرار می‌گیرد.'},
    ];
    const articles = [
      {id:1,image:'/img/article1.png',title:'راهـکاری نوین برای تغذیه زنبـورهای عسـل',summary:'محصولات ما با هدف بهبـود سلامـت زنبــورها و افـزایـش بهره‌وری تولید، طراحی شده‌اند.'},
      {id:2,image:'/img/article2.png',title:'نقطـه تـلاقی دانش، صنعت و طبیعـت',summary:'در عسل لذیذ، تلاش می‌کنیم راهـکارهـایی علـمی و کـاربـردی بـرای تـغـذیـه زنـبـور عسـل ارائه دهیم.'},
      {id:3,image:'/img/article3.png',title:'پیـوند صنـعـت و عـلـم',summary:'همکاری با دانشگاه شهید بهشتی، بستری برای تحقیق، توسعه و بهبود مستمر محصولات ما فراهم کرده است.'},
      {id:4,image:'/img/article4.png',title:'جـایـی بـرای تـوسـعـه محـصـول در دل طبـیـعـت',summary:'خوراک زنبور عسل کوپابی، پیش از ورود به بازار، در زنبورستان علمـی و تحـت شـرایط واقعی مـورد بررسـی و ارزیابی قرار می‌گیـرد تا از کیفیت، ایمنی و عملکرد قابل اعتماد آن اطمیـنان حـاصـل شــود.'},
     ];
    const width = (faq.length * 300 / 100) + 100;

    const scroll = (e)=>{
      document.querySelector('.faqq').scrollLeft = -e.clientX;

    }
   const scrollBack = (e)=>{
      document.querySelector('.faqq').scrollLeft = e.clientX;

    }


    const activeIndex = ref();
    const scrollArticles = ()=>{
      let cards = document.querySelectorAll('.article');
      // console.log(document.querySelector('.article.active').getBoundingClientRect().top);
      // console.log(window.scrollY  )
      let index = 0;
      cards.forEach((card)=>{
        let top = card.getBoundingClientRect().top
               if(top>=150 && top<=300){
          console.log(top)
          document.querySelector('.activeArticle')?.classList.remove('activeArticle')
          card.classList.add('activeArticle')
        activeIndex.value = index;
          card.style.marginTop = "-300px"
          if (card.nextElementSibling){ card.nextElementSibling.style.marginTop = '-100px'}
        }
        index++;

      })

    }
    onMounted(()=>{
      window.addEventListener('scroll',scrollArticles)
    })
    return {
      faq, width, articles,scroll, scrollBack, scrollArticles,activeIndex
    }
  }
}
</script>
<style>

</style>