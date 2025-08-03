<script setup>
import Footer from "@layouts/components/Footer.vue";
import TopMenu from "@layouts/components/TopMenu.vue";
</script>

<template>
  <div class="main-layout">
    <TopMenu />

    <VContainer class="layout-content" fluid>
      <RouterView />
    </VContainer>

    <VContainer class="footer-container" fluid>
      <Footer />
    </VContainer>
  </div>
</template>

<style scoped>
.main-layout {
  display: flex;
  flex-direction: column;
  min-height: 100vh;
}

.layout-content {
  flex: 1;
  padding-top: 16px;
  padding-bottom: 32px;
}

.footer-container {
  padding-top: 0;
  padding-bottom: 16px;
}
</style>
