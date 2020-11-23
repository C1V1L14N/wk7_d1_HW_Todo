<template>

<div id="app">
  <h1>ToDo's</h1>
  <form v-on:submit.prevent="saveNewTask">

    <input id="new-task" type="text" v-model="newTask">
    <label for="priority-high">High</label>
    <input type="radio" name="priority" id="priority-high" value="true" v-model="todoPriority">
    <label for="priority-low">Low</label>
    <input type="radio" name="priority" id="priority-low" value="" v-model="todoPriority">
    <button id="submit-button" type="submit">Save Item</button>
  </form>

  <ul>
    <li class="list-items" v-for="(task, index) in tasks" v-bind:key="index"
    :class="task.priority ? 'high': 'low'">
    <span>{{task.name}}</span>
    </li>
  </ul>
</div>
  
</template>

<script>

export default {
  data(){
    return {
      tasks: [
        {name: 'Buy shopping', priority: false},
        {name: 'Clean bathroom', priority: false},
        {name: "Car's MOT", priority: false}
        ],
        newTask: ''
    }
  },
  methods: {
    saveNewTask: function(){
      this.tasks.push({
        name: this.newTask,
        priority: this.todoPriority       
      });
      this.newTask = '';
    },
    taskComplete: function(index){
      this.tasks[index].isComplete = true;
    }
  }
}
</script>

<style>

#app{
  display: flex;
  flex-direction: column;
  align-items: center;
}

form {
  display: flex;
  flex-direction: row;
  align-items: flex-start;
}

ul {
  margin: 0;
  padding: 0;
}

.list-items {
  max-width: 100%;
  width: 800px;
  padding: 5px;
  margin: 10px;
  font-size: 25px;
  border-style: solid;
  border-width: 3px;
  border-color: limegreen;
  list-style: none;
  text-size-adjust: 40px;
  display: flex;
  flex-direction: row;
  text-align: left;
}

#new-task{
  max-width: 600px;
}

#complete-button {
  white-space: normal;
  display: block;
  left: 130px;
  top: -19px;
  position: relative;
}

#complete-span {
  white-space: normal;
  display: block;
  left: 130px;
  top: -19px;
  position: relative;
}

.high {
  color: red;
  border-color: red;
}

.low {
  color: limegreen;
  border-color: limegreen;
}


</style>