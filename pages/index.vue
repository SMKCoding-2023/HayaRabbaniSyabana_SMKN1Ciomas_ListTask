<template>
  <main>
    <h1>Ada Tugas apa hari ini?</h1>
    <p>Ayo Buat list tugas mu agar tidak telat mengumpulkan!</p>

    <div class="create-new">
      <input 
        type="text" 
        v-model="newTask" 
        placeholder="    Tambah list tugas mu!" 
        @keypress.enter="addTask" />
      <button @click="addTask">Tambah</button>
    </div>

    <div class="tasks">
      <Task
        v-for="(task, i) in $store.state.tasks"
        :key="i"
        :task="task" />
    </div>

  </main>
</template>

<script>
export default {
  data (){
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
