<template>
  <form class="card-body " style="margin: 0 25%;">
    <div class="row mb-3">
      <label for="inputEmail" class="col-sm-2 col-form-label">Email</label>
      <div class="col-sm-10">
        <input 
            type="email" 
            class="form-control" 
            id="inputEmail" 
            placeholder="Email"
            v-model="login.email"
            />
      </div>
    </div>
    <div class="row mb-3">
      <label for="inputPassword" class="col-sm-2 col-form-label"
        >Password</label
      >
      <div class="col-sm-10">
        <input 
            type="password" 
            class="form-control" 
            id="inputPassword"
            placeholder="Password"
            v-model="login.password"
            />
      </div>
    </div>
    
    <div class="row mb-3">
      <div class="col-sm-10 offset-sm-2">
        <div class="form-check">
          <input class="form-check-input" type="checkbox" id="gridCheck1" />
          <label class="form-check-label" for="gridCheck1">
            Remember me
          </label>
        </div>
      </div>
    </div>
    <div class="d-flex justify-content-end">
        <button 
            type="submit" 
            class="btn btn-primary"
            @click.prevent="loginUser"
            >Sign in</button>
    </div>
    
    
  </form>
</template>

<script>
import swal from 'sweetalert';
export default {
    data(){
        return{
            login: {
                email: "",
                password: ""
            }
        }
    },
    methods:{
        async loginUser(){
            try {
                let response = await this.$http.post('/api/usuario/login', this.login);//api/auth/signin
                console.log(response.data);    
                let token = response.data.tokenReturn;
                let user = response.data.user;

                localStorage.setItem('jwt', token);
                localStorage.setItem('user', JSON.stringify(user));

                if(token){
                    swal("Acceso permitido", `Los datos de usuario son correctos, ¡Bienvenido ${user.nombre}!`, "success");
                    this.$router.push('/home');
                    
                }
            } catch (error) {
                console.log(error);
                swal("Acceso denegado", "Los datos de usuario son incorrectos", "error");
            }
            
        }
    }
};
</script>

<style scoped>

</style>
