<template>
    <div class="container">
      <header id="main-heading" class="fw-bold mt-3 py-4 px-5 bg-warning" style="text-align: center;">
        <div class="row">
          <div class="col-md-12">
            <h1 class="header-title">ToDo List</h1>
          </div>
        </div>
      </header>
      <div class="card mt-4">
        <div class="card-body">
          <div class="input-group mb-3 mt-3">
            <input
              v-model="newTask"
              type="text"
              class="form-control"
              placeholder="Add new task"
            >
            <button @click="addTask" class="btn btn-primary"><i class="fa-solid fa-plus"></i></button>
          </div>
          <div class="to-dos">
            <div v-for="(task, index) in tasks" :key="index" class="task alert alert-primary">
              <li :class="{ 'fs-5': true, 'completed': task.completed }" :style="{ 'text-decoration': task.completed ? 'line-through' : 'none' }">{{ task.text }}</li>
              <button @click="toggleTask(index)" class="checkTask btn btn-success movCh"><i class="fa-solid fa-check"></i></button>
              <button @click="deleteTask(index)" class="deleteTask btn btn-danger movedel"><i class="fa-solid fa-trash-can"></i></button>
            </div>
          </div>
        </div>
      </div>
    </div>
  </template>
  
  <script>
// import 'bootstrap/dist/css/bootstrap.css';
// import 'bootstrap/dist/js/bootstrap.bundle';
  export default {
    data() {
      return {
        newTask: '',
        tasks: [],
      };
    },
    methods: {
      addTask() {
        if (this.newTask.trim() === '') {
          alert('Please Enter a Task');
          return;
        }
  
        this.tasks.push({ text: this.newTask, completed: false });
        this.newTask = '';
      },
      toggleTask(index) {
        this.tasks[index].completed = !this.tasks[index].completed;
      },
      deleteTask(index) {
        if (confirm('Are you sure you want to remove this task?')) {
          this.tasks.splice(index, 1);
        }
      },
    },
  };
  </script>

  <style>
  
.task li {
    list-style: none;
    text-align: left;
}

.task {
    list-style: none;
    display: flex;
    justify-content: space-between;
    align-items: center;
}

.task li {
    flex: 1; /* Allow the list items to expand and occupy available space */
}

.movCh, .movedel {
    margin-left: 6px; /* Add space between buttons */
}
  </style>