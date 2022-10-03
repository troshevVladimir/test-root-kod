<template>
  <div class="table">
    <div
      class="table__column"
      @drop="onDrop($event, 1)"
      @dragover.prevent
      @dragenter.prevent
    >
      <TaskCard
        :title="item.title"
        v-for="item in listOne"
        :key="item.title"
        draggable
        @dragstart="startDrag($event, item)"
      />
    </div>
    <div
      class="table__column"
      @drop="onDrop($event, 2)"
      @dragover.prevent
      @dragenter.prevent
    >
      <TaskCard
        :title="item.title"
        v-for="item in listTwo"
        :key="item.title"
        draggable
        @dragstart="startDrag($event, item)"
      />
    </div>
  </div>
</template>

<script>
import TaskCard from '@/components/TaskCard.vue'

export default {
  name: 'TaskTable',
  components: { TaskCard },
  data() {
    return {
      item: null,
      items: [
        {
          id: 0,
          title: 'Item A',
          list: 1,
        },
        {
          id: 1,
          title: 'Item B',
          list: 1,
        },
        {
          id: 2,
          title: 'Item C',
          list: 2,
        },
      ],
    }
  },
  computed: {
    listOne() {
      return this.items.filter((item) => item.list === 1)
    },
    listTwo() {
      return this.items.filter((item) => item.list === 2)
    },
  },
  methods: {
    startDrag(evt, item) {
      evt.dataTransfer.dropEffect = 'move'
      evt.dataTransfer.effectAllowed = 'move'
      evt.dataTransfer.setData('itemID', item.id)
    },
    onDrop(evt, list) {
      const itemID = evt.dataTransfer.getData('itemID')
      const item = this.items.find((item) => item.id == itemID)
      item.list = list
    },
  },
}
</script>

<style>
.table {
  width: 100%;
  height: 100vh;
  padding: 40px;
  display: flex;
  justify-content: space-between;
}

.table__column {
  border: 1px solid #666;
  height: 100%;
  flex: 1 0 200px;
  padding: 20px;
}

.table__column:not(:last-child) {
  margin-right: 10px;
}
</style>