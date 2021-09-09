<template>
  <div class="backdrop" @click.self="closeModal">

    <div class="modal" :class="{sale: theme === 'sale' }">
        <!-- <h1>hello</h1> -->
        <slot></slot>
      <div class="actions">
        <slot name="links"></slot>
      </div>
    </div>
  
    <div class="modal" :class="{ bl: theme === 'bl' }">
      <slot></slot>
    </div>
  
  </div>
</template>


<script>
export default {
  props: ["theme",],
  methods: {
    closeModal() {
      // 发射事件，使父组件监听
      this.$emit("close");
    },
  },
};
</script>


<style>
.modal.sale {
  background: orangered;
  /* color: white; */
}
.modal.bl {
    background: turquoise;
}
.modal {
  width: 400px;
  padding: 20px;
  margin: 50px auto;
  background: white;
  border-radius: 10px;
}
.backdrop {
  top: 0;
  position: fixed;
  background: rgba(0, 0, 0, 0.5);
  width: 100%;
  height: 100%;
}
.modal h1 {
  color: #03cfb4;
  border: none;
  padding: 0;
}
.modal .actions {
  text-align: center;
  margin: 20px 0 10px 0;
}
.modal .actions a {
  color: rgb(19, 18, 18);
  padding: 8px;
  border: 1px solid #eee;
  border-radius: 4px;
  text-decoration: none;
  margin: 10px;
}
</style>