<template>
  
  <div class="container">
    <h1>Formulario</h1>
    <form class="form-component" action>
      <div>
        <input v-model="name" class="input" type="text" placeholder="Nombre" @change=" $v.name.$touch()">
        <span class="error" v-if="$v.name.$error">Este campo es requerido</span>
      </div>
      
      <div>
        <input v-model="password" class="input" type="text" placeholder="Contraseña"  @change=" $v.password.$touch()">
        <span class="error" v-if="$v.password.$error">Este campo es requerido</span>
      </div>
      
      <div>
        <input v-model="email" class="input" type="text" placeholder="Email"  @change=" $v.email.$touch()">  
        <span class="error" v-if="$v.email.$error">Este campo es requerido</span>
      </div>
      <div>
       <div class="button-container">
          <button @click.prevent="submit" class="button" type="button"> Submit</button>
          <button @click.prevent="$v.$reset()" class="button" type="button"> Reset</button>
      </div> 
        <!-- <pre>{{$v.$invalid}}</pre> -->
      </div>  
    </form>
  </div>

</template>

<script>
import {required,email} from 'vuelidate/lib/validators';
export default {
  name: 'HelloWorld',
  data(){
    return{
      name:"",
      password:"",
      email:""
    }
  },

  validations:{
    name:{required},
    password:{required},
    email:{required,email}
  },

  methods:{

    submit(){
      if(!this.$v.$invalid){
        alert("Ingresando...")
        
      }else{
        this.$v.$touch();
      }


    }

  }

}
</script>


<style lang = "scss" scope>


.container{
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
  width: 100%;
  height: 100vh;
  background-color: #14A388;

  }

.form-component{
  display: flex;
  flex-direction: column;
  justify-content: center;
  background-color:#F03541;
  border-radius: 10px;
}




  .input{
    display: flex;
    flex-direction: column;
    width: 500px;
    height: 40px;
    margin: 1rem;
    border: 0px solid;
  }
.button-container{
  display: flex;
  flex-direction: column;
}


  .button{
    width: 500px;
    height: 40px;
    margin: 1rem;
    background-color:#14A388;
    border: 0px solid;
    
  }

  .button:hover{
    background-color:#197029;
  }


  .error{
    color: white;
  }

</style>