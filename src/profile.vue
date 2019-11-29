<template>
    <div>
        <p v-if="user && user.username.length>0"> Ви зайшли як {{user.username}} </p>
        <div v-else> 
        <p > Авторизуйтесь </p> 
            <form>
                <label> 
                    Login <input type="text" v-model="loginData.login">
                </label>
                <label> 
                    Password <input type="password" v-model="loginData.password">
                </label>
                <button type="button" v-on:click="LogIn(loginData.login, loginData.password)">
                    Log in
                </button>
            </form> 
        </div>
    </div>
</template>

<script>
export default {
    props:{
            userLink:Object,
            
        },
    data:function(){
        
        return{
            user:this.userLink,
            loginData:{
                login:"",
                password:""
            }
        }
    }, methods:{
        LogIn:function(login, password){
            console.log(this);
            this.user.username = login;
            
        }
    }
}
</script>

<style scoped>

</style>