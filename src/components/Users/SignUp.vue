<template>
  <div>
    <h1>회원 가입</h1>
    <v-text-field v-model="userId" label="아이디"></v-text-field>
    <v-text-field type="password" v-model="password" label="비밀번호"></v-text-field>
    <v-text-field v-model="name" label="이름"></v-text-field>
    <v-text-field v-model="address" label="주소"></v-text-field>
    <v-text-field v-model="src" label="이미지"></v-text-field>
    <v-btn @click="signUp">가입하기</v-btn>
  </div>
</template>

<script>
import { EventBus } from '@/main.js';
import { mapMutations, mapActions } from 'vuex';

export default {
  data() {
    return {
      userId: null,
      password: null,
      name: null,
      address: null,
      src: null
    };
  },
  methods: {
    ...mapActions(['addUsers']),
    signUp() {
      const userObj = {
        userId: this.userId,
        password: this.password,
        name: this.name,
        address: this.address,
        src: this.src
      };
      this.addUsers(userObj);
      this.clearForm();
    },
    clearForm() {
      this.userId = null;
      this.password = null;
      this.name = null;
      this.address = null;
      this.src = null;
    }
  }
};
</script>
