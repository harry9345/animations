<template>
  <section>
    <transition-group tag="ul" name="user-list">
      <li v-for="user in users" :key="user" @click="removeUser(user)">{{ user }}</li>
    </transition-group>

    <input type="text" ref="userNameInput" />
    <button @click="addUser">Add user</button>
  </section>
</template>

<script>
export default {
  data() {
    return {
      users: ['max', 'manul', 'harry', 'mona', 'sasan']
    };
  },
  methods: {
    addUser() {
      const enteUserName = this.$refs.userNameInput.value;
      this.users.unshift(enteUserName);
    },
    removeUser(user) {
      this.users = this.users.filter(usr => usr !== user);
    }
  }
};
</script>

<style  scoped>
ul {
  list-style: none;
  padding: 0;
  margin: 1rem 0;
}
li {
  border: 1px solid blue;
  padding: 1rem;
  text-align: center;
}
.user-list-enter-from {
  opacity: 0;
  transform: translateX(-30px);
}
.user-list-enter-active {
  transition: all 1s ease-out;
}
.user-list-enter-to,
.user-list-leave-from {
  opacity: 1;
  transform: translateX(0);
}

.user-list-leave-active {
  transition: all 1s ease-out;
  position: absolute;
}
.user-list-leave-to {
  opacity: 1;
  transform: translateX(30px);
}
.user-list-move {
  transition: transform 0.8s ease;
}
</style>