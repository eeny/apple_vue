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
  watch: {
    month(a) {
      if (a >= 13) {
        alert("13이상 입력할 수 없습니다");
        this.month = 1;
      } else if (isNaN(a) == true) {
        alert("문자는 입력할 수 없습니다");
        this.month = 1;
      }
    },
  },
  props: {
    onerooms: Array,
    clickNum: Number,
    modalStatus: Boolean,
  },
  updated() {
    if (this.month == 2) {
      alert("2개월은 선택하실 수 없습니다.");
      this.month = 3;
    }
  },
};
</script>

<style></style>
