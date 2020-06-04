<template>
  <div id="app" class="wrapper">
    <h1>Задачи</h1>
    <TaskList 
      :tasks="tasks"
      @delete="deleteTask"
    />
    <AddTask @add-task="addTask" />
  </div>
</template>

<script>
import TaskList from './components/TaskList.vue'
import AddTask from './components/AddTask.vue'

export default {
  name: 'App',
  data() {
    return {
      tasks: []
    }
  },
  mounted() {
    
    if(localStorage.getItem('tasks')) {
      try {
        this.tasks = JSON.parse(localStorage.getItem('tasks'))
      } catch(e) {
        localStorage.removeItem('tasks')
      }
    }
  },
  components: {
    TaskList,
    AddTask
  },
  methods: {
    addTask(addTask) {
      this.tasks.push(addTask)
      this.saveCats()
    },
    deleteTask(index){
      this.tasks.splice(index, 1)
      this.saveCats()
    },
    saveCats() {
      let parsed = JSON.stringify(this.tasks);
      localStorage.setItem('tasks', parsed);
    }
  },
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  margin-top: 60px;
}

.wrapper {
    max-width: 640px;
    margin: 0 auto;
    box-shadow: 0 3px 6px rgba(0,0,0,0.16), 0 3px 6px rgba(0,0,0,0.23);
    padding: 40px;
}

button.btn {
    border: 2px solid #000;
    background: #fff;
    height: 35px;
    transition: background .45s, color .45s;
    cursor: pointer;
}

button.btn:hover {
  background: #000;
  color: #fff;
}
</style>
