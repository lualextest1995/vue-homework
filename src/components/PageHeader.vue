<template>
  <div class="head">
    <img class="wave" src="../assets/海浪.svg" alt="" />
    <img class="wave1" src="../assets/海浪.svg" alt="" />
    <div class="wavebox">
      <img src="../assets/白色海浪.svg" alt="" />
    </div>
    <h1>There is no one</h1>
    <h1>who loves pain</h1>
    <a href="#form">
      <button class="form">FORM</button>
    </a>
    <div class="container">
      <img class="sup" src="../assets/sup.svg" alt="" />
      <img class="paddle" src="../assets/船槳.svg" alt="" />
      <img class="bigCircle" src="../assets/Ellipse246.svg" alt="" />
      <img class="circle" src="../assets/Ellipse248.svg" alt="" />
      <img class="firework" src="../assets/煙火.svg" alt="" />
      <img class="firework-sup" src="../assets/sup煙火.svg" alt="" />
      <strong class="paragraph">
        <img src="../assets/cactus.svg" alt="" />
        paragraph
        <img src="../assets/cactus.svg" alt="" />
      </strong>
      <ol>
        <li>Lorem ipsum dolor sit amet,consectrtur adipiscing elit.</li>
      </ol>
      <strong class="paragraph">
        <img src="../assets/cactus.svg" alt="" />
        paragraph
        <img src="../assets/cactus.svg" alt="" />
      </strong>
      <ol class="second">
        <li>
          Quisque sodales leo
          <strong class="underline">vitae vulputate auctor.</strong>
        </li>
        <li>
          Proin ac justo ut nisl tincidunt imperdiet.Maecenas viverra libero a
          pellentesque blabdit.
        </li>
        <li>Cras tristique tellus id leo bibendum,eu dapibus nisl accumsan.</li>
        <li>
          Donec ultrices sapien
          <strong>vitae leo venenatis ullamcorper.</strong>
        </li>
      </ol>
    </div>
  </div>
</template>

<script>
export default {
  name: "PageHeader",
  setup() {
    return {};
  },
};
</script>

<style lang="scss" scoped>
.head {
  height: 900px;
  background-image: url(../assets/底色.svg);
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  position: relative;
  .wave {
    position: absolute;
    z-index: 2;
    right: 0;
    bottom: -50px;
    width: 50%;
  }
  .wave1 {
    position: absolute;
    z-index: 2;
    left: 0;
    bottom: -50px;
    width: 50%;
  }

  .wavebox {
    position: absolute;
    width: 100%;
    height: 800px;
    z-index: 0;
    img {
      width: 100%;
      height: 800px;
      object-fit: cover;
      object-position: 0 90px;
    }
  }

  h1 {
    text-align: center;
    font-size: 32px;
    line-height: 125%;
    letter-spacing: 0.2em;
    color: #ffffff;
    &:nth-child(2) {
      font-size: 28px;
    }
  }
  a {
    z-index: 1;
    .form {
      width: 200px;
      height: 57px;
      background: #b57556;
      box-shadow: 0px 0px 20px rgba(250, 163, 163, 0.91);
      border-radius: 50px;
      font-size: 18px;
      line-height: 125%;
      letter-spacing: 0.2em;
      color: #ffffff;
      margin: 30px 0;
      border: none;
      cursor: pointer;
      transition: all 0.3s ease;
      position: relative;
      z-index: 1;
      &:hover,
      &:focus {
        color: #fff;
      }
      &:before {
        content: "";
        background: #b57556;
        width: 100%;
        height: 100%;
        border-radius: 50px;
        position: absolute;
        left: 0;
        top: 0;
        z-index: -1;
      }
      &:after {
        content: "";
        background: linear-gradient(
          124deg,
          #efdbc8,
          #e9c87f,
          #b2e1ea,
          #90cae5,
          #f5caf4,
          #dfc9f9
        );
        background-size: auto;
        background-size: 400%;
        width: calc(100% + 4px);
        height: calc(100% + 4px);
        border-radius: 50px;
        filter: blur(5px);
        opacity: 1;
        position: absolute;
        left: -2px;
        top: -2px;
        z-index: -2;
        transition: all 0.3s ease-in-out;
        animation: move 20s linear infinite;
      }
    }
  }
  .container {
    width: 808px;
    height: 322px;
    background: #dae4f1;
    border: 2px solid #b57556;
    border-radius: 20px;
    display: flex;
    flex-direction: column;
    align-items: center;
    z-index: 1;
    position: relative;
    .sup {
      position: absolute;
      top: -40px;
      right: 10px;
      z-index: 2;
    }
    .paddle {
      position: absolute;
      top: -25px;
      right: 10px;
      z-index: 2;
      animation: swing 2s infinite;
    }
    .circle {
      position: absolute;
      top: -90px;
      right: 0px;
      z-index: 2;
      animation: moveUp 10s infinite;
    }

    .bigCircle {
      position: absolute;
      top: -55px;
      right: 45px;
      z-index: 2;
      animation: moveUp 5s infinite;
    }
    .firework {
      position: absolute;
      bottom: -50px;
      left: 20px;
      z-index: 3;
      animation: scaleAndFade 2s infinite;
    }
    .firework-sup {
      position: absolute;
      bottom: -50px;
      left: 50px;
      z-index: 2;
    }
    strong {
      text-align: center;
      font-size: 18px;
      color: #204379;
    }
    .paragraph {
      display: flex;
      align-items: center;
      justify-content: center;
      margin: 12px 0;
      img {
        margin: 0 0.5rem;
      }
    }
    ol {
      margin-left: 50px;
      align-self: start;
      li {
        font-weight: 400;
        font-size: 16px;
        line-height: 140%;
        color: #204379;
      }
    }
    .second {
      li {
        line-height: 180%;
        .underline {
          text-decoration: underline;
        }
      }
    }
  }
}
@media screen and(max-width:840px) {
  .head {
    .container {
      width: 720px;
    }
  }
}
@media screen and(max-width:730px) {
  .head {
    .wave,
    .wave1 {
      bottom: -20px;
    }
    .container {
      width: 550px;
      height: 430px;
    }
  }
}
@media screen and(max-width:560px) {
  .head {
    .container {
      width: 366px;
      height: 489px;
      .paragraph {
        margin: 5px 0;
      }
    }
  }
}

@keyframes move {
  0% {
    background-position: 0 0;
  }
  50% {
    background-position: 400% 0;
  }
  100% {
    background-position: 0 0;
  }
}
@media only screen and (max-width: 767px) {
  .form {
    margin-bottom: 30px;
  }
}

@keyframes scaleAndFade {
  0% {
    transform: scale(1);
    opacity: 1;
  }
  50% {
    transform: scale(1.5);
    opacity: 0.5;
  }
  100% {
    transform: scale(1.5);
    opacity: 0;
  }
}

@keyframes moveUp {
  0% {
    transform: translateY(150%);
  }
  100% {
    transform: translateY(0);
  }
}

@keyframes swing {
  0% {
    transform: rotate(0deg);
  }
  50% {
    transform: rotate(50deg);
  }
  100% {
    transform: rotate(0deg);
  }
}
</style>
