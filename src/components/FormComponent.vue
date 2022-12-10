<template>
  <div class="form">
    <div class="container">
      <img id="form" src="../assets/Frame1819.svg" alt="" />
      <img class="turtle" src="../assets/turtle.svg" alt="" />
      <InputComponent item="store">
        <input
          list="store"
          placeholder="placeholder text"
          v-model="storeInfo.value"
          ref="storeRef"
        />
        <datalist id="store">
          <option v-for="data in storeInfo.datalist" :key="data" :value="data">
            {{ data }}
          </option>
        </datalist>
        <p class="error" v-show="storeInfo.error">{{ storeInfo.error }}</p>
      </InputComponent>
      <InputComponent item="name">
        <input
          type="text"
          id="name"
          placeholder="placeholder text"
          v-model="nameInfo.value"
          ref="nameRef"
        />
        <p class="error" v-show="nameInfo.error">{{ nameInfo.error }}</p>
      </InputComponent>
      <InputComponent item="phone">
        <input
          type="text"
          id="phone"
          placeholder="placeholder text"
          v-model="phoneInfo.value"
          ref="phoneRef"
        />
        <p class="error" v-show="phoneInfo.error">{{ phoneInfo.error }}</p>
      </InputComponent>
      <InputComponent item="Amount of consumption">
        <input
          type="text"
          id="Amount of consumption"
          placeholder="placeholder text"
          v-model="amountInfo.value"
          ref="amountRef"
        />
        <p class="error" v-show="amountInfo.error">{{ amountInfo.error }}</p>
      </InputComponent>
      <InputComponent item="payment">
        <select id="payment" v-model="paymentInfo.value" ref="paymentRef">
          <option value="" disabled>placeholder text</option>
          <option value="digital payment">digital payment</option>
          <option value="ATM">ATM</option>
        </select>
        <p class="error" v-show="paymentInfo.error">{{ paymentInfo.error }}</p>
      </InputComponent>
    </div>
    <div class="btnBox">
      <button v-if="btnState === 0" @click="check">submit</button>
      <button v-else-if="btnState === 1" @click="check" class="success">
        <img src="../assets/success.svg" alt="" />success
      </button>
      <button v-else @click="check" class="failure">
        <img src="../assets/failure.svg" alt="" />failure
      </button>
    </div>
  </div>
</template>

<script>
import { ref, reactive, watch } from "vue";
import InputComponent from "./InputComponent.vue";
export default {
  name: "FormComponent",
  components: { InputComponent },
  setup() {
    const storeInfo = reactive({
      value: "",
      error: null,
      datalist: ["store1", "store2", "store3", "store4"],
    });
    const storeRef = ref(null);
    const nameInfo = reactive({
      value: "",
      error: null,
    });
    const nameRef = ref(null);
    const phoneInfo = reactive({
      value: "",
      error: null,
    });
    const phoneRef = ref(null);
    const amountInfo = reactive({
      value: "",
      error: null,
    });
    const amountRef = ref(null);
    const paymentInfo = reactive({
      value: "digital payment",
      error: null,
    });
    const paymentRef = ref(null);
    const btnState = ref(0);

    //監控store
    watch(storeInfo, (val) => {
      if (val.value.trim() === "") {
        storeInfo.error = "required";
        storeRef.value.style = "outline: 3px solid #E06D6D";
      } else if (!storeInfo.datalist.includes(val.value)) {
        storeInfo.error = "not result";
        storeRef.value.style = "outline: 3px solid #E06D6D";
      } else {
        storeInfo.error = null;
        storeRef.value.style = "";
      }
    });
    //監控name
    watch(nameInfo, (val) => {
      if (val.value.trim() === "") {
        nameInfo.error = "required";
        nameRef.value.style = "outline: 3px solid #E06D6D";
      } else if (
        nameInfo.value.trim() ===
        nameInfo.value.replace(/^[\u4e00-\u9fa5a-zA-Z]+$/)
      ) {
        nameInfo.error = "wrong format";
        nameRef.value.style = "outline: 3px solid #E06D6D";
      } else {
        nameInfo.error = null;
        nameRef.value.style = "";
      }
    });
    //監控phone
    watch(phoneInfo, (val) => {
      if (val.value.trim() === "") {
        phoneInfo.error = "required";
        phoneRef.value.style = "outline: 3px solid #E06D6D";
      } else if (
        phoneInfo.value.trim() === phoneInfo.value.replace(/^09[0-9]{8}$/)
      ) {
        phoneInfo.error = "wrong format";
        phoneRef.value.style = "outline: 3px solid #E06D6D";
      } else {
        phoneInfo.error = null;
        phoneRef.value.style = "";
      }
    });
    //監控Amount of consumption
    watch(amountInfo, (val) => {
      if (val.value.trim() === "") {
        amountInfo.error = "required";
        amountRef.value.style = "outline: 3px solid #E06D6D";
      } else if (
        amountInfo.value.trim() !== amountInfo.value.replace(/[^\d]/g, "")
      ) {
        amountInfo.error = "wrong format";
        amountRef.value.style = "outline: 3px solid #E06D6D";
      } else {
        amountInfo.error = null;
        amountRef.value.style = "";
      }
      //監控payment
      watch(paymentInfo, (val) => {
        if (val.value.trim() === "") {
          paymentInfo.error = "required";
          paymentRef.value.style = "outline: 3px solid #E06D6D";
        } else {
          paymentInfo.error = null;
          paymentRef.value.style = "";
        }
      });
    });

    function check() {
      btnState.value = 2;
      //檢查store
      if (storeInfo.value.trim() === "") {
        storeInfo.error = "required";
        storeRef.value.style = "outline: 3px solid #E06D6D";
      }
      //檢查name
      if (nameInfo.value.trim() === "") {
        nameInfo.error = "required";
        nameRef.value.style = "outline: 3px solid #E06D6D";
      }
      //檢查phone
      if (phoneInfo.value.trim() === "") {
        phoneInfo.error = "required";
        phoneRef.value.style = "outline: 3px solid #E06D6D";
      }
      //檢查Amount of consumption
      if (amountInfo.value.trim() === "") {
        amountInfo.error = "required";
        amountRef.value.style = "outline: 3px solid #E06D6D";
      }
      //檢查payment
      if (paymentInfo.value.trim() === "") {
        paymentInfo.error = "required";
        paymentRef.value.style = "outline: 3px solid #E06D6D";
      }

      if (
        storeInfo.error === null &&
        nameInfo.error === null &&
        phoneInfo.error === null &&
        amountInfo.error === null &&
        paymentInfo.error === null
      ) {
        btnState.value = 1;
      }
    }
    return {
      storeInfo,
      storeRef,
      nameInfo,
      nameRef,
      phoneInfo,
      phoneRef,
      amountInfo,
      amountRef,
      paymentInfo,
      paymentRef,
      btnState,
      check,
    };
  },
};
</script>

