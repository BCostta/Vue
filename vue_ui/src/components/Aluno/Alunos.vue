<template>
  <div>
   <Titulo texto="Aluno"/>
    <input type="text" placeholder="Nome do aluno" v-model="nome" v-on:keyup.enter="addAluno()">
    <button class="btn btninput" v-on:click="addAluno()">Adicionar</button>
    <table border="1px solid black">
    <thead>
      <th>Mat.</th>
      <th>Nome</th>
      <th>Opções</th>
    </thead>
    <tbody v-if="alunos.length">
      <tr v-for="(aluno, index) in alunos" :key="index">
        <td>{{ index + 1 }}</td>
        <td>{{ aluno.nome }}</td>
        <td> <button class="btn" v-on:click=" remover(aluno)">Remover</button></td>
      </tr>
    </tbody>
    <tfoot v-if="!alunos.length">
        <h1>Nenhum aluno encontrado</h1>
      </tfoot>
  </table>

  </div>
</template>

<script>
import Titulo from '../_share/Titulo'
export default {

  components: {

    Titulo

  },

  data(){
    return{
      titulo: "Aluno",
      nome: '',
      alunos: []
    }
  },

  created(){
    this.$http
    .get('http://localhost:3000/alunos')
    .then(res => res.json())
    .then(alunos => this.alunos = alunos)
  },

  props: {   
  },
  methods: {
    addAluno() {
      let _aluno = {
        nome: this.nome,
        Sobrenome: ""
      }

    this.$http
    .post('http://localhost:3000/alunos', _aluno)
    .then(res => res.json())
    .then(aluno => {
      this.alunos.push(aluno);
      this.nome = '';
    })
    
    },
    remover(aluno){

     this.$http
    .delete(`http://localhost:3000/alunos/${aluno.id}`)
    .then(res => {      let indice = this.alunos.indexOf(aluno);
      this.alunos.splice(indice, 1)})

    }
  },
}
</script>
<style scoped>
input{
  
  border: 0;
  padding: 20px;
  font-size: 1.3em;
  color: #687f7f;
  display: inline;
}

.btninput{
  display: inline;
  border: 0;
  padding: 20px;
  font-size: 1.3em;
  background-color: rgb(116, 115, 115);
}

.btninput:hover{
  padding: 20px;
  margin: 0px;
  border: 0px;
}
</style>
