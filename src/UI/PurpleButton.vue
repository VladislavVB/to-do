<template>
  <button class="purple-button"><slot></slot></button>
</template>
<script>
export default {
  name: "purple-button",
};
</script>
<style lang="scss" scoped>
.purple-button {
  width: 140px;
  height: 40px;
  background: #7d83b9;
  border-radius: 20px;
  color: #fff;
  border: none;
  cursor: pointer;
}
</style>
