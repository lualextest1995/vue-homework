<template>
  <div class="form">
    <div class="container">
      <img id="form" src="../assets/Frame1819.svg" alt="" />
      <img class="turtle" src="../assets/turtle.svg" alt="" />
      <InputComponent item="store">
        <input
          list="store"
          placeholder="placeholder text"
          v-model="storeValue"
          ref="storeRef"
        />
        <datalist id="store">
          <option v-for="data in datalist" :key="data" :value="data">
            {{ data }}
          </option>
        </datalist>
        <p class="error" v-show="storeError">{{ storeError }}</p>
      </InputComponent>
      <InputComponent item="name">
        <input
          type="text"
          id="name"
          placeholder="placeholder text"
          v-model="nameValue"
          ref="nameRef"
        />
        <p class="error" v-show="nameError">{{ nameError }}</p>
      </InputComponent>
      <InputComponent item="phone">
        <input
          type="text"
          id="phone"
          placeholder="placeholder text"
          v-model="phoneValue"
          ref="phoneRef"
        />
        <p class="error" v-show="phoneError">{{ phoneError }}</p>
      </InputComponent>
      <InputComponent item="Amount of consumption">
        <input
          type="text"
          id="Amount of consumption"
          placeholder="placeholder text"
          v-model="amountValue"
          ref="amountRef"
        />
        <p class="error" v-show="amountError">{{ amountError }}</p>
      </InputComponent>
      <InputComponent item="payment">
        <select id="payment" v-model="paymentValue" ref="paymentRef">
          <option value="" disabled>placeholder text</option>
          <option value="digital payment">digital payment</option>
          <option value="ATM">ATM</option>
        </select>
        <p class="error" v-show="paymentError">{{ paymentError }}</p>
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
import { ref, watch } from "vue";
import InputComponent from "./InputComponent.vue";
export default {
  name: "FormComponent",
  components: { InputComponent },
  setup() {
    const storeValue = ref("");
    const storeRef = ref(null);
    const storeError = ref(null);
    const datalist = ref(["store1", "store2", "store3", "store4"]);
    const nameValue = ref("");
    const nameRef = ref(null);
    const nameError = ref(null);
    const phoneValue = ref("");
    const phoneRef = ref(null);
    const phoneError = ref(null);
    const amountValue = ref("");
    const amountRef = ref(null);
    const amountError = ref(null);
    const paymentValue = ref("digital payment");
    const paymentRef = ref(null);
    const paymentError = ref(null);
    const btnState = ref(0);

    //監控store
    watch(storeValue, (val) => {
      if (val === "") {
        storeError.value = "required";
        storeRef.value.style = "outline: 3px solid #E06D6D";
      } else if (!datalist.value.includes(val)) {
        storeError.value = "not result";
        storeRef.value.style = "outline: 3px solid #E06D6D";
      } else {
        storeError.value = null;
        storeRef.value.style = "";
      }
    });
    //監控name
    watch(nameValue, (val) => {
      if (val === "") {
        nameError.value = "required";
        nameRef.value.style = "outline: 3px solid #E06D6D";
      } else if (
        nameValue.value.trim() ===
        nameValue.value.replace(/^[\u4e00-\u9fa5a-zA-Z]+$/)
      ) {
        nameError.value = "wrong format";
        nameRef.value.style = "outline: 3px solid #E06D6D";
      } else {
        nameError.value = null;
        nameRef.value.style = "";
      }
    });
    //監控phone
    watch(phoneValue, (val) => {
      if (val === "") {
        phoneError.value = "required";
        phoneRef.value.style = "outline: 3px solid #E06D6D";
      } else if (
        phoneValue.value.trim() === phoneValue.value.replace(/^09[0-9]{8}$/)
      ) {
        phoneError.value = "wrong format";
        phoneRef.value.style = "outline: 3px solid #E06D6D";
      } else {
        phoneError.value = null;
        phoneRef.value.style = "";
      }
    });
    //監控Amount of consumption
    watch(amountValue, (val) => {
      if (val === "") {
        amountError.value = "required";
        amountRef.value.style = "outline: 3px solid #E06D6D";
      } else if (
        amountValue.value.trim() !== amountValue.value.replace(/[^\d]/g, "")
      ) {
        amountError.value = "wrong format";
        amountRef.value.style = "outline: 3px solid #E06D6D";
      } else {
        amountError.value = null;
        amountRef.value.style = "";
      }
      //監控payment
      watch(paymentValue, (val) => {
        if (val === "") {
          paymentError.value = "required";
          paymentRef.value.style = "outline: 3px solid #E06D6D";
        } else {
          paymentError.value = null;
          paymentRef.value.style = "";
        }
      });
    });

    function check() {
      btnState.value = 2;
      //檢查store
      if (storeValue.value.trim() === "") {
        storeError.value = "required";
        storeRef.value.style = "outline: 3px solid #E06D6D";
      }
      //檢查name
      if (nameValue.value.trim() === "") {
        nameError.value = "required";
        nameRef.value.style = "outline: 3px solid #E06D6D";
      }
      //檢查phone
      if (phoneValue.value.trim() === "") {
        phoneError.value = "required";
        phoneRef.value.style = "outline: 3px solid #E06D6D";
      }
      //檢查Amount of consumption
      if (amountValue.value.trim() === "") {
        amountError.value = "required";
        amountRef.value.style = "outline: 3px solid #E06D6D";
      }
      //檢查payment
      if (paymentValue.value.trim() === "") {
        paymentError.value = "required";
        paymentRef.value.style = "outline: 3px solid #E06D6D";
      }

      if (
        storeError.value === null &&
        nameError.value === null &&
        phoneError.value === null &&
        amountError.value === null &&
        paymentError.value === null
      ) {
        btnState.value = 1;
      }
    }
    return {
      storeValue,
      storeRef,
      storeError,
      datalist,
      nameValue,
      nameRef,
      nameError,
      phoneValue,
      phoneRef,
      phoneError,
      amountValue,
      amountRef,
      amountError,
      paymentValue,
      paymentRef,
      paymentError,
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
