<template>
    <div class="about">
        <h1>Nueva pagina</h1>
        <router-link to="/about">About</router-link>
    </div>
</template>

<script>
    export default{
        name:'NuevaView',
        props:[],
        emits:[],
        data(){
            return{
            }
        },
        methods: { 
            getUsuario(){
                this.axios.get("http://localhost:3000/usuario")
                .then((response)=>{console.log(response);})
                .catch((err)=>{console.log(err);})
            }
        },
        computed:{
        },
        mounted(){
            this.getUsuario();
        },
        components:{
        }
    }
</script>