<template>
  <header>
    <div class="search-box">
    <router-link to="/"><img v-bind:src="img" alt="" id="home" class="home"/></router-link>

      <div class="search-control">
         <input class="search" :placeholder="prompt + selected" />
      <div class="search-select">
        <button @click="show = !show" class="search-class">▼</button>
        <transition
          @enter="enter"
          @leave="leave"
          @after-enter="afterEnter"
          @after-leave="afterLeave"
        >
          <div v-if="show">
            <div class="block" id="v-model-radiobutton">
              <div>
                <input
                  type="radio"
                  value="標題"
                  v-model="selected"
                  id="title"
                  name="selected"
                />
                <label for="title">標題</label>
              </div>

              <div>
                <input
                  type="radio"
                  value="作者"
                  id="user"
                  v-model="selected"
                  name="selected"
                />
                <label for="user">作者</label>
              </div>
              <div>
                <input
                  type="radio"
                  value="日期"
                  id="date"
                  v-model="selected"
                  name="selected"
                />
                <label for="date">日期</label>
              </div>
              <div>
                <input
                  type="radio"
                  value="分類"
                  id="class"
                  v-model="selected"
                  name="selected"
                />
                <label for="class">分類</label>
              </div>
            </div>
          </div>
        </transition>
      </div>
      </div>
     
    </div>
    <div class="button-box">
      <Login />
    </div>
  </header>
</template>

<script>
import Login from "./Login";

export default {
  name: "Header",
  data() {
    return {
      img: require("../../static/img/icon.png"),
      prompt: "請輸入",
      selected: "標題",
      show: false,
    };
  },

  components: {
    Login,
  },
};
</script>

<style scoped>
header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 3px 200px 3px 200px;
}
.search-box{
  display: flex;  
  align-items: center;
}

.search-box>.search-control {
  display: flex;
  width: 200px;
  height: 25px;
  padding: 5px 10px;
  border-radius: 20px;
  background-color: white;
}
.search-control > .search {
  border: none;
  outline: none;
}
.search-control > .search-select {
  border-radius: 50%;
}
.button-box {
  display: flex;
  align-items: center;
  justify-content: center;
}
#home {
  width: 50px;
}
.home{
  margin: 3px 20px 0px 0px;
}
.v-leave {
  opacity: 1;
}

.v-leave-active {
  transition: opacity 0.5s;
}

.v-leave-to {
  opacity: 0;
}

.v-enter {
  opacity: 0;
}

.v-enter-active {
  transition: opacity 0.5s;
}

.v-enter-to {
  opacity: 1;
}

button {
  margin-bottom: 10px;
}
.block {
  display: flex;
  background: rgb(255, 255, 255);
  width: 230px;
  height: 30px;
  margin-top: 10px;
  border-radius: 5px;
  position: absolute;
  left: 265px;
}
.search-class {
  border-radius: 100px;
}
</style>