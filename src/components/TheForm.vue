<template>
  <form @submit.prevent="submitForm">
    <div class="form-control" :class="{invalid: userNameValidity === 'invalid'}">
      <label for="user-name">Your Name</label>
      <input id="user-name" name="user-name" type="text" v-model="userName" @blur="validateInput">
      <p style="color: red" v-if="userNameValidity === 'invalid'">Please enter a valid name</p>
    </div>
    <div class="form-control">
      <label for="age">Your Age (Years)</label>
      <input id="age" name="age" type="number" v-model="userAge">
    </div>
    <div class="form-control">
      <label for="referrer" name="referrer">
        <select name="referrer" id="referrer" v-model="referrer">
          <option value="google">Google</option>
          <option value="wom">Word of mouth</option>
          <option value="newspaper">Newspaper</option>
        </select>
      </label>
    </div>
    <div class="form-control">
      <h2>What you interested in?</h2>
      <div>
        <input id="interested-news" name="interested" type="checkbox" value="news" v-model="interest">
        <label for="interested-news">News</label>
      </div>
      <div>
        <input id="interested-tutorials" name="interested" type="checkbox" value="tutorials" v-model="interest">
        <label for="interested-news">Tutorials</label>
      </div>
      <div>
        <input id="interested-nothing" name="interested" type="checkbox" value="nothing" v-model="interest">
        <label for="interested-news">Nothing</label>
      </div>
    </div>
    <div class="form-control" >
      <h2>How do you learn&</h2>
      <div>
        <input id="how-video" name="how" type="radio" value="video" v-model="how" >
        <label for="how-video">Video Courses</label>
      </div>
      <div>
        <input id="how-blogs" name="how" type="radio" value="blogs" v-model="how">
        <label for="how-video">Blogs</label>
      </div>
      <div>
        <input id="how-other" name="how" type="radio" value="other" v-model="how">
        <label for="how-video">Other</label>
      </div>
    </div>

    <div class="form-control">
      <rating-control v-model="rating"></rating-control>
    </div>

    <div class="form-control">
      <input type="checkbox" name="confirm-terms" id="confirm-terms" v-model="confirm" />
      <label for="confirm-terms">Agree to terms use?</label>
    </div>
    <button>Save Data</button>
  </form>
</template>

<script>
import RatingControl from "@/components/RatingControl";
export default {
  name: "TheForm",
  components: {
    RatingControl
  },
  data() {
    return {
      userName: '',
      userAge: null,
      referrer: 'wom',
      interest: [],
      how: null,
      confirm: false,
      userNameValidity: 'pending',
      rating: null
    }
  },
  methods: {
    submitForm() {
        console.log('Rating')
        console.log(this.rating)
         this.rating = null
    },
    validateInput() {
      if (this.userName.trim() === '') {
        this.userNameValidity = 'invalid'
      } else {
        this.userNameValidity = 'valid'
      }
    }
  }
}
</script>

<style scoped>

form {
  margin: 2rem auto;
  max-width: 40rem;
  border-radius: 12px;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.26);
  padding: 2rem;
  background: white;
}

.form-control {
  margin: 0.5rem 0;
}

.form-control.invalid input {
  border-color: red;
}
.form-control.invalid label {
  color: red;
}

label {
  font-weight: bold;
}

h2 {
  font-size: 1rem;
  margin: 0.5rem 0;
}

input,
select {
  display: block;
  width: 100%;
  font: inherit;
  margin-top: 0.5rem;
}

select {
  width: auto;
}

input[type='checkbox'],
input[type='radio'] {
  display: inline-block;
  width: auto;
  margin-right: 1rem;
}

button {
  font: inherit;
  border: 1px solid #0076bb;
  background-color: #0076bb;
  color: white;
  cursor: pointer;
  padding: 0.75rem 2rem;
  border-radius: 30px;
}

button:hover,
button:active {
  border-color: #002350;
  background-color: #002350;
}



</style>