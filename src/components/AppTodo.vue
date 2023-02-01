<template>
  <div class="container">
    <div>
      <img src="https://images.pexels.com/photos/3243/pen-calendar-to-do-checklist.jpg" alt="tarefas" class="image-title rounded mx-auto d-block">
    </div>
    <form class="row form-todo">
      <div class="col">
        <input type="text" class="form-control input-todo" placeholder="Novo Todo" />
      </div>
      <div class="col">
        <button class="btn btn-outline-primary buttons">
          <i class="bi bi-plus-square"></i>
          Adicionar
        </button>
      </div>
    </form>
  </div>
</template>

<script>
export default {
  name: 'AppTodo',
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

.buttons {
  width: 150px;
}
</style>
