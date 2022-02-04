<template>

  <!-- <div v-if="1 == 2">
    안녕하세요
  </div>
  <div v-else-if="1 == 3">
    안녕하세요2
  </div> -->

  <div class="black-bg" v-if="modalStatus == true">
    <div class="white-bg">
      <img :src="onerooms[clickNum].image" alt="">
      <h4>{{ onerooms[clickNum].title }}</h4>
      <p>{{ onerooms[clickNum].price }}원 <br> {{ onerooms[clickNum].content }}</p>
      <button @click="modalStatus = false">닫기</button>
    </div>
  </div>

  <div class="menu">
    <a v-for="a in menus" :key="a">{{ a }}</a>
  </div>

  <div v-for="(a,i) in onerooms" :key="i">
    <img :src="a.image" class="room-img">
    <h4 @click="modalStatus = true; clickNum = i">{{ a.title }} 원룸</h4>
    <p>{{ a.price }}원</p>
    <button @click="increase(0)">허위매물신고</button> <span>신고수 : {{ reports[0] }}</span>
  </div>
</template>

<script>

import data from './assets/oneroom';


export default {
  name: 'App',
  data(){
    return {
      clickNum : 0,
      onerooms : data,
      modalStatus : false,
      reports : [0, 0, 0],
      menus : ['Home', 'Shop', 'About'],
      products : ['역삼동원룸', '천호동원룸', '마포구원룸'],
    }
  },
  methods : {
    increase(i){
      this.reports[i]++;
    },
  },
  components: {
  }
}
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


</style>