<style lang="scss" scoped>
.form {
  display: flex;
  flex-direction: column;
  align-items: center;
  padding-top: 60px;
  .container {
    width: 808px;
    height: 575px;
    background: #ffffff;
    border: 2px solid #b57556;
    box-shadow: 0px 1px 20px rgba(73, 72, 72, 0.25);
    border-radius: 16px;
    margin: 60px 0;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: space-evenly;
    position: relative;
    img {
      position: absolute;
      top: -30px;
    }
    .turtle {
      right: 302px;
      top: -33px;
      animation: moveLeft 5s infinite linear;
    }
    select,
    input,
    datalist {
      width: 768px;
      height: 57px;
      border: 1px solid #204379;
      border-radius: 20px;
      padding-left: 15px;
    }
  }
  input:focus,
  select:focus {
    outline: 3px solid #93bbf9;
  }

  .error {
    color: #e06d6d;
    font-weight: 400;
    font-size: 12px;
    line-height: 140%;
  }
  .btnBox {
    button {
      display: flex;
      justify-content: center;
      align-items: center;
      margin-bottom: 60px;
      background-color: #b57556;
      color: #ffffff;
      border: none;
      cursor: pointer;
      width: 200px;
      height: 57px;
      box-shadow: 0px 4px 10px rgba(40, 35, 35, 0.35),
        0px -4px 10px rgba(255, 255, 255, 0.9);
      border-radius: 50px;
      font-weight: 700;
      font-size: 20px;
      line-height: 125%;
      letter-spacing: 0.2em;
      transition: background-color 0.3s ease;
      animation: scale 2s infinite;
      &:hover {
        background-color: #d3a995;
      }
      img {
        margin-right: 10px;
      }
    }
    .success {
      color: #e6ffb1;
    }
    .failure {
      color: #ffe3e3;
    }
  }
}
@media screen and (max-width: 840px) {
  .form {
    .container {
      width: 720px;
      .turtle {
        right: 260px;
      }
      select,
      input,
      datalist {
        width: 680px;
      }
    }
  }
}
@media screen and (max-width: 730px) {
  .form {
    .container {
      width: 550px;
      .turtle {
        right: 170px;
      }
      select,
      input,
      datalist {
        width: 510px;
      }
    }
  }
}
@media screen and (max-width: 560px) {
  .form {
    .container {
      width: 366px;
      .turtle {
        right: 80px;
      }
      select,
      input,
      datalist {
        width: 326px;
      }
    }
  }
}
@keyframes scale {
  /* 0% 表示動畫的開始時刻 */
  0% {
    transform: scale(1);
  }

  /* 50% 表示動畫的中間時刻 */
  50% {
    transform: scale(1.2);
  }

  /* 100% 表示動畫的結束時刻 */
  100% {
    transform: scale(1);
  }
}
@keyframes moveLeft {
  /* 0% 表示動畫的開始時刻 */
  0% {
    transform: translateX(0);
  }

  /* 100% 表示動畫的結束時刻 */
  100% {
    transform: translateX(-200%);
  }
}
</style>
