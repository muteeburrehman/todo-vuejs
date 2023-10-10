<template>
   <div class="input-group mb-3 mt-3">
    <input
     :value="newTask"
      @input="updateParentNewTask"
      type="text"
      class="form-control"
      placeholder="Add new task"
    >
    <button @click="addTask" class="btn btn-primary"><i class="fa-solid fa-plus"></i></button>
  </div>
</template>

<script>
export default{
    props:{
    newTask:{
      type:String
    },
    addTask:{
      type:Function
    },
},
methods:{
    updateParentNewTask(event) {
      this.$emit('update:newTask', event.target.value);
    },
}
}
</script>