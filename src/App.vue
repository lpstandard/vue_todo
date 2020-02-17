<template>
  <div class="container" id="app">
    <h1 class="text-center">To Do App</h1>
    <form @submit.prevent="addToDo()">
  <div class="form-group">
    <label for="newToDo">New To Do</label>
    <input v-model="newToDo" type="text" class="form-control" id="exampleInputEmail1" aria-describedby="newToDolHelp" placeholder="Writing">
    <small id="newToDoHelp" class="form-text text-muted">Enter A New To Do.</small>
  </div>
  <button type="submit" class="btn btn-primary">Add To Do</button>
  <h3 ></h3>
  <ul class="list-group" mt-3>
    <li v-for="(todo, i) in ToDos" class="list-group-item">
      <button 
        @click="markDone(todo)"
        v-if="!todo.done"
        type="button" 
        class="btn btn-primary"
      >
        Done
      </button>
      <button 
      @click="removeTodo(i)" 
      class="btn btn-danger"
      >
      Delete
      </button>
      <span 
      :class="{
        isDone: todo.done
      }">
      {{todo.title}}
      </span>
    </li>
</ul>
</form>
  </div>
</template>

<script>
export default {
  name: "app",
  data() {
    return {
      newToDo: "",
      ToDos: []
    };
  },
  methods: {
    addToDo() {
      this.ToDos.push({
        title: this.newToDo,
        done: false
      });
      this.newToDo = "";
    },
    markDone(todo) {
      todo.done = true;
    },
    removeTodo(index) {
      // console.log(index);
      this.ToDos.splice(index, 1);
    }
  }
};
</script>

<style>
.isDone {
  text-decoration: line-through;
}
</style>
