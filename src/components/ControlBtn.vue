<template>
  <div>
    <img class="control-img" :src="require(`@/assets/${img}.png`)" />
  </div>
</template>

<script>
export default {
  name: "ControlBtn",
  props: {
    img: String,
  },
};
</script>

<style scoped>
.control-img {
  width: 100%;
  height: 100%;
}
</style>
