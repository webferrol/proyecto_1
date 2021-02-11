<template>
  <div id="nav">
    <CustomerButton href="http://www.webferrol.com" message="Webferrol" :callback="detenerEnlace"/>
    <CustomerButton :callback="goHome">Home</CustomerButton>
    <CustomerButton :callback="saludo">Hola</CustomerButton>
    
    <router-link to="/">Home</router-link> |
    <router-link to="/about">About</router-link>
    <input type="text" v-model="info">{{info}}
     <router-view/>
  </div>
</template>

<script>
import CustomerButton from "@/components/CustomerButton.vue"
export default {
    data(){
      return {
        info: 'd'
      }
    },
    components:{
        CustomerButton
    },
    methods:{
        goAbout(){
           this.$router.push('/about');
        },
         goHome(){
           this.$router.push('/');
        },
        saludo(){
          alert(`Hola ${this.info}`)
        },
        detenerEnlace(e){
          e.preventDefault();
        }
    }
  
}
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

#nav {
  padding: 30px;

  
}
a {
    font-weight: bold;
    color: #2c3e50;

    &.router-link-exact-active {
      color: #42b983;
    }
  }
</style>
