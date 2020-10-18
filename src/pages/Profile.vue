<template>
  <div>
    <h1>Welcome, {{ user.username }}</h1>
  </div>
</template>
<script>
export default {
  name: "Profile",
  components: {},
  data() {
    let userPlaceholder = {
      username: "bar"
    };
    return {
      user: userPlaceholder,
      signedIn: false
    };
  },
  beforeCreate() {
    this.$Auth
      .currentAuthenticatedUser()
      .then(user => {
        console.log("User: ", user);
        this.user = user;
        this.signedIn = true;
      })
      .catch(() => console.log("not signed in..."));
  }
};
</script>
<style></style>
