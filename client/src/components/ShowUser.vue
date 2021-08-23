<template>
  <div>
    <h1>รายละเอียดLabTop</h1>
    <p> {{ userId }}</p>
    <p>รุ่น {{ user.name }}</p>
    <p>สเปค {{ user.lastname }}</p>
    <p>ช่องทางการติดต่อ(email): {{ user.email }}</p>
    <p>ราคา: {{ user.password }}</p>
  </div>
</template>
<script>
import UserService from "@/services/UsersService";
export default {
  data() {
    return {
      user: null,
    };
  },
  async created() {
    try {
      let userId = this.$route.params.userId;
      this.user = (await UserService.show(userId)).data;
    } catch (error) {
      console.log(error);
    }
  },
};
</script>
<style scoped>
</style>