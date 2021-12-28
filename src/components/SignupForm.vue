<template>
  <form @submit.prevent="handleSubmit">
      <label>Email:</label>
      <input type="email" required v-model="email">

      <label>Password:</label>
      <input type="password" v-model="password" required>
      <div v-if="passwordError" class="error">{{ passwordError }} </div>

      <label>Role:</label>
      <select v-model="role">
          <option value="developer">web developer</option>
          <option value="designer">web designer</option>
      </select>



      <label>Skills:</label>
      <input type="text" v-model="tempSkill" @keyup.alt="addSkill">
      <div v-for="skill in skills" :key="skill" class="pill">
          <span @click="delSkill(skill)">{{ skill }}</span>
      </div>





      <div class="terms">
          <input type="checkbox" required v-model="terms">
          <label>Accept terms and conditions</label>
      </div>


      <!-- <div>
          <input type="checkbox" value="Gulu" v-model="names">
          <label>Gulu</label>
      </div>
      <div>
          <input type="checkbox" value="Cute" v-model="names">
          <label>Cute</label>
      </div>
      <div>
          <input type="checkbox" value="Gudong" v-model="names">
          <label>Gudong</label>
      </div> -->

      <div class="submit">
      <button>Create an Account</button>
      </div>

  </form>

  <p>Email:{{ email }} </p>
  <p>Password:{{ password }} </p>
  <p>Role:{{ role }} </p>
  <p>Terms accepted:{{ terms }} </p>
  <p>Names:{{ names }} </p>
  <p>skills:{{ skills }} </p>
</template>

<script>
export default {
    data() {
        return {
            // email: 'v-model双向绑定',
            email: '',
            password: '',
            role: 'developer',
            terms: false,
            names: [],
            tempSkill: '',
            skills: [],
            passwordError: ''
        }
    },
    methods: {
        addSkill(e) {
            // console.log(e)
            if(e.key === ',' && this.tempSkill) {
                if(!this.skills.includes(this.tempSkill)) {
                    this.skills.push(this.tempSkill)
                }
                this.tempSkill = ''
            }
        },
        delSkill(skill) {
        // console.log(e)
        this.skills = this.skills.filter((item) => {
            return skill !== item
        })
        },
        handleSubmit() {
            // console.log('form')
            // 验证密码
            this.passwordError = this.password.length > 5 ? '' : '至少输入6位密码'

            // 没有错误的情况下，输出一些信息到控制台
            if(!this.passwordError) {
                console.log('email: ', this.email)
                console.log('password: ', this.password)
                console.log('role: ', this.role)
                console.log('skills: ', this.skills)
                console.log('terms accepted: ', this.terms)
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
    padding: 40px;
    border-radius: 10px;
}
label {
    color: #aaa;
    display: inline-block;
    margin: 25px 0 15px 0;
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
.pill {
    display: inline-block;
    margin: 20px 10px 0 0;
    padding: 6px 12px;
    background: #eee;
    border-radius: 20px;
    font-size: 12px;
    letter-spacing: 1px;
    font-weight: bold;
    color: #777;
    cursor: pointer;
}
button {
    background: #0b6dff;
    border: 0;
    padding: 10px 20px;
    margin-top: 20px;
    color: white;
    border-radius: 20px;
}
.submit {
    text-align: center;
}
.error {
    color: #ff0062;
    margin-top: 10px;
    font-size: 0.8em;
    font-weight: bold;
}
</style>