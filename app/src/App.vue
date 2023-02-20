<template>
  <div class="container">
    <h2>
      {{ titulo }}
    </h2>
    <div class="inpu-group">
      <input @keyup.enter="adicionarTarefa"  type="text" v-model="novaTarefa">
      <span class="input-group-btn">
        <button @click="adicionarTarefa" class="btn btn-primary">
          Adicionar Tarefa
        </button>
      </span>
    </div>
    <ul>
      <li v-for="(tarefa, index) in tarefas" :key="index" :class="{'remover': tarefa.checked}">
        <input type="checkbox" v-model="tarefa.checked">
        <label>{{ tarefa.titulo }}</label>
      </li>
    </ul>

    <footer>
      <em>Altere aqui o titulo da sua lista de tarefa</em>
      <input type="text" v-model="titulo">
    </footer>
  </div>

</template>

<script>


export default {
  name: 'App',
  data(){
    return{
      titulo: 'Minha lista de tarefas',
      novaTarefa: '',
      tarefas:[{
        titulo: 'Estudar',
        checked: true
      },
      {
        titulo: 'Estudar',
        checked: false
      },
    ]
    }
    
  },
  methods:{
      adicionarTarefa(){
        this.tarefas.push({
          titulo: this.novaTarefa,
          checked: false,
        }),
        this.novaTarefa = ''
      }
    }
}
</script>

<style>
.containe{
  width: 40%;
  margin: 20px auto 0px auto;
}
.remover{
  color: gray;
  text-decoration: line-through;
}
ul li{
  list-style: none;
}
</style>
