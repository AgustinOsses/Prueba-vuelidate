<template>
  
  <div class="container">
    <form class="form-component" action>
    <h1>Formulario</h1>
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
        <span class="error" v-if="$v.email.$error">Email invalido</span>
      </div>
      <div>
       <div class="button-container">
          <button @click.prevent="submit" class="button" type="button"> Submit</button>
          <button @click.prevent="$v.$reset()" class="button" type="button" style="background-color:#F60055"> Reset</button>
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
  flex-direction: column;
  justify-content: center;
  width: 100%;
  height: 100vh;
  background-color: #181C34;
  }

.form-component{
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  width: 80vh;
  height: 100%;
  background-color:#F0F1E4;
}




.input{
  display: flex;
  flex-direction: column;
  width: 500px;
  height: 40px;
  margin: 1rem;
  border: none;
  border-radius: 5px;
  padding-left: 15px;
}
 


.button-container{
  display: flex;
  flex-direction: column;
}


.button{
  width: 500px;
  height: 40px;
  margin: 1rem;
  background-color:#181C34;
  color: white;
  border: none;
  border-radius: 5px;  
}

.button:hover{
  background-color:#09101d;
}


.error{
  color: #F60055;
}

</style>