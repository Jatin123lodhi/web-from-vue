<template>
  <form @submit.prevent="handleSubmit">
    <label>Email</label>
    <input v-model="email" type="email" />
    <br />
    <label>Password</label>
    <input v-model="password" type="password" />
    <br />
    <label>Gender</label>
    <select v-model="gender">
      <option value="male">Male</option>
      <option value="female">Female</option>
    </select>
    <br />
    <label>Terms and conditons</label>
    <input v-model="terms" type="checkbox" />
    <br />
    <div>
      <label>Select Skills</label>
      <br />
      <label>HTML</label>
      <input v-model="skills" value="html" type="checkbox" />
      <br />
      <label>CSS</label>
      <input v-model="skills" value="css" type="checkbox" />
      <br />
      <label>Java</label>
      <input v-model="skills" value="java" type="checkbox" />
    </div>

    <div>
        <label>Enter other skills </label>
        <input v-model="tempSkill" type="text" @keyup.enter="addSkill"/>
        <ul>
            <li @click="deleteSkill"  v-for="skill in otherSkills" :key="skill">{{skill}}</li>
        </ul>
    </div>
    <button >Submit</button>
  </form>

  <hr />
  <p>Email: {{ email }}</p>
  <p>Password: {{ password }}</p>
  <p>Gender: {{ gender }}</p>
  <p>Terms: {{ terms }}</p>
  <p>Skills: {{ skills }}</p>
</template>

<script>
export default {
  data() {
    return {
      email: "",
      password: "",
      gender: "female",
      terms: false,
      tempSkill: "",
      skills: [],
      otherSkills: [],
    };
  },
  methods:{
    addSkill(e){
        this.otherSkills.push(this.tempSkill)
        this.tempSkill = ''
    },
    deleteSkill(e){
        this.otherSkills = this.otherSkills.filter(s=>s!==e.target.innerHTML)
    },
    handleSubmit(){
        console.log('form submitted')
    }
  }
};
</script>

<style></style>
