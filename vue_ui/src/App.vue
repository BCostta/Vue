<template>
  <div id="app">
  <Alunos/>
  </div>
</template>

<script>
import Alunos from './components/Aluno/Alunos.vue'

export default {
  name: 'app',
  components: {
    Alunos
  }
}
</script>

<style>
@import url("https://fonts.googleapis.com/css?family=Montserrat:400,700");

body{
  background-color: #eee;
  font-family: "Montserrat", sans-serif;
  display: grid;
  justify-items: center;
}
body, html {
  margin: 0;
  height: 100%;
}
#app {

}

table {
  margin: 0px;
  padding: 0px;
  list-style-type: none;
  width: 100%;
}
table tr td{
  padding: 20px;
  font-size: 1.3em;
  background-color: #e0edf4;
  margin-bottom: 2px;
  color: #3e5252;
}
table thead th{
  background-color: rgb(184, 208, 216) !important;
  font-size: 1.2em;
  padding: 10px 0px;
  text-align: center !important;
}
.colPequeno {
  width: 5%;
}

.btn{
  background-color: red;
  padding: 10px 20px;
  border: 1px solid #000;
  cursor: pointer;
  color: white;
  font-weight: bold;
  border-radius: 5px;
  border-bottom: 3px solid #000;
 }

 .btn:hover{
  text-shadow: 1px 1px 1px #000;
  margin-top: 3px;
  border-bottom: 1px;
 }
#app {

}
</style>
