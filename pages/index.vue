<template>
  <div class="container">
    <date></date>
    <div class="box"></div>
  </div>
</template>

<script>
  import Date from '~/components/Date.vue'
  export default {
    components: {Date}
  }
</script>

<style>
  .container {
    position: relative;
    margin: 0 auto;
    min-height: 100vh;
    background: linear-gradient(to bottom, #99DCBD 0%, #DAE9A8 60%, #2FCEFF 100%);
  }

  .box {
    transform: scale(2);
    left: 10%;
    position: absolute;
    bottom: 45%;
  }

  .box:before {
    content: '';
    position: absolute;
    z-index: 2;
    top: 60px;
    left: 50px;
    width: 50px;
    height: 50px;
    background: #f60;
    border-radius: 2px;
    transform: rotate(45deg);
    -webkit-animation: box 1s infinite;
  }

  @-webkit-keyframes box {
    0% {
      top: 50px;
    }
    20% {
      border-radius: 2px; /*从20%的地方才开始变形*/
    }
    50% {
      top: 80px;
      border-bottom-right-radius: 25px;
    }
    80% {
      border-radius: 2px; /*到80%的地方恢复原状*/
    }
    100% {
      top: 50px;
    }
  }

  .box:after {
    content: '';
    position: absolute;
    z-index: 1;
    top: 128px;
    left: 52px;
    width: 44px;
    height: 3px;
    background: #eaeaea;
    border-radius: 100%;
    -webkit-animation: shadow 1s infinite;
  }

  @-webkit-keyframes shadow {
    0%, 100% {
      left: 54px;
      width: 40px;
      background: #eaeaea;
    }
    50% {
      top: 126px;
      left: 50px; /*让阴影保持在原位*/
      width: 50px;
      height: 7px;
      background: #eee;
    }
  }

</style>
