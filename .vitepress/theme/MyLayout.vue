<script setup>
import DefaultTheme from 'vitepress/theme'
import Giscus from '@giscus/vue'

const { Layout } = DefaultTheme
</script>

<template>
  <Layout>
    <template #doc-after>
      <div class="giscus">
        <Giscus
          :key="giscus"
          host="https://giscus.app"
          repo="like-buer/Blog"
          repoId="R_kgDOK_1uwQ"
          category="Announcements"
          categoryId="DIC_kwDOK_1uwc4CcIip"
          :theme="isDark ? 'dark' : 'light'"
          lang="zh-CN"
          strict="1"
          mapping="title"
          crossorigin="anonymous"
        />
      </div>
    </template>
  </Layout>
</template>

<script>
import { watch } from 'vue'
import { useRoute, useData } from 'vitepress'

export default {
  mounted() {
    const vitePressData = useData()
    this.isDark = vitePressData.isDark

    const route = useRoute()
    watch(route, () => {
      this.giscus = !this.giscus
    })
  },
  data() {
    return {
      giscus: true,
      isDark: false,
    }
  },
}
</script>

<style>
img.pv {
  margin-top: 1em;
}

div.giscus {
  margin-top: 2em;
}

.donation {
  margin-top: 2em;
}

.donation div {
  margin: 0 auto;
  flex: 0 1 auto;
  flex-direction: row;
  max-width: max-content;
  row-gap: 10px;
}

.donation img {
  display: inline-block;
  zoom: 25%;
  margin: 4em;
}
</style>
