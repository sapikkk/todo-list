<template>
  <div id="app">
    <h1>To-do list app - Muhammad Syafiq</h1>
    <div class="input-container">
      <input type="text" v-model="newTask" placeholder="Input data..." />
      <button @click="addTask">+</button>
    </div>
    <ul>
      <li v-for="(task, index) in filteredTasks" :key="index">
        <div class="task-container">
          <span :class="{ 'completed': task.completed }">{{ task.name }}</span>
          <div class="button-container">
            <button @click="toggleTask(index)">
              {{ task.completed ? 'Batal' : 'Selesai' }}
            </button>
            <button @click="removeTask(index)">Hapus</button>
          </div>
        </div>
      </li>
    </ul>
    <button class="toggle-filter" @click="showOnlyCompleted = !showOnlyCompleted">
      {{ showOnlyCompleted ? 'Show Not Completed' : 'Show Completed' }}
    </button>
  </div>
</template>

<script>
export default {
  data() {
    return {
      newTask: '',
      tasks: [],
      showOnlyCompleted: false
    };
  },
  methods: {
    addTask() {
      if (this.newTask !== '') {
        this.tasks.push({ name: this.newTask, completed: false });
        this.newTask = '';
      }
    },
    removeTask(index) {
      this.tasks.splice(index, 1);
    },
    toggleTask(index) {
      this.tasks[index].completed = !this.tasks[index].completed;
    }
  },
  computed: {
    filteredTasks() {
      if (this.showOnlyCompleted) {
        return this.tasks.filter(task => task.completed);
      } else {
        return this.tasks;
      }
    }
  }
};
</script>

<style scoped>
#app {
background-color: #1e1e2f;
color: #f5f5f5;
margin: auto;
padding: 30px;
max-width: 600px;
min-height: 100vh;
border-radius: 12px;
box-shadow: 0 0 25px rgba(0, 0, 0, 0.4);
display: flex;
flex-direction: column;
gap: 20px;
}

#app h1 {
font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
text-align: center;
color: #00ffaa;
margin-bottom: 10px;
}

.input-container {
display: flex;
justify-content: center;
gap: 10px;
}

input[type="text"] {
padding: 10px 15px;
border-radius: 8px;
border: 1px solid #444;
background-color: #2d2d3a;
color: white;
width: 70%;
}

.input-container button {
padding: 10px 15px;
background-color: #00ffaa;
border: none;
border-radius: 8px;
color: #1e1e2f;
font-weight: bold;
cursor: pointer;
transition: 0.2s;
}

.input-container button:hover {
background-color: #00ddaa;
}

ul {
list-style-type: none;
padding: 0;
display: flex;
flex-direction: column;
gap: 10px;
}

li {
background-color: #2d2d3a;
padding: 12px 16px;
border-radius: 10px;
display: flex;
align-items: center;
justify-content: space-between;
}

.task-container {
display: flex;
justify-content: space-between;
align-items: center;
width: 100%;
gap: 10px;
}

.completed {
text-decoration: line-through;
color: #888;
}

.button-container {
display: flex;
gap: 10px;
}

.button-container button {
padding: 8px 12px;
background-color: #00ffaa;
border: none;
border-radius: 6px;
color: #1e1e2f;
font-weight: bold;
cursor: pointer;
}

.button-container button:hover {
background-color: #00ddaa;
}

.toggle-filter {
align-self: center;
padding: 10px 20px;
background-color: #00ffaa;
border: none;
border-radius: 8px;
font-weight: bold;
color: #1e1e2f;
cursor: pointer;
transition: 0.2s;
}

.toggle-filter:hover {
background-color: #00ddaa;
}

</style>
