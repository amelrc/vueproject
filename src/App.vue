<template>
  <h1 @click="handleClick">{{title}}</h1>
  <div class="alignment">
    <div>
      <h2>First List ({{firstListAmount}})</h2>
      <transition-group tag="ul" name='list' appear>
        <li @click="() => onSelect(user, index)" v-for="(user, index) in users" :key="user">
          <User :name='user.name' :age='user.age' />
        </li>
      </transition-group>
    </div>
    <div>
      <h2>Second List ({{secondListAmount}})</h2>
      <transition-group tag="ul" name='list' appear>
        <li v-for="user in secondList" :key="user">
          <User :name='user.name' :age='user.age' :style="secondList.length > 0 ? {'color':'red'} : ''"/>
        </li>
      </transition-group>
    </div>
  </div>
</template>

<script>
import User from './components/User.vue'
export default {
  name: "App",
  components: {
  User
  },
  data() {
    return {
      title: 'Hello Square Users',
      usersNumber: 0,
      users: [
        {
          name: "Bas",
          age: 26,
        },
        {
          name: "Daphne",
          age: 38,
        },
        {
          name: "Martijn",
          age: 50,
        },
        {
          name: "Gerben",
          age: 42,
        },
        {
          name: "Wytze",
          age: 25,
        },
        {
          name: "Robin",
          age: 29,
        },
        {
          name: "Ralph",
          age: 40,
        },
        {
          name: "Stefanie",
          age: 38,
        },
        {
          name: "Souni",
          age: 38,
        },
        {
          name: "Jango",
          age: 39,
        },
      ],
      secondList: [],
    };
  },
  methods: {
    onSelect(user,index) {
      this.secondList.push(user)
      this.users.splice(index, 1);
    },
    updateUserListNumber(array) {
      return array.length
    },
  },
  computed: {
    firstListAmount() {
      return this.updateUserListNumber(this.users)
    },
    secondListAmount() {
      return this.updateUserListNumber(this.secondList)
    }
  },
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
ul {
  list-style-type: none;
  display: flex;
  flex-direction: column;
  align-items: flex-start;
  position: relative;
}
.alignment {
  display: flex;
  justify-content: space-around;
}
/* list transitions */
  .list-enter-from {
    opacity: 0;
    transform: scale(0.6);
  }
  .list-enter-active {
    transition: all 0.4s ease;
  }
  .list-leave-to {
    opacity: 0;
    transform: scale(0.6);
  }
  .list-leave-active {
    transition: all 0.4s ease;
    position: absolute;
  }
  .list-move {
    transition: all 0.3s ease;
  }
</style>
