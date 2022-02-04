<template>
  <div class="discount">
    <h4>지금 결제하면 {{ percentage }}% 할인</h4>
  </div>
</template>

<script>
export default {
  name: "Discount",
  data() {
    return {
      percentage: 30,
    };
  },
  mounted() {
    setInterval(() => {
      if (this.percentage > 0) {
        this.percentage--;
      }
    }, 1000);
  },
};
</script>

<style></style>
