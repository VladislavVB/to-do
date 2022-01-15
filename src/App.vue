<template>
  <router-view />
</template>

<style lang="scss">
@import url("https://fonts.googleapis.com/css2?family=Montserrat&display=swap");
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
  font-family: "Montserrat", sans-serif;
  font-weight: 400;
  font-size: 14px;
}
.container {
  max-width: 800px;
  margin: auto;
}

@media (max-width: 992px) {
  .container {
    width: 97%;
  }
}

@media (max-width: 575px) {
  * {
    font-size: 12px;
  }
}
</style>
