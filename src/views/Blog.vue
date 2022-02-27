<template>
  <Titulo title="Este es el titulo de mi Blog !!!"/>
<div class="container">
  <ul v-for="article in listaArticulos" :key="article.id_article">
    <li style="list-style-type: none;  ">
      <router-link :to="`/blog/${article.id_article}`">{{ article.title_article }}</router-link>
    </li>    
  </ul>
</div>
</template>

<script>

import Titulo from '../components/Titulo.vue'

export default {
    components: {
        Titulo
    },
    data() {
      return {
        listaArticulos: []
      }
    },
    methods: {
      //Llamado a metodos de API Utilizando HTTP Fetch 
      //Se utiliza autenticacion por token JWT
      /*
      async obtenerArticulos(){
        try {
          const data = await fetch("http://localhost/api-rest/public/api/articulos", { 
            method: 'get', 
            headers: new Headers({
            'Authorization': 'bearer ' + 'eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJodHRwOlwvXC9sb2NhbGhvc3RcL2FwaS1yZXN0XC9wdWJsaWNcL2FwaVwvbG9naW4iLCJpYXQiOjE2NDU5Mzk5MTUsImV4cCI6MTY0NTk0MzUxNSwibmJmIjoxNjQ1OTM5OTE1LCJqdGkiOiJWZ1VNUzVGbmJXS09Razc4Iiwic3ViIjoxLCJwcnYiOiIyM2JkNWM4OTQ5ZjYwMGFkYjM5ZTcwMWM0MDA4NzJkYjdhNTk3NmY3In0.YGbhHg2O2kUZ1M_bPY82_G7KtS4NnEjldn7l4h1YT7U', 
            'Content-Type': 'application/json'
            })
          })
          const array = await data.json()
          console.log(array)
        }
        catch(error){
          console.log(error)
        }
      }
      */
     //Llamado a metodos de API utilizando AXIOS !!!
     //Ya se ha configurado la libreria en el archivo main.js
     async obtenerArticulos(){
        this.axios.get("http://localhost/api-rest/public/api/articulos", {
            headers: {
            'Authorization': 'Bearer' + 'eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJodHRwOlwvXC9sb2NhbGhvc3RcL2FwaS1yZXN0XC9wdWJsaWNcL2FwaVwvbG9naW4iLCJpYXQiOjE2NDU5NDM1NzksImV4cCI6MTY0NTk0NzE3OSwibmJmIjoxNjQ1OTQzNTc5LCJqdGkiOiJ2UWp6dVhGSThoR05hYnl0Iiwic3ViIjoxLCJwcnYiOiIyM2JkNWM4OTQ5ZjYwMGFkYjM5ZTcwMWM0MDA4NzJkYjdhNTk3NmY3In0.gBzAhInDTE6NFRNIB8dBjnWJHIxSONxGzs5JaOKBqog',
            "Content-Type": "application/json",
            }
        })
        .then(response => {
            this.listaArticulos = response.data.data
            console.log(response.data);
        })
          .catch(function (error) {
             console.log(error);
        });
      }
    },
    created(){
      this.obtenerArticulos();
    }
}
</script>

<style>

</style>