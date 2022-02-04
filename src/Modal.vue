<template>
  <div class="black-bg" v-if="modalStatus == true">
    <div class="white-bg">
      <img :src="onerooms[clickNum].image" alt="" />
      <h4>{{ onerooms[clickNum].title }}</h4>
      <p>{{ onerooms[clickNum].content }}</p>
      <p>{{ onerooms[clickNum].price }}원</p>
      <!-- <button @click="modalStatus = false">닫기</button> -->
    </div>
  </div>
</template>

<script>
export default {
  name: "Modal",
  props: {
    onerooms: Array,
    clickNum: Number,
    modalStatus: Boolean,
  },
};
</script>

<style></style>
