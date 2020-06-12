<template>
  <div>
    <h2>Login</h2>

    <form>
    <div class="form-login">
        <label for="Email" class="form-label-email">Email</label>
        <input type="email" class="form-control" id="inputEmail" placeholder="Email"> 
  
        <label for="Password" class="form-label-password">Password</label>
        <input type="password" class="form-control" id="inputPassword" placeholder="Password">
        
        <button type="submit" class="btn btn-primary">Sign in</button>
  </div>

</form>
  </div>
</template>

<script>

export default {
    
    data(){
        return{
        email:'',
        password:'',
        }
        
    },
}
</script>