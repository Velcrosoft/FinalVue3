<template>
    <div class="about">
        <h1>Nueva pagina</h1>
        <router-link to="/about">About</router-link>

        <!--bootstrap ejemplo-->
        <div class="card" style="width: 18rem;">
        <div class="card-body">
            <h5 class="card-title">Card title</h5>
            <p class="card-text">Some quick example text to build on the card title and make up the bulk of the card's content.</p>
            <a href="#" class="btn btn-primary">Go somewhere</a>
        </div>
        </div>

    </div>
</template>

<script>
    export default{
        name:'UsuarioView',
        props:[],
        emits:[],
        data(){
            return{
            }
        },
        methods: { 
            getUsuarios(){
                this.axios.get("http://localhost:3000/usuario")
                .then((response)=>{console.log(response);})
                .catch((err)=>{console.log(err);})
            }
        },
        computed:{
        },
        mounted(){
            this.getUsuarios();
        },
        components:{
        }
    }
</script>