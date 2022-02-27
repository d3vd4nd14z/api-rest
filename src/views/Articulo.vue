<template>
    <div class="container">        
        <div class="row">
            <div class="col-md-12">
                <Titulo :title="articulo.title_article"/>
            </div>
            <hr/>
            <p class="text-justify">{{ articulo.content_article }}</p>
        </div>
        <div class="row">
            <div class="col-md-12">
            </div>
        </div>
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
            articulo: {}
        }
    },
    methods: {
        async obtenerArticulo(){
            await this.axios.get(`http://localhost/api-rest/public/api/articulos/${this.$route.params.id}`, {
                headers: {
                'Authorization': 'Bearer' + 'eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJodHRwOlwvXC9sb2NhbGhvc3RcL2FwaS1yZXN0XC9wdWJsaWNcL2FwaVwvbG9naW4iLCJpYXQiOjE2NDU5NDM1NzksImV4cCI6MTY0NTk0NzE3OSwibmJmIjoxNjQ1OTQzNTc5LCJqdGkiOiJ2UWp6dVhGSThoR05hYnl0Iiwic3ViIjoxLCJwcnYiOiIyM2JkNWM4OTQ5ZjYwMGFkYjM5ZTcwMWM0MDA4NzJkYjdhNTk3NmY3In0.gBzAhInDTE6NFRNIB8dBjnWJHIxSONxGzs5JaOKBqog',
                "Content-Type": "application/json",
                }
            })
            .then(response => {
                this.articulo = response.data
                console.log(response.data);
            })
            .catch(function (error) {
                console.log(error);
            });
        }
    },
    created (){
        this.obtenerArticulo();
    }
}
</script>

<style>

</style>