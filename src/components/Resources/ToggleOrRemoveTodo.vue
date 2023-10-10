<template>
   <div class="to-dos">
            <div v-for="(task, index) in tasks" :key="index" class="task alert alert-primary">
              <li :class="{ 'fs-5': true, 'completed': task.completed }" :style="{ 'text-decoration': task.completed ? 'line-through' : 'none' }">{{ task.text }}</li>
              <button @click="toggleTask(index)" class="checkTask btn btn-success movCh"><i class="fa-solid fa-check"></i></button>
              <button @click="deleteTask(index)" class="deleteTask btn btn-danger movedel"><i class="fa-solid fa-trash-can"></i></button>
            </div>
          </div>
</template>

<script>
export default {
  props:{
    tasks:{
      type:Array
    },
    toggleTask:{
      type:Function
    },
    deleteTask: {
      type: Function
    }
  }
  
}
</script>