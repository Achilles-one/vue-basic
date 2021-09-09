<template>
  <h1>{{ title }}</h1>
  <p>Welcome...</p>
  <teleport to=".testmo" v-if="showModal">
    <modal theme="sale" @close="toggleModal">
      <!-- @close="toggleModal"表示父组件监听到事件后执行函数 -->
      <template v-slot:links>
        <a href="#">sign up now</a>
        <a href="#">more info</a>
      </template>
      <h1>使用slot将父组件的内容放到子组件内</h1>
      <p>这个也包括</p>
    </modal>
    
  </teleport>

  <div v-if="showModal2">
    <modal theme="bl" @close="toggleModal2">
      <!-- @close="toggleModal"表示父组件监听到事件后执行函数 -->
      <!-- <template v-slot:links>
        <a href="#">sign up now</a>
        <a href="#">more info</a>
      </template> -->
      <h1>第二个modal</h1>
      <p>这个也包括</p>
    </modal>
  </div>

  <button @click.shift="toggleModal">open modal (shift)</button>
  <br>
  <button @click="toggleModal2">show modal2</button>

 
</template>

<script>
import modal from "./components/modal.vue";

export default {
  name: "App",
  components: {
    modal,
  },
  data() {
    return {
      title: "My VUE :)",
      showModal: false,
      showModal2: false,
    };
  },
  methods: {
    toggleModal() {
      this.showModal = !this.showModal;
    },
    toggleModal2() {
      this.showModal2 = !this.showModal2;
    },
  },
};
</script>

<style>
#app, .testmo {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
h1 {
  border-bottom: 1px solid #ddd;
  display: inline-block;
  padding-bottom: 10px;
}
</style>
