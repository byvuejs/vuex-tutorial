<template>
  <div>
    <h1>회원 리스트</h1>
    <h3>총 {{ allUsersCount }}명</h3>
    <h3>서울 거주 회원 : {{ countOfSeoul }}명 ({{ percentOfSeoul }}%)</h3>
    <v-list two-line>
      <v-list-tile v-for="(user, index) in allUsers" :key="index" avatar>
        <v-list-tile-avatar color="grey lighten-3">
          <img :src="user.src" />
        </v-list-tile-avatar>

        <v-list-tile-content>
          <v-list-tile-title v-html="user.name"></v-list-tile-title>
          <v-list-tile-sub-title>id:#{{ index }} / {{ user.address }} 거주</v-list-tile-sub-title>
        </v-list-tile-content>
      </v-list-tile>
    </v-list>
  </div>
</template>

<script>
import { EventBus } from "@/main.js";
import { mapState, mapGetters } from "vuex";

export default {
  data() {
    return {
    }
  },
  computed: {
    ...mapState(['allUsers']),
    ...mapGetters(['allUsersCount', 'countOfSeoul', 'percentOfSeoul'])
  },
  mounted() {
    EventBus.$on("signUp", users => {
      this.$store.state.allUsers.push(users);
    });
  }
};
</script>
