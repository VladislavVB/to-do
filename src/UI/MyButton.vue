<template>
  <button class="my-button"><slot></slot></button>
</template>
<script>
export default {
  name: 'my-button'
};
</script>
<style lang="scss" scoped>
.my-button {
  border-radius: 50%;
  border: none;
  width: 30px;
  height: 30px;
  display: flex;
  justify-content: center;
  align-items: center;
  cursor: pointer;
  margin-left: 10px;
  background-color: #71a663;
}
</style>
