<template>
  <div class="page-container">
    <section class="first-section-wrap first-slider-wrap">
      <!-- 轮播 -->
      <div class="ele-slider-wrap slider-wrap">
        <Swiper
          :modules="[Autoplay, Pagination]"
          :pagination="{ clickable: true }"
          :slides-per-view="1"
          :loop="true"
          :allowTouchMove="false">
          <SwiperSlide v-for="(slide, index) in slides" :key="slide.id">
            <img :src="getPath(`image/${themeColor}/${slide.image}`)" class="ele-slider-img" />
          </SwiperSlide>
        </Swiper>
      </div>
      <div class="section-wrap">
        <div class="first-website-wrap">
          <div class="first-website-inner">
            <div class="website-item">
              <div class="website-item-icon website-item-icon--deposit"></div>
              <div class="website-item-title">存款平均<br>到帐时间</div>
              <div class="website-item-num"><span>20</span>秒</div>
            </div>
            <div class="website-item">
              <div class="website-item-icon website-item-icon--withdraw"></div>
              <div class="website-item-title">取款平均<br>到帐时间</div>
              <div class="website-item-num"><span>20</span>秒</div>
            </div>
            <div class="website-item">
              <div class="website-item-icon website-item-icon--game"></div>
              <div class="website-item-title">官方合作<br>游戏平台</div>
              <div class="website-item-num"><span>50</span>家</div>
            </div>
            <div class="website-item">
              <div class="website-item-icon website-item-icon--bank"></div>
              <div class="website-item-title">银行服务<br>合作平台</div>
              <div class="website-item-num"><span>30</span>家</div>
            </div>
          </div>
        </div>
      </div>
    </section>
    <section class="first-section-wrap first-ranking-wrap">
      <div class="section-wrap">
        <div class="first-ranking-header">
          <div class="first-ranking-title">
            <img :src="getPath(`image/${themeColor}/lang/${lang}/first_ranking_title.png`)" />
          </div>
          <button class="first-ranking-more-btn">
            <span>More</span>
            <i class="icon"></i>
          </button>
        </div>
        <div class="first-ranking-container">
          <a href="#" v-for="index in 5" :key="index" class="first-ranking-link">
            <img
              :src="rankingHover === index
                  ? getPath(`image/${themeColor}/lang/${lang}/first_ranking0${index}_h.png`)
                  : getPath(`image/${themeColor}/lang/${lang}/first_ranking0${index}.png`)"
              @mouseenter="rankingHover = index"
              @mouseleave="rankingHover = null"
            />
          </a>
        </div>
      </div>
    </section>
    <section class="first-section-wrap first-platform-wrap">
      <div class="section-wrap">
        <a
          :href="platform"
          v-for="(platform, index) in ['casino', 'lottery', 'card', 'live', 'sport']"
          :key="index"
          :style="{
            backgroundImage: `url(${getPath(`image/${themeColor}/lang/${lang}/first_platform_${platform}.png`)})`
          }"
          :class="[`first-platform-link first-platform--${platform}`]"
          @mouseenter="platformHover = index"
          @mouseleave="platformHover = null"
        ></a>
      </div>
    </section>
    <section class="first-section-wrap first-mobile-wrap">
      <div class="section-wrap">
        <div class="first-mobile-left-wrap">
          <div class="first-mobile-title"></div>
            <div class="first-intro-text">
              独家原生APP给玩家最优质的画面，便捷登录、操作简单，随时随地都可投注，极速稳定畅通，无阻多款游戏任由你畅玩。
            </div>
            <div class="first-mobile-info-wrap">
              <div class="first-mobile-qrcode-wrap">
                <div class="img-qrcode-bg">
                  <img :src="isLoggedIn
                    ? getPath(`image/not-use/qrcode.jpg`)
                    : getPath(`image/not-use/lang/${lang}/${imgQrcode}.png`)" class="first-mob-qrcode-img" />
                </div>
                <div class="first-mobile-info-title">扫码下载App</div>
                <p>支持 ios & Android</p>
                <div class="first-mobile-info-highlight">
                  <div class="first-mobile-info-icon ios"></div>
                  ios
                  <div class="first-mobile-info-icon android"></div>
                  Android
                </div>
              </div>
              <div class="first-mobile-h5-wrap">
                <div class="img-h5-bg"></div>
                <div class="first-mobile-info-title">直接访问</div>
                <p>手机输入网址即可访问</p>
                <div class="first-mobile-info-highlight">bbin.com</div>
              </div>
            </div>
        </div>
        <div class="first-mobile-right-wrap">
          <img v-for="index in 5" :key="index" :src="getPath(`image/first_mob0${index}.png`)"
            :class="`first-mobile-phone-img first-mobile-phone-img0${index}`" />
          <div class="first-mobile-right-bg"></div>
        </div>
      </div>
    </section>
  </div>
</template>
<script setup>
import { storeToRefs } from 'pinia';
import { useTheme } from '@/composables/useTheme.js';
import { useAuthStore } from '@/stores/authStore.js';
import { getPath } from '@/composables/usePath.js'

const { themeColor, lang, imgQrcode } = useTheme(); // 使用动态主题和语言设定
const authStore = useAuthStore();
const { isLoggedIn } = storeToRefs(authStore); // 使用全域登入状态

import { Swiper, SwiperSlide } from 'swiper/vue';
import { Autoplay, Pagination } from 'swiper/modules';
import 'swiper/css';
import 'swiper/css/pagination';
import 'swiper/css/autoplay';

// 轮播图资料
const slides = ref([
  { id: 1, image: 'slider01.jpg' },
  { id: 2, image: 'slider02.jpg' }
]);
const rankingHover = ref(null);
const platformHover = ref(null);
</script>
