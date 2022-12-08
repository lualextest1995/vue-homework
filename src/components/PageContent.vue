<template>
  <div class="content">
    <FormComponent></FormComponent>
    <GiftComponent></GiftComponent>
    <div class="container">
      <div class="slash"></div>
      <div class="reverseSlash"></div>
      <strong class="num">13.32</strong>
      <strong>who seeks after it and</strong>
      <strong>wants to have it</strong>
      <img src="../assets/lighthouse.svg" alt="" />
    </div>
  </div>
</template>

<script>
import FormComponent from "./FormComponent.vue";
import GiftComponent from "./GiftComponent.vue";
export default {
  name: "PageContent",
  components: { FormComponent, GiftComponent },
  setup() {
    return {};
  },
};
</script>

<style lang="scss" scoped>
.content {
  width: 100%;
  height: 1800px;
  background-color: #e2d9d3;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;

  .container {
    width: 400px;
    position: relative;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    .slash {
      width: 90px;
      border: 1px solid #204379;
      transform: rotate(-80deg);
      position: absolute;
      top: 40px;
      right: 0;
    }
    .reverseSlash {
      width: 90px;
      border: 1px solid #204379;
      transform: rotate(80deg);
      position: absolute;
      top: 40px;
      left: 0;
    }
    strong {
      text-align: center;
      color: #204379;
      font-size: 20px;
      line-height: 140%;
    }
    .num {
      color: #b57556;
    }
    img {
      margin-top: 2rem;
    }
  }
}

@media screen and (max-width: 730px) {
  .content {
    height: 2100px;
  }
}
</style>
