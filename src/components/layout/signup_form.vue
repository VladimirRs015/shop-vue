<template>
  <section>
      <h1 class="title is-2 has-text-centered"> Registrarse</h1>
    <div class="columns">
      <div class="column is-4 is-offset-4">
        <b-field label="Nombre">
          <b-input v-model="form.name"></b-input>
        </b-field>
        <b-field label="E-mail" type="is-sucess">
          <b-input type="email" v-model="form.email" maxlength="30"></b-input>
        </b-field>

        <b-field label="Nombre de usuario" >
          <b-input v-model="form.username" maxlength="30"></b-input>
        </b-field>

        <b-field label="Password">
          <b-input type="password" v-model="form.password" ></b-input>
        </b-field>
        <b-field label="Confirma el password">
          <b-input type="password" v-model="confirmPassword" password-reveal></b-input>
        </b-field>
        <b-field > 
          <div class="control">
            <b-button class="form-submit-button" tag="input"
                @click="toRegister"
                native-type="submit"
                type="is-primary"
                value="Enviar"  />
          </div>
        </b-field>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  data() {
    return {
      form :{
        name :null,
        email :null,
        password :null,
      },
      confirmPassword:""
    };
  },
  methods: {
    toRegister(){
      if(this.form.password === this.confirmPassword){
        alert('all right')
      }
    }
  },
};
</script>
<style lang="scss" scoped>
    .form-submit-button{
        width: 100%;
    }
</style>