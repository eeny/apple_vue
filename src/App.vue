<template>
  <!-- <div v-if="1 == 2">
    안녕하세요
  </div>
  <div v-else-if="1 == 3">
    안녕하세요2
  </div> -->

  <Modal :onerooms="onerooms" :clickNum="clickNum" :modalStatus="modalStatus" />

  <div class="menu">
    <a v-for="a in menus" :key="a">{{ a }}</a>
  </div>

  <Discount />

  <Card
    :onerooms="onerooms[i]"
    :clickNum="clickNum"
    :modalStatus="modalStatus"
    :reports="reports"
    v-for="(a, i) in onerooms"
    :key="i"
  />
  <!-- <Card
    :onerooms="onerooms[0]"
    :clickNum="clickNum"
    :modalStatus="modalStatus"
    :reports="reports"
  />
  <Card
    :onerooms="onerooms[1]"
    :clickNum="clickNum"
    :modalStatus="modalStatus"
    :reports="reports"
  />
  <Card
    :onerooms="onerooms[2]"
    :clickNum="clickNum"
    :modalStatus="modalStatus"
    :reports="reports"
  />
  <Card
    :onerooms="onerooms[3]"
    :clickNum="clickNum"
    :modalStatus="modalStatus"
    :reports="reports"
  />
  <Card
    :onerooms="onerooms[4]"
    :clickNum="clickNum"
    :modalStatus="modalStatus"
    :reports="reports"
  />
  <Card
    :onerooms="onerooms[5]"
    :clickNum="clickNum"
    :modalStatus="modalStatus"
    :reports="reports"
  /> -->
</template>

<script>
import data from "./assets/oneroom";
import Discount from "./Discount.vue";
import Modal from "./Modal.vue";
import Card from "./Card.vue";

export default {
  name: "App",
  data() {
    return {
      object: { name: "kim", age: "20" },
      clickNum: 0,
      onerooms: data,
      modalStatus: false,
      reports: [0, 0, 0],
      menus: ["Home", "Shop", "About"],
      products: ["역삼동원룸", "천호동원룸", "마포구원룸"],
    };
  },
  methods: {
    increase(i) {
      this.reports[i]++;
    },
  },
  components: {
    Discount: Discount,
    Modal: Modal,
    Card: Card,
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

body {
  margin: 0;
}

div {
  box-sizing: border-box;
}

.black-bg {
  width: 100%;
  height: 100%;
  background: rgba(0, 0, 0, 0.5);
  position: fixed;
  padding: 20px;
}

.white-bg {
  width: 100%;
  background: white;
  border-radius: 8px;
  padding: 20px;
}

.menu {
  background: darkslateblue;
  padding: 15px;
  border-radius: 5px;
}

.menu a {
  color: white;
  padding: 10px;
}

.room-img {
  width: 100%;
  margin-top: 40px;
}

.white-bg img {
  width: 100%;
}

.discount {
  background: #eee;
  padding: 10px;
  margin: 10px;
  border-radius: 5px;
}
</style>
