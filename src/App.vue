<template>
  <div class="w-[600px] mx-auto mt-6">
    <h1 class="text-4xl font-bold mb-4">Todo list <span class="text-gray-300 text-lg">({{allTask}})</span></h1>
    <form class="flex">
      <input v-model="newTask" class="px-4 py-2 border w-full outline-none" type="text" placeholder="Enter the task">
      <button @click.prevent="addTask()" class="bg-black text-white px-4 py-2">Add</button>
    </form>
    <ul class="mt-6 space-y-3">
      <li v-for:="(task, index) in tasks" class="flex justify-between items-center border">
        <button @click="completedTask(task)" :class="task.completed ? 'bg-green-300 line-through' : ''" class="w-full px-4 py-2 bg-gray-100 flex justify-start">{{ task.title }}</button>
        <button @click="removeTask(index)" class="bg-red-500 text-white px-4 py-2">Delete</button>
      </li>
    </ul>
  </div>
</template>

<script>

export default {
  name: 'App',
  data() {
    return {
      newTask: '',
      tasks: [
        {
          title: "Learn Javascript",
          completed: false
        }
      ]
    }
  },
  methods: {
    addTask() {
      this.tasks.push({
        title: this.newTask,
        completed: false
      })
      this.newTask = ''
    },
    completedTask(task) {
      task.completed = !task.completed
    },
    removeTask(index) {
      this.tasks.splice(index, 1);
    }
  },
  computed: {
    allTask() {
      return this.tasks.length;
    }
  }
}
</script>

<style>

</style>
