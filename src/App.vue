<template>
  <TheHeader v-show="showHeader" />
  <HelloWorld msg="Welcome to Your Vue.js App"/>

  <div>

    <h1 :class="{'title': true, 'title-home': isHome }">
       Curso Vue 3
    </h1>

    <h2 :class="nameUser" v-show="showFirstName">
      Nome do usuário: {{ user.name }}
    </h2>
    <h2 :class="['online', {title: true, 'title-home': isHome}]" v-if="showYear < 19">
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
    <div :key="obj.id" v-for="(obj, index) in todos">
      {{ index }} - {{ obj.text }} - {{ obj.done }}

      <img v-if="obj.imgSrc" id="user-avatar" :src="obj.imgSrc">

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
      isHome  : true,
      nameUser: 'online',
      classTitle: 'title',
      showHeader: true,
      showFirstName: true,
      showYear: false,
      typeUser: 'nothing',

      user: {
        name: 'John Doe',
        years: 10,
        imgSrc: 'https://www.w3schools.com/howto/img_avatar.png',
      },
      todos: [
        {
          id: 1,
          text: 'Learn Vue.js',
          done: true,
          imgSrc: 'https://www.w3schools.com/howto/img_avatar.png',
        },
        {
          id: 2,
          text: 'Learn Vuex',
          done: false,
          imgSrc: 'https://www.w3schools.com/howto/img_avatar.png',
        },
        {
          id: 3,
          text: 'Learn Vue Router',
          done: false
        },
        {
          id: 4,
          text: 'Learn Vuex',
          done: true,
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

#user-avatar{
  width: 4rem;
  height: 4rem;
  border-radius: 50%;
}

.todos{
  margin: 0 auto;
  width: 100%;
  padding: 10px;
  background: #f1f1f1;
  text-align: left;
}

.title{
  font-size: 2rem;
  font-weight: bold;
  color: #42b983;
}

.title-home{
  font-size: 2.5rem;
  font-weight: bold;
  color: red;
  margin-top: 0;
}

.online{
  text-transform: uppercase;
  font-size: 1.5rem;
  text-shadow: #2c3e50 1px 1px 1px;
}
</style>
