<template>
    <div class="w-full flex items-center justify-center bg-teal-lightest font-sans">
      <div class="bg-gray-800 rounded shadow p-6 m-4 w-full lg:w-3/4 lg:max-w-full bg-opacity-20 ">
            <div class="mb-4">
                <h1 class="text-white font-bold text-3xl">Todo List</h1>
                <div class="flex mt-4">
                    <input v-model="newTask" v-on:blur="addTask" @keydown.enter="addTask" class="shadow appearance-none border bg-transparent rounded w-full py-2 px-3 mr-4 text-white" placeholder="Add Todo">
                    <button v-on:click="addTask" class="flex-no-shrink border-green-600 text-green-600 p-2 border-2 rounded text-teal border-teal hover:text-white hover:bg-green-600 w-20">Add</button>
                </div>
            </div>
            <div>
                <div class="flex mb-4 items-center" v-for="task in tasks" :key="task.id">
                    <p class="w-full text-white" :class="[task.finished ? 'line-through' : '']">{{ task.name }}</p>
                    <button v-if="!task.finished" v-on:click="() => {
                      task.finished = true
                    }" class="flex-no-shrink p-2 ml-4 mr-2 border-green-600 text-green-600  border-2 rounded hover:text-white text-green border-green hover:bg-green-600 lg:w-40">Done</button>
                    <button v-else v-on:click="() => {
                      task.finished = false
                    }" class="flex-no-shrink p-2 ml-4 mr-2 border-2 text-gray-600 border-gray-600 rounded hover:text-white text-grey border-grey hover:bg-gray-600 lg:w-40">Not Done</button>
                    <button v-on:click="() => {
                      tasks.pop(task)
                    }" class="flex-no-shrink p-2 ml-2 border-2 rounded text-red-600 border-red-600 hover:text-white hover:bg-red-600">Remove</button>
                </div>
            </div>
        </div>
        
  </div>
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

