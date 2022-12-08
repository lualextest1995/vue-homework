<template>
  <PageHeaderVue></PageHeaderVue>
  <PageContentVue></PageContentVue>
  <PageFooterVue></PageFooterVue>
</template>

<script>
import PageHeaderVue from "./components/PageHeader.vue";
import PageContentVue from "./components/PageContent.vue";
import PageFooterVue from "./components/PageFooter.vue";
export default {
  name: "App",
  components: { PageHeaderVue, PageContentVue, PageFooterVue },
};
</script>

<style lang="scss">
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-family: "Noto Sans TC", Courier, monospace;
  font-style: normal;
  font-weight: 700;
  scroll-behavior: smooth;
}
</style>
