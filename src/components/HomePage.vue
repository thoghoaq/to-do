<template>
  <h1>{{ title }}</h1>
  <h2>Add a new task</h2>
  <div>
    <input type="text" v-model="newTask" placeholder="Add a new task" v-on:blur="addTask" @keydown.enter="addTask">
  </div>
  <ul>
    <li class="flex items-center border rounded-lg p-4" v-for="task in tasks" :key="task.id">
      <input type="checkbox" class="form-checkbox h-5 w-5 text-blue-600" />
      <span class="text-sm font-medium text-gray-900">{{ task.name }}</span>
    </li>
  </ul>
</template>

<script>
export default {
  data() {
    return {
      title: 'To-do App',
      tasks: [],
      newTask: ""
    }
  },
  methods: {
    addTask() {
      if (this.newTask.length < 1) return
      this.tasks.push({
        id: this.tasks.length + 1,
        name: this.newTask,
        finished: false
      })
      this.newTask = ''
    }
  },
}
</script>

