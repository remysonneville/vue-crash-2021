<template>
  <div class="container">
    <Header @toggle-add-task="toggleAddTask" title="Suivi des taches" />
    <div v-if="showAddtask">
      <AddTask @add-task="addTask" />
    </div>
    <Tasks @toggle-reminder="toggleReminder" @delete-task="deleteTask" :tasks="tasks"/>
  </div>
</template>

<script>
import Header from '@/components/Header'
// eslint-disable-next-line import/no-duplicates
import Tasks from '@/components/Tasks'
import AddTask from '@/components/AddTask'
// eslint-disable-next-line import/no-duplicates
import tasks from '@/components/Tasks'

export default {
  name: 'App',
  components: {
    Header,
    // eslint-disable-next-line vue/no-unused-components
    Tasks,
    // eslint-disable-next-line vue/no-unused-components
    AddTask
  },
  data () {
    return {
      tasks: [],
      showAddtask: false
    }
  },
  methods: {
    toggleAddTask () {
      this.showAddtask = !this.showAddtask
    },
    addTask (task) {
      this.tasks = [...this.tasks, task]
    },
    deleteTask (id) {
      this.tasks = this.tasks.filter((task) => task.id !== id)
    },
    toggleReminder (id) {
      this.tasks = this.tasks.map((task) => task.id === id ? { ...task, reminder: !task.reminder } : task)
    }
  }
}
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Poppins:wght@300;400&display=swap');

* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

body {
  font-family: 'Poppins', sans-serif;
}

.container {
  max-width: 500px;
  margin: 30px auto;
  overflow: auto;
  min-height: 300px;
  border: 1px solid steelblue;
  padding: 30px;
  border-radius: 5px;
}

.button {
  display: inline-block;
  background: #000;
  color: #fff;
  border: none;
  padding: 10px 20px;
  margin: 5px;
  border-radius: 5px;
  cursor: pointer;
  text-decoration: none;
  font-size: 15px;
  font-family: inherit;
}

.btn:focus {
  outline: none;
}

.btn:active {
  transform: scale(0.98);
}

.btn-block {
  display: block;
  width: 100%;
}
</style>
