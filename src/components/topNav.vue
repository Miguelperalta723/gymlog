<template>
  <div class="nav-container">
      <div class="name">name?</div>
      <div class="add" @click="add()">+</div>
  </div>
</template>

<script>
export default {
    data: function (){
        return {
            addForm: false,
        }
    },
    methods: {
        add: function () {
            this.addForm = true;
            this.$emit('addForm', true);
        }
    }
}
</script>

<style>
.nav-container {
    border: 2px solid orangered;
    height: 60px;
    width: 100%;
    display: flex;
    justify-content: space-between;
    background-color: orange;
}

.add {
    border: 4px solid peru;
    border-radius: 50%;
    background-color: peru;
    padding: 10px;
}
</style>