<template>
  <!-- <div v-if="1 == 2">
    안녕하세요
  </div>
  <div v-else-if="1 == 3">
    안녕하세요2
  </div> -->

  <!-- <div class="start" :class="{ end: modalStatus }">
    <Modal
      @closeModal="modalStatus = false"
      :onerooms="onerooms"
      :clickNum="clickNum"
      :modalStatus="modalStatus"
    />
  </div> -->

  <transition name="fade">
    <Modal
      @closeModal="modalStatus = false"
      :onerooms="onerooms"
      :clickNum="clickNum"
      :modalStatus="modalStatus"
    />
  </transition>

  <div class="menu">
    <a v-for="a in menus" :key="a">{{ a }}</a>
  </div>

  <Discount />

  <button @click="priceSort">가격낮은순정렬</button>
  <button @click="priceSortReverse">가격높은순정렬</button>
  <button @click="titleSort">상품명가나다순정렬</button>
  <button @click="sortBack">되돌리기</button>

  <Card
    @openModal="
      modalStatus = true;
      clickNum = $event;
    "
    :onerooms="onerooms[i]"
    v-for="(a, i) in onerooms"
    :key="i"
  />
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
      oneroomsOrigin: [...data],
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
    priceSort() {
      this.onerooms.sort(function (a, b) {
        return a.price - b.price;
      });
    },
    sortBack() {
      this.onerooms = [...this.oneroomsOrigin];
    },
    priceSortReverse() {
      this.onerooms.sort(function (a, b) {
        return b.price - a.price;
      });
    },
    titleSort() {
      this.onerooms.sort(function (a, b) {
        if (a.title > b.title) {
          return 1;
        }
        if (a.title < b.title) {
          return -1;
        }
        if (a.title == b.title) {
          return 0;
        }
      });
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

.start {
  opacity: 0;
  transition: all 1s;
}

.end {
  opacity: 1;
}

.fade-enter-from {
  opacity: 0;
}
.fade-enter-active {
  transition: all 1s;
}
.fade-enter-to {
  opacity: 1;
}

.fade-leave-from {
  opacity: 1;
}
.fade-leave-active {
  transition: all 1s;
}
.fade-leave-to {
  opacity: 0;
}
</style>
