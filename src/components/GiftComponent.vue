<template>
  <div class="gift">
    <div class="container">
      <ItemComponentA itemName="dehumidifier" itemNumber="ONE" itemEnglish="A">
      </ItemComponentA>
      <ItemComponentA itemName="range hood" itemNumber="ONE" itemEnglish="B">
      </ItemComponentA>
      <ItemComponentA
        itemName="vacuum cleaner"
        itemNumber="ONE"
        itemEnglish="C"
      >
      </ItemComponentA>
      <ItemComponentD
        itemName="toaster"
        itemNumber="ONE"
        itemEnglish="D"
      ></ItemComponentD>
      <ItemComponentD
        itemName="scale"
        itemNumber="ONE"
        itemEnglish="E"
      ></ItemComponentD>
      <ItemComponentD
        itemName="straightening iron"
        itemNumber="ONE"
        itemEnglish="F"
      ></ItemComponentD>
      <ItemComponentD
        itemName="vacuum cleaner"
        itemNumber="FIVE"
        itemEnglish="G"
      ></ItemComponentD>
      <ItemComponentD
        itemName="rice cooker"
        itemNumber="TEN"
        itemEnglish="H"
      ></ItemComponentD>
    </div>
  </div>
</template>

<script>
import ItemComponentA from "./ItemComponentA.vue";
import ItemComponentD from "./ItemComponentD.vue";
export default {
  name: "GiftComponent",
  components: { ItemComponentA, ItemComponentD },
  setup() {
    return {};
  },
};
</script>

<style lang="scss" scoped>
.gift {
  width: 100%;
  display: flex;
  justify-content: center;
  background-image: url(../assets/抽獎沙子.svg);
  margin-bottom: 50px;
  .container {
    width: 730px;
    display: flex;
    align-items: center;
    flex-wrap: wrap;
  }
}
@media screen and(max-width:730px) {
  .gift {
    .container {
      width: 500px;
      justify-content: center;
    }
  }
}
</style>
