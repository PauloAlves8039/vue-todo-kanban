<template>
  <div class="container">
    <div>
      <img src="https://images.pexels.com/photos/3243/pen-calendar-to-do-checklist.jpg" alt="tarefas" class="image-title rounded mx-auto d-block">
    </div>
    <form @submit.prevent="addTodo(todo)" class="row form-todo">
      <div class="col">
        <input 
          type="text" 
          v-model="todo.description"
          class="form-control input-todo" 
          placeholder="Novo Todo" 
        />
      </div>
      <div class="div-buttons col">
        <button class="btn btn-outline-primary buttons">
          Adicionar
        </button>
      </div>
      <div>
        {{ todos }}
      </div>
    </form>
  </div>
</template>

<script>
export default {
  name: 'AppTodo',
  data() {
    return {
      todos: [],
      todo: {
        checked: false
      }
    }
  },
  methods: {
    addTodo(todo) {
      todo.id = Date.now();
      this.todos.push(todo);
      this.clearFild();
    },
    clearFild() {
      this.todo = "";
    },
  }
}
</script>

<style scoped>
.image-title {
  width: 100px;  
  height: 100px;
  margin-bottom: 5px;
}

.form-todo {
  max-width: 600px;
  margin: 3% auto;
}

.input-todo {
  width: 400px;
}

.content-button {
  margin-right: 250px;
}

.div-buttons {
  margin-left: -3%;
}

.buttons {
  width: 150px;
}
</style>
