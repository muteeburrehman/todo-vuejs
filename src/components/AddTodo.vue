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
          
          <add-todo :add-task="addTask"   @update:newTask="updateNewTask">

          </add-todo>

          <todo-base-item>
            <toggle-or-remove-todo :toggle-task="toggleTask" :delete-task="deleteTask" :tasks="tasks"></toggle-or-remove-todo>
        
        </todo-base-item>
        </div>
      </div>
    </div>
  </template>
  
  <script>

import TodoBaseItem from './UI/TodoBaseItem.vue'
import AddTodo from './Resources/AddTodo.vue'

import ToggleOrRemoveTodo from './Resources/ToggleOrRemoveTodo.vue';

  export default {
  components: { TodoBaseItem, ToggleOrRemoveTodo,AddTodo },
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
      updateNewTask(newTask) {
      this.newTask = newTask;
    },
    },
  };
  </script>

