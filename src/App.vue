<template>
  <div class="menu">
    <a v-for="(item, i) in menuItems" :key="item + i">{{ item }}</a>
  </div>
  <div v-for="(product, index) in products" :key="product.where + index">
    <!-- 모달창 -->
    <div class="black-bg" v-if="product.isModal === true">
      <div class="white-bg">
        <button @click="product.isModal = false">X</button>
        <h4>{{ product.where }} 원룸</h4>
        <p>월세 : {{ product.price }}만원</p>
        <p v-html="product.detail"></p>
      </div>
    </div>

    <!-- 매물 목록 -->
    <img
      :src="`./assets/room${index}.jpg`"
      alt="매물사진{{ product.where }}"
      class="roomImg"
      @click="product.isModal = true" />
    <h4>{{ product.where }} 원룸</h4>
    <p>월세 : {{ product.price }} 만원</p>
    <button @click="product.danger++">허위매물 신고</button>
    <p>신고된 수: {{ product.danger }}</p>
  </div>
</template>

<script>
export default {
  name: 'App',
  data() {
    return {
      menuItems: ['Home', 'Shop', 'About'],
      products: [
        {
          where: '역삼동',
          price: 60,
          danger: 0,
          isModal: false,
          detail: `저희 역삼 원룸은 10평입니다.<br/> 채광이 잘들고 행복한 집이에요.<br/> 반려동물 고양이 환영입니다.<br/> 수도세,전기세,인터넷망요금은 관리비에 포함되어있고, 관리비는 3만원입니다.`,
        },
        {
          where: '천호동',
          price: 40,
          danger: 0,
          isModal: false,
          detail: `저희 천호 원룸은 10평입니다.<br/> 채광이 잘들고 행복한 집이에요.<br/> 반려동물 고양이 환영입니다.<br/> 수도세,전기세,인터넷망요금은 관리비에 포함되어있고, 관리비는 3만원입니다.`,
        },
        {
          where: '마포동',
          price: 50,
          danger: 0,
          isModal: false,
          detail: `저희 마포 원룸은 10평입니다.<br/> 채광이 잘들고 행복한 집이에요.<br/> 반려동물 고양이 환영입니다.<br/> 수도세,전기세,인터넷망요금은 관리비에 포함되어있고, 관리비는 3만원입니다.`,
        },
      ],
    };
  },
  components: {},
};
</script>

<style lang="scss">
body {
  margin: 0;
  div {
    box-sizing: border-box;
    position: relative;
    padding-bottom: 40px;
  }
  .black-bg {
    position: absolute;
    width: 100%;
    height: 100%;
    background: rgba(0, 0, 0, 0.5);
    padding: 20px;
  }
  .white-bg {
    width: 60%;
    background: white;
    border-radius: 8px;
    padding: 20px;
    margin: 0 auto;
    position: relative;
    top: 40%;
    button {
      background-color: #2c3e50;
      color: #fff;
      border: none;
      outline: none;
      padding: 8px 12px;
      font-size: 24px;
      border-radius: 2px;
      position: absolute;
      right: 40px;
      &:hover {
        background-color: #fee902;
        color: #2c3e50;
      }
    }
  }
}

#app {
  font-family: Arial, Helvetica, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;

  .menu {
    background: darkcyan;
    padding: 15px;

    a {
      color: #fff;
      padding: 10px;
      &:hover {
        color: #fee902;
      }
    }
  }

  .roomImg {
    width: 50%;
    margin-top: 40px;
  }
}
</style>
