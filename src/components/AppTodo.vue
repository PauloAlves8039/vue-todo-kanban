<template>
  <div class="container">
    <div>
      <img src="../assets/images/todo1.jpg" alt="tarefas" class="image-title rounded mx-auto d-block">
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
      <div class="col div-buttons">
        <button class="btn btn-outline-primary buttons">
          Adicionar
        </button>
      </div>
    </form>
    <div class="todo-list">
      <div v-for="todoList in todos" :key="todoList.id" @toggle="toggleTodo">
        <div class="card border-info mb-2" style="max-width: 40rem;">
          <div class="title-card card-header text-center" :class="{Checked: todo.checked}">
            <i
              :class="todo.checked ? 'bi-check-circle' : 'bi bi-alarm'" 
            ></i>
          </div>
          <div class="card-body">
            <p class="card-text">
              {{ todoList.description }}
            </p>
            <div class="text-end">
              <button @click="$emit('toggle', todo)" class="btn btn-outline-success">
                <span v-if="todo.checked">Desmarcar</span>
                <span v-else>Concluido</span>
              </button>
              <button class="btn btn-outline-danger m-2">Remover</button>
            </div>
          </div>
        </div>
      </div>
    </div>
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
      this.todo = {checked: false};
    },
    toggleTodo(todo) {
      const index = this.todos.findIndex(item => item.id === todo.id);
      if (index > -1) {
        const checked = !this.todos[index].checked;
        this.$set(this.todos, index, {...this.todos[index], checked});
      }
    }
  }
}
</script>

<style scoped>
.container {
  max-width: 700px;
}

.image-title {
  width: 100px;  
  height: 100px;
  margin-bottom: 5px;
}

.form-todo {
  max-width: 700px;
  margin: 3% auto;
}

.input-todo {
  width: 454px;
}

.content-button {
  margin-right: 200px;
}

.buttons {
  width: 150px;
}

.todo-list {
  margin-left: 10px;
}

.Checked {
  text-decoration: line-through;
  color: #E9E2E2;
}
</style>
