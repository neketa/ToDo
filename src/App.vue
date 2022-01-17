<template>
  <div class="body">
    <div class="main">
      <div class="header">
        <input
          v-bind:value="body"
          @input="inputValue"
          class="input"
          type="text"
        />
        <button class="add-todo-btn" v-on:keyup.enter="addTodo" @click="addTodo">
          <i class="fas fa-plus"></i>
        </button>
      </div>
      <ul class="todo-list" v-for="(todo, index) in todos" :key="todo.id">
        <li class="todo-item">
          <div class="delete-task-btn" @click="deleteTodo(index)">🗸</div>
          {{ todo.body }}
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
        todos: [
            {id: 1, body: "I will"},
            {id: 2, body: "I will do"},
            {id: 3, body: "I will nothing"},
            {id: 4, body: "I will"},
            {id: 5, body: "I will do"},
            {id: 6, body: "I will nothing"}
        ],

        body: ''
    };
  },
  methods: {
      inputValue(event) {
          this.body = event.target.value;
      },

      deleteTodo(index) {
          this.todos.splice(index, 1)
      },

      addTodo() {
          const newTodo = {
            id:  Date.now(),
            body: this.body
          }
        if (this.body != '') {
        this.todos.push(newTodo);
        this.body = "";
        }
      }


  }
};
</script>

<style>
* {
  margin: 0;
  padding: 0;
}

html {
  height: 100%;
}

.body {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
}

.main {
  height: 600px;
  width: 1000px;
}

.header {
  display: flex;
  justify-content: space-between;
}

.input {
  width: 800px;
  height: 50px;
  border: 2px solid #000000;
  font-size: 30px;
  padding: 10px 0;
}

.add-todo-btn {
  display: flex;
  height: 70px;
  border: 2px solid #000000;
  width: 70px;
  margin-left: 20px;
  font-size: 30px;
  justify-content: center;
  align-items: center;
  background-color: #000000;
  color: #fff;
}

.add-todo-btn:hover {
  cursor: pointer;
}

.todo-list {
  list-style-type: none;
  font-size: 25px;
}

.todo-item {
  margin: 15px 0;
  display: flex;
}

.delete-task-btn {
  display: block;
  height: 50px;
  width: 50px;
  margin-right: 10px;
  font-size: 30px;
}

.delete-task-btn:hover {
    cursor: pointer;
  }
</style>

