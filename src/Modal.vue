<template>
  <div class="black-bg" v-if="modalStatus == true">
    <div class="white-bg">
      <img :src="onerooms[clickNum].image" alt="" />
      <h4>{{ onerooms[clickNum].title }}</h4>
      <p>{{ onerooms[clickNum].content }}</p>
      <!-- <input type="text" @input="month = $event.target.value" /> -->
      <input type="text" v-model.number="month" />
      <p>{{ month }}개월 선택함 : {{ onerooms[clickNum].price * month }}원</p>
      <button @click="$emit('closeModal')">닫기</button>
    </div>
  </div>
</template>

<script>
export default {
  name: "Modal",
  data() {
    return {
      month: 1,
    };
  },
  props: {
    onerooms: Array,
    clickNum: Number,
    modalStatus: Boolean,
  },
};
</script>

<style></style>
