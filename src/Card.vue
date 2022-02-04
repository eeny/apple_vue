<template>
  <div>
    <img :src="onerooms.image" class="room-img" />
    <h4 @click="emitFunc">{{ onerooms.title }} 원룸</h4>
    <p>{{ onerooms.price }}원</p>
    <!-- <button @click="increase(0)">허위매물신고</button>
    <span>신고수 : {{ reports[0] }}</span> -->
  </div>
</template>

<script>
export default {
  name: "Card",
  props: {
    onerooms: Object,
  },
  methods: {
    emitFunc() {
      this.$emit("openModal", this.onerooms.id);
    },
  },
};
</script>

<style>
.room-img {
  width: 100%;
  margin-top: 40px;
}
</style>
