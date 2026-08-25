<template>
  <div class="home">
    <div>
      <img src="/img/hero.png" width="100%" alt="">
    </div>
    <div class="position-relative p-4">
      <img src="/img/aboutbg.png" width="100%" alt="">
      <div class="row position-absolute row h-100 d-grid " style="top: 0; left: 0">
        <div class="about row align-self-center col-8 mx-auto">
          <div class="col-4 text-center">
            <h1>
              کوپابی
            </h1>
            <h2>باهـم برای پیشـرفت
              صنعـت زنبـورداری</h2>
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

    <div class="position-relative">
      <img src="/img/faqbg.png" width="100%" alt="">
      <div class="position-absolute w-100 " style="top: 0; right: 0;padding-top: 150px;">
        <h1 class="w-100 mb-5 text-center">سـوالات مـتـداول</h1>
        <div class="w-100 mt-5" style="overflow-x: scroll">
          <div class="faq-inner d-flex" :style="{minWidth: width+'%'}">
            <div v-for="(item,index) in faq" :key="index" class="faq">
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
    <div class="position-relative">
      <img src="/img/faqbg.png" width="100%" alt="">
      <div class="position-absolute w-100 " style="top: 0; right: 0;padding-top: 150px;">
        <h1 class="w-100 mb-5 text-center">سـوالات مـتـداول</h1>
        <div class="w-100 mt-5" style="overflow-x: scroll">
          <div class="faq-inner d-flex" :style="{minWidth: width+'%'}">
            <div v-for="(item,index) in faq" :key="index" class="faq">
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
  </div>
</template>

<script>

export default {
  name: 'HomeView',
  components: {},
  setup() {
    const faq = [
      {
        id: 1,
        title: 'خوراک زنبور کوپابی چه تفاوتی با سایر محصولات بازار دارد؟',
        summary: 'کوپابی با بافت نیمه‌جامد، مصرف آسان‌تر، ماندگاری بالا و فرمولاسیون علمی، تجربه‌ای متفاوت از تغذیه زنبور عسل فراهم می‌کند.'
      },
      {
        id: 2,
        title: 'خمیر شیرین چیست و چه کاربردی دارد؟',
        summary: 'خمیر شیرین یک خوراک مکمل برای زنبور عسل است که در زمان کمبود منابع طبیعی، به حفظ سلامت و پایداری کلنی کمک می‌کند.'
      },
      {
        id: 3,
        title: 'بهترین زمان استفاده از کوپابی چه زمانی است؟',
        summary: 'این محصول برای فصل کمبود شهد، پاییز، زمستان و اوایل بهار طراحی شده است.'
      },
      {
        id: 4,
        title: 'آیا برای استفاده از کوپابی نیاز به افزودن آب وجود دارد؟',
        summary: 'خیر. کوپابی کاملاً آماده مصرف است و بدون نیاز به رقیق‌سازی در اختیار زنبورها قرار می‌گیرد.'
      },

    ];
    const width = (faq.length * 300 / 100) + 100;
    return {
      faq, width
    }
  }
}
</script>
<style>
.about h1 {
  font-size: 96px;

}

.about h2 {
  font-size: 32px;

}

.about p {
  font-size: 23px;

}

.faq h1 {
  font-size: 46px;
}

.faq-box {
  width: 396px;
  height: 482px;
  border-radius: 48px;
  padding: 82px 36px 36px 36px;
  box-shadow: 12px 12px 20px 0px #0000001A;
  text-align: justify;
}

.faq-box h1 {
  font-size: 23px;
  color: #EC6F00;
  font-weight: 400;
}

.faq-box p {
  font-size: 19px;

}

</style>