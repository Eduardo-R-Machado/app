<template>
  <TheHeader v-show="showHeader" />
  <HelloWorld msg="Welcome to Your Vue.js App"/>

  <div>
    <h2 v-show="showFirstName">
      Nome do usuário: {{ user.name }}
    </h2>
    <h2 v-if="showYear < 19">
      idade do usuário: {{ user.years }}
    </h2>
  </div>

  <section class="type">
    <h3 v-if="typeUser === 'admin'"> Admin</h3>
    <h3 v-else-if="typeUser === 'user'"> User</h3>
    <h3 v-else-if="typeUser === 'Developer'">Desenvolvedor</h3>
    <h3 v-else>Não definido</h3>
  </section>


  <section class="todos">
    <div v-bind:key="obj.id" v-for="(obj, index) in todos">
      {{ index }} - {{ obj.text }} - {{ obj.done }}

    </div>
  </section>


</template>







<script>
import HelloWorld from './components/HelloWorld.vue'
import TheHeader from './components/TheHeader.vue'


export default {
  name: 'App',
  components: {
    HelloWorld,
    TheHeader
  },
  data() {
    return {
      showHeader: true,
      showFirstName: true,
      showYear: false,
      typeUser: 'nothing',
      user: {
        name: 'John Doe',
        years: 10
      },
      todos: [
        {
          id: 1,
          text: 'Learn Vue.js',
          done: true
        },
        {
          id: 2,
          text: 'Learn Vuex',
          done: false
        },
        {
          id: 3,
          text: 'Learn Vue Router',
          done: false
        }
      ]
    }
  }
}
</script>




<style>
body{
  margin: 0;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
  margin: 0 auto;
  padding: 0;
}

.todos{
  margin: 0 auto;
  width: 100%;
  padding: 10px;
  background: #f1f1f1;
  text-align: left;
}
</style>
