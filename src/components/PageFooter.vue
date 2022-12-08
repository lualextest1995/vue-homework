<template>
  <div class="foot">
    <div>
      <p>Neque porro quisquam</p>
      <p>est qui dolorem!</p>
      <img src="../assets/market.svg" alt="" />
    </div>
  </div>
</template>

<script>
export default {
  name: "PageFooter",
  setup() {
    return {};
  },
};
</script>

<style lang="scss" scoped>
.foot {
  background-color: #e2d9d3;
  div {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    background-color: #204379;
    border-radius: 50px 50px 0px 0px;
    height: 700px;
    p {
      font-size: 20px;
      color: #ffffff;
      line-height: 200%;
    }
    img {
      margin-top: 40px;
    }
  }
}
</style>
