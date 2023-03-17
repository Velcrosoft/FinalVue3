<template>
    <div class="container">
        <div class="row">
            <div class="col-md-6">
                <div style="text-align: left;">
                    Lista de Usuarios<br>
                    <form class="form" @submit.prevent="crearPersona()">
                        <div class="form-group">
                            <label for="">Nombre</label>

                            <input type="text" v-model="payload.nombre" class="form-control">
                        </div>
                        <div class="form-group">
                            <label for="">Usuario</label>
                            <input type="text" v-model="payload.usuario" class="form-control">
                        </div>
                        <div class="form-group">
                            <label for="">Password</label>
                            <input type="text" v-model="payload.password" class="form-control">
                        </div>
                        <div class="form-group">
                            <button type="submit" class="btn btn-primary">Enviar</button>
                        </div>
                    </form>
                    
                    <table class="table">
                        <thead>
                            <tr>
                            <th scope="col">#</th>
                            <th scope="col">Nombre</th>
                            <th scope="col">Usuario</th>
                            <th scope="col">Password</th>
                            </tr>
                        </thead>
                        <tbody>
                            <tr v-for="{value, key} of usuario" id=key>
                            <th scope="row">{{ value.id }}</th>
                            <td>{{ value.nombre }}</td>
                            <td>{{ value.usuario }}</td>
                            <td>{{ value.password }}</td>
                            <td><button class="btn btn-primary">Editar</button></td>
                            </tr>
                        </tbody>
                    </table>
                </div>
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
                usuario:[],
                payload:{
                    nombre: "",
                    usuario: "",
                    password: ""
                }
            }
        },
        methods: { 
            getUsuarios(){
                this.axios.get("http://localhost:3000/usuario")
                .then((response)=>{this.usuario = response.data})
                .catch((err)=>{console.log(err);})
            },
            crearPersona(){
                this.axios.post("http://localhost:3000/usuario", this.payload)
                .then((response)=>{this.getUsuarios()})
                .catch((err)=>{console.log(err);})
                console.log(this.payload);
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