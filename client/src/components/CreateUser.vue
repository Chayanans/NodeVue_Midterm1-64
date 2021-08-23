<template>
<div>
    <h1>สร้างการขายLabtop</h1>
    <form v-on:submit.prevent = "createUser">
        <p>ชื่อรุ่น: <input type="text" v-model="user.name"></p>
        <p>สเปค: <input type="text" v-model="user.lastname"></p>
        <p>ช่องทางติดต่อ(email): <input type="text" v-model="user.email"></p>
        <p>ราคา: <input type="text" v-model="user.password"></p>
        <p><button type="submit">สร้างการขาย</button></p>
    </form>
    <hr>
    <div>
        <p>ชื่อรุ่น: {{user.name}}</p>
        <p>สเปค: {{user.lastname}}</p>
        <p>ช่องทางติดต่อ(email): {{user.email}}</p>
        <p>ราคา: {{user.password}}</p>
    </div>
</div>
</template>
<script>
import UsersService from '@/services/UsersService'

export default {
    data(){
        return{
            user:{
                name: '',
                lastname: '',
                email: '',
                password: '',
                status: 'active'
            }
        }
    },
    methods:{
        async createUser(){
            try{
                await UsersService.post(this.user)
                this.$router.push({
                    name: 'users'
                })
            }catch(error){
                console.log(error)
            }
        }
    }    
}
</script>
<style scoped>


</style>