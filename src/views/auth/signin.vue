<template>
  <div class="signin">
    <SignInForm/>
  </div>
</template>

<script>
import SignInForm from '@/components/layout/signin_form'
export default {
    components : {
        SignInForm,
    }
}
</script>

<style>
  .signin{
    min-height: 100vh;
  }
</style>