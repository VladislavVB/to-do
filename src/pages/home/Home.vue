<template>
  <div class="home">
    <div class="container">
      <div class="home__head">
        <input class="post__input" type="text" placeholder="Описание дела..." />
        <button class="btn post__add">Добавить</button>
      </div>
      <div class="home__posts">
        <div v-for="post in posts" :key="post.id" class="home__post">
          <div class="home__post-head">
            <div class="home__post-title">{{ post.title }}</div>
            <div class="home__post-btns">
              <button class="complite"></button>
              <button class="remove">
                <img src="@/assets/del.svg" alt="" />
              </button>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Home",
  data() {
    return {
      posts: [
        { id: 1, title: "Дело 1" },
        { id: 2, title: "Дело 2" },
        { id: 3, title: "Дело 3" },
      ],
    };
  },
};
</script>

<style lang="scss" scoped>
.home {
  background-color: #a8d7da;
  min-height: 100vh;
  &__head {
    display: flex;
    padding-top: 50px;
    justify-content: space-between;
  }
  &__posts {
    border-radius: 20px;
    width: 100%;
    overflow: hidden;
    margin-top: 40px;
  }
  &__post {
    background-color: #fff;
    padding: 5px 20px;
    border-bottom: 1px solid #c4c4c4;
    color: #000;
    &:last-child {
      border-bottom: 0px solid #c4c4c4;
    }
    &-head {
      display: flex;
      justify-content: space-between;
      align-items: center;
    }
    &-btns {
      display: flex;
      button {
        border-radius: 50%;
        border: none;
        width: 30px;
        height: 30px;
        display: flex;
        justify-content: center;
        align-items: center;
        cursor: pointer;
      }
    }
  }
}
.post {
  &__add {
    width: 140px;
    height: 40px;
    background: #7d83b9;
    border-radius: 20px;
    color: #fff;
    border: none;
    cursor: pointer;
  }
  &__input {
    padding: 0 20px;
    width: 650px;
    background: #ffffff;
    border: 1px solid #c4c4c4;
    box-shadow: inset 0px 0px 10px 1px rgba(0, 0, 0, 0.25);
    border-radius: 20px;
  }
}
.complite {
  background-color: #71A663;
}
.remove {
  background-color: #c15151;
  margin-left: 10px;
}
</style>
