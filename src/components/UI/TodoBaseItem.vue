<template>
    <div>
        <slot></slot>
    </div>
</template>

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
