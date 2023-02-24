<template>
  <form>
    <label>Email: </label>
    <input type="email" required v-model="email">
    <label>Password: </label>
    <input type="password" required v-model="password">

    <label>Role: </label>
    <select v-model="role">
        <option value="SE">Software Engineer</option>
        <option value="QA">Software QA Engineer</option>
        <option value="PM">Product Manager</option>
    </select>
    <div>
        <label>skills: </label>
        <input type="text" v-model="tempSkill" @keyup="addSkill">
    </div>
    <div v-for="skill in skills" :key="skill" class="pill">
        {{ skill }}
    </div>

    <div class="terms">
        <input type="checkbox" v-model="checked" required>
        <label>Accept Terms and Conditions</label>
    </div>

    
  </form>
  <p>Email: {{ email }}</p>
  <p>Password: {{ password }}</p>
  <p>Role: {{ role }}</p> 
  <p>Status: {{ checked }}</p>

</template>

<script>
export default {
    data() {
        return {
            email: '',
            password: '',
            role: 'SE',
            checked: false,
            tempSkill: '',
            skills: []
        }
    },
    methods: {
        addSkill(e){
            if(e.key === ',' && this.tempSkill){
                this.skills.push(this.tempSkill)
            }
        }
    }
}
</script>

<style>
  form {
    max-width: 420px;
    margin: 30px auto;
    background: white;
    text-align: left;
    font-size: 25px;
    padding: 40px;
    border-radius: 10px;
  }
  label {
    color: #aaa;
    display: inline-block;
    margin: 25px 0 15px;
    font-size: 0.6em;
    text-transform: uppercase;
    letter-spacing: 1px;
    font-weight: bold;
  }
  input, select {
    display: block;
    padding: 10px 6px;
    width: 100%;
    box-sizing: border-box;
    border: none;
    border-bottom: 1px solid #ddd;
    color: #555;
  }
  input[type="checkbox"] {
    display: inline-block;
    width: 16px;
    margin: 0 10px 0 0;
    position: relative;
    top: 2px;
  }
</style>