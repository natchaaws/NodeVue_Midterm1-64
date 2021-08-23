<template>
  <div>
    <h1>Show User</h1>
    <p>id: {{ userId }}</p>
    <p>ยี่ห้อ :{{ user.name }} - {{ user.lastname }}</p>
    <p>รุ่น: {{ user.email }}</p>
    <p>ขนาด: {{ user.password }}</p>
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