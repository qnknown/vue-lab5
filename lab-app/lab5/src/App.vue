<template>
  <div id="app">
    <h1>User List</h1>

    <div class="toolbar">
      <button @click="filterUsers('all')">All</button>
      <button @click="filterUsers('male')">Male</button>
      <button @click="filterUsers('female')">Female</button>
    </div>

    <div v-if="filteredUsers.length === 0">Список юзерів пустий</div>
    <div v-else>
      <UserCard
        v-for="user in filteredUsers"
        :key="user.firstName"
        :user="user"
      />
    </div>
  </div>
</template>

<script lang="ts">
import { Options, Vue } from "vue-class-component";
import UserCard from "./components/userCard.vue";

@Options({
  components: {
    UserCard,
  },
})
export default class App extends Vue {
  users = [
    {
      firstName: "John",
      lastName: "Doe",
      age: 25,
      gender: "male",
      position: "Developer",
      photo: require("@/assets/user.jpg"),
      hobbies: ["Coding", "Reading"],
    },
    {
      firstName: "Jane",
      lastName: "Smith",
      age: 22,
      gender: "female",
      position: "Designer",
      photo: require("@/assets/user.jpg"),
      hobbies: ["Art", "Music"],
    },
    {
      firstName: "Michael",
      lastName: "Johnson",
      age: 30,
      gender: "male",
      position: "Manager",
      photo: require("@/assets/user.jpg"),
      hobbies: ["Sports", "Travel"],
    },
    {
      firstName: "Emily",
      lastName: "Davis",
      age: 20,
      gender: "female",
      position: "Intern",
      photo: require("@/assets/user.jpg"),
      hobbies: ["Photography", "Cooking"],
    },
    {
      firstName: "William",
      lastName: "Brown",
      age: 29,
      gender: "male",
      position: "Analyst",
      photo: require("@/assets/user.jpg"),
      hobbies: ["Gaming", "Reading"],
    },
    {
      firstName: "Olivia",
      lastName: "Wilson",
      age: 26,
      gender: "female",
      position: "Developer",
      photo: require("@/assets/user.jpg"),
      hobbies: ["Coding", "Traveling"],
    },
    {
      firstName: "James",
      lastName: "Garcia",
      age: 35,
      gender: "male",
      position: "Director",
      photo: require("@/assets/user.jpg"),
      hobbies: ["Golf", "Fishing"],
    },
    {
      firstName: "Sophia",
      lastName: "Martinez",
      age: 18,
      gender: "female",
      position: "Student",
      photo: require("@/assets/user.jpg"),
      hobbies: ["Dancing", "Reading"],
    },
    {
      firstName: "Jacob",
      lastName: "Hernandez",
      age: 40,
      gender: "male",
      position: "CEO",
      photo: require("@/assets/user.jpg"),
      hobbies: ["Travel", "Music"],
    },
    {
      firstName: "Ava",
      lastName: "Lopez",
      age: 21,
      gender: "female",
      position: "Teacher",
      photo: require("@/assets/user.jpg"),
      hobbies: ["Gardening", "Painting"],
    },
  ];

  filteredUsers = this.users;

  filterUsers(gender: string) {
    if (gender === "male") {
      this.filteredUsers = this.users.filter((user) => user.gender === "male");
    } else if (gender === "female") {
      this.filteredUsers = this.users.filter(
        (user) => user.gender === "female"
      );
    } else {
      this.filteredUsers = this.users; // Reset to all users
    }
  }
}
</script>

<style>
#app {
  display: flex;
  flex-direction: column;
  align-items: center; /* Center elements horizontally */
}

.toolbar {
  margin-bottom: 20px;
}

button {
  margin-right: 10px;
  padding: 10px;
  background-color: #4caf50;
  color: white;
  border: none;
  border-radius: 5px;
  cursor: pointer;
}

button:hover {
  background-color: #45a049;
}
</style>
