<template>
  <header>
    <b-navbar>
      <template slot="brand">
        <b-navbar-item class="is-3by3" tag="router-link" :to="{ path: '/' }">
        </b-navbar-item> 
      </template>
 
      <template slot="start">
        <div class="search-bar navbar-item  ">
          <SearchAutoComplete />
        </div>
      </template>

      
      

      <template slot="end" v-if="!isLogged">
        <b-navbar-item
          v-for="authbutton in auth"
          :key="authbutton.title"
          tag="router-link"
          :to="{name:authbutton.link}"
        >
          <strong :class="authbutton.class">{{authbutton.title}}</strong>
        </b-navbar-item>
      </template>
      <template slot="end" v-else>
          <UserAvatar/>
      </template>
    </b-navbar>
  </header>
</template>

<script>
          // <img src="../../assets/imgs/" alt="logo del instituto" />
import UserAvatar from './user_avatar_menu'
import SearchAutoComplete from "@/components/presentation/searchAutoComplete";
export default {
  name: "MainNavbar",
  data() {
    return {
      auth: [
        {
          link: "signin",
          title: "Ingresar",
          class: "button is-primary is-outlined"
        },
        {
          link: "signup",
          title: "Registrarse",
          class: "button is-primary"
        },
      ],
      categoryDropDown: []
    };
  },
  computed: {
    isLogged() {
      return this.$store.getters.isLogged;
    }
  },
  created() {}
  ,components : {
  UserAvatar,
  SearchAutoComplete,
}
};
</script>

<style >
    .navbar-start{
      margin-right:0;
      flex-grow:1;
    }
    .navbar-end{
      margin-left:0 !important
    }
    .search-bar{
      width:100%
      
    }
</style>