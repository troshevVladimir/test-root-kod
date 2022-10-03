<template>
  <div class="card" group="asdasd">
    <div class="card-title">{{title}}</div>
  </div>
</template>

<script>
export default {
  props: {
    title: {
      type: String,
      required: true
    },
  }
}
</script>

<style>
.card {
  cursor: grab;
  background-color: #999;
  padding: 20px;
  width: 100%;
  border: 1px solid rgb(51, 81, 136);
  margin-bottom: 20px;
}

.card.selected {
  border: 1px dashed rgb(37, 39, 44);
}

</style>