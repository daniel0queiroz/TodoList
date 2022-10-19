<template>
  <main>
    <h1>Lista de Tarefas</h1>
    <p>Lista de afazeres para o casamento</p>

    <div class="create-new">
      <input 
      type="text" 
      v-model="newTask" placeholder="Adicionar uma nova tarefa" 
      @keypress.enter="addTask" />
      <button @click="addTask">Add</button>
    </div>

    <div class="tasks">
      <Task
      v-for="(task, i) in $store.state.tasks" :key="i"
      :task="task" />
    </div>

  </main>
</template>

<script>
export default {
  data () {
    return {
      newTask: ''
    }
  },
  methods: {
    addTask () {
      if (this.newTask) {
        this.$store.commit('ADD_TASK', this.newTask);
        this.newTask = '';
      }
    }
  }
}
</script>
