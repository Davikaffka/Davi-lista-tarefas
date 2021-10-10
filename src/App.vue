<template>
  <div class="container">
    <h2>{{ titulo }}</h2>
    <div class="input-group">
      <input @keyup.enter="adicionartarefa" v-model="novaTarefa" type="text" />
      <span class="input-group-btn">
        <button @click="adicionartarefa" class="btn btn-primary"> 
        </button>
      </span>
    </div>
    <ul>
      <li
        v-for="(tarefa, index) in tarefas"
        :key="index"
        :class="{ removed: tarefa.checked }"
      >
        <input type="checkbox" v-model="tarefa.checked" />
        <label>{{ tarefa.titulo }}</label>
      </li>
    </ul>
    <footer>
      <em>Altere aqui seu título</em>
      <input v-model="titulo" type="text" />
    </footer>
  </div>
</template>

<script>
export default {
  name: "App",
  data() {
    return {
      titulo: "Minha lista de tarefas",
      novaTarefa: "",
      tarefas: [
        { titulo: "Estudar", checked: false },
        { titulo: "Programar", checked: true },
      ],
    };
  },
  methods: {
    adicionartarefa() {
      this.tarefas.push({
        titulo: this.novaTarefa,
        checked: false,
      });
      this.novaTarefa = "";
    },
  },
};
</script>

<style>
.container {
  width: 40%;
  margin: 20px auto 0px auto;
}
ul li {
  list-style: none;
}
.removed {
  color: black;
}
.removed label {
  text-decoration: line-through;
}
</style>
