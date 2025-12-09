<template>
  <footer class="page-footer">
    <div class="footer-top-wrap">
      <img :src="getPath(`image/${themeColor}/footer_img01.png`)">
      <div class="footer-top-line"></div>
      <img :src="getPath(`image/${themeColor}/footer_img02.png`)">
    </div>
    <div class="footer-bottom-wrap">
      <div class="bottom-link-wrap">
        <FooterLink />
      </div>
      <div class="footer-logo-wrap">
        <img class="footer-logo-bb" :src="getPath(`image/not-use/${themeFooterLogo.bb}.png`)" width="96" />
        <a class="footer-logo-ub" href="#">
          <img :src="getPath(`image/not-use/ublogo/${themeFooterLogo.ub}.png`)" width="162" />
        </a>
      </div>
      <div class="copyright">Copyright © BBIN Reserved</div>
    </div>
  </footer>
</template>

<script setup>
import FooterLink from '@/components/common/FooterLink.vue';
import { useConfigStore } from '@/stores/configStore.js';
import { getPath } from '@/composables/usePath.js'

const configStore = useConfigStore()
const { themeColor, themeFooterLogo } = storeToRefs(configStore)
</script>
