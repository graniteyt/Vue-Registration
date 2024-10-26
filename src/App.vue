<template>
  <div className="inputs">
    <input type="text" v-model="Name" class="type">
    <input type="password" v-model="Pass" class="type">
    <input type="email" v-model="Mail" class="type">
  </div>
  <!-- <p>{{ Name }}</p>
  <p>{{ Pass }}</p>
  <p>{{ Mail }}</p> -->
  <button @click="sign()">Регистрация</button>

  <User v-for="(user, index) in users" :key="index" :user="user" :index="index" :deleteUser="deleteUser"/>

  <p className="error"> {{ error }}</p>
</template>

<script>
import User from './components/User.vue'
export default {
  components: { User },
  data() {
    return {
      users: [],
      error: '',
      Name: '',
      Pass: '',
      Mail: '',
    }
  },
  methods: {
    // insertData (val) {
    //   this.Name = val
    // }
    sign() {
      if (this.Name === '' || this.Pass === '' || this.Mail === '') {
        this.error = "Поле пустое!"
        return;
      }

      this.error = '';

      this.users.push({
        name: this.Name, 
        pass: this.Pass, 
        mail: this.Mail
      })

      // Clear input fields after adding a user
      this.Name = '';
      this.Pass = '';
      this.Mail = '';
    },
    deleteUser(index) {
      this.users.splice(index, 1);
    }
  }
}
</script>


<style scoped>
.inputs {
  display: flex;
  flex-direction: column;
}

input {
  border-radius: 5px;
  width: 200px;
  height: 30px;
  margin-bottom: 10px;
  border: 2px solid rgba(83, 83, 83, 0.73);
  background-color: rgba(225, 225, 225, 0.491);
  font-weight: 500;
  font-family: 'Franklin Gothic Medium', 'Arial Narrow', Arial, sans-serif;
  font-size: 16px;
}

button {
  background-color: rgb(125, 255, 212);
  height: 50px;
  width: 180px;
  font-size: 600;
  font-family: 'Franklin Gothic Medium', 'Arial Narrow', Arial, sans-serif;
  border-radius: 10px;
  border: none;
  font-size: 25px;
  transition: 0.5s;
}

button:hover {
  transform: translateY(-5px);
}

.output {
  margin-top: 10px;
  padding: 15px;
  background-color: rgb(220, 220, 220);
  box-shadow: 4px 4px 8px 0px rgba(34, 60, 80, 0.2);
  border-radius: 10px;
  font-size: 22px;
  width: auto;
  border: 1px black solid;
  max-width: fit-content;
  font-family: 'Franklin Gothic Medium', 'Arial Narrow', Arial, sans-serif;
  transition: 0.5s;
}

.output:hover {
  transform: translateY(-5px);
}
</style>
