<template>
  <TaskTable></TaskTable>
</template>

<script>
import TaskTable from '@/components/TaskTable.vue'

export default {
  name: 'App',
  components: {TaskTable}
}
</script>

<style>
* {
  margin: 0;
  box-sizing: border-box;
}
</style>
