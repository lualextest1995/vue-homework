<template>
  <div class="item">
    <div class="box">
      <img class="itemPicture" src="../assets/certificateA.svg" alt="" />
      <p class="itemEnglish">{{ itemEnglish }}</p>
      <p class="itemName">{{ itemName }}</p>
      <div class="oval">
        <p class="itemNumber">{{ itemNumber }}</p>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "ItemComponentA",
  props: ["itemName", "itemNumber", "itemEnglish"],
  setup() {
    return {};
  },
};
</script>

<style lang="scss" scoped>
.item {
  margin: 2rem;
  .box {
    width: 178px;
    height: 112px;
    color: #ffffff;
    background-color: #ffffff;
    box-shadow: 0px 8px 0px #edeef0;
    border-radius: 20px;
    position: relative;
    .itemName {
      text-align: center;
      width: 100%;
      position: absolute;
      font-size: 18px;
      bottom: 20px;
      color: #b3b960;
    }
    .itemEnglish {
      position: absolute;
      font-size: 17px;
      z-index: 2;
      left: 50%;
      transform: translate(-50%, 0);
    }
    .itemPicture {
      position: absolute;
      top: -23px;
      left: 50%;
      transform: translate(-50%, 0);
      z-index: 1;
    }
    .oval {
      position: absolute;
      top: 20px;
      right: 8px;
      width: 45px;
      height: 23px;
      background: #fafafa;
      border: 1px solid #b3b960;
      border-radius: 50px;
      display: flex;
      align-items: center;
      justify-content: center;
      p {
        color: #b3b960;
        font-weight: 400;
        font-size: 12px;
        line-height: 140%;
      }
    }
  }
}
@media screen and(max-width:490px) {
  .item {
    margin: 10px;
  }
}
</style>
