<template>
  <div class="hello">
    <!--  Directives examples are commented
    <div class="holder">
      <ul>
        <li v-for="(data,index) in skills" :key='index'>
          {{index}}: {{data.skill}}
        </li>
      </ul>
      <p v-if="skills.length >= 2">
        You have more than two skills
      </p>
      <p v-else>
        You have less than two skill
      </p>
    -->
      <!-- Apply the following class "Alert" just if showAlert is true -->
      <!--
      <div v-bind:class="{alert : showAlert, 'another-class': showClass}">
        <h4>Holis</h4>
      </div>

      <div v-bind:class="alertObject">
        <h4>Holis</h4>
      </div>

      <div v-bind:style="{backgroundColor: bgColor, width: bgWidth, height: bgHeight}">
        <h4>Holis</h4>
      </div>
    </div>
  -->

  <div class="holder">

    <form @submit.prevent="addSkill">
      <input type="text" placeholder="Enter a skill you have.." v-model="skill" v-validate="'min:5'" name="skill"/>
      <transition name="alert-in" enter-active-class="animated flipInX" leave-active-class="animated flipOutX">
        <p class="alert" v-if="errors.has('skill')">
           {{errors.first('skill')}}
        </p>
      </transition>
    </form>

    <ul>
      <transition-group name="list" enter-active-class="animated bounceInUp" leave-active-class="animated bounceOutDown">
        <li v-for="(data,index) in skills" :key="index">{{data.skill}} <i class="fa fa-minus-circle" v-on:click="remove(index)"></i></li>
      </transition-group>
    </ul>

    <p>These are the skills you posses </p>
  </div>
  </div>
</template>

<script>
export default {
  name: 'Skills',
  data() {
    return {
      skill: '',
      skills: [
        {"skill":"Vue.js"},
        {"skill":"Frontend developer"}

      ]
      /*showAlert: true,
      showClass: true,
      alertObject: {
        alert: true
      },
      bgColor: 'yellow',
      bgWidth: '100%',
      bheight: '20px'*/
    }
  },
  methods: {
    addSkill() {
      this.$validator.validateAll().then((result) => {
        if(result) {
          this.skills.push({skill: this.skill})
          this.skill = '';
        } else {
          console.log("Not valid");
        }
      })

    },
    remove(id) {
      this.skills.splice(id,1);
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
@import "https://cdn.jsdelivr.net/npm/animate.css@3.5.1";
@import "https://use.fontawesome.com/releases/v5.4.1/css/all.css";

.another-class {
  border: 5px solid black;
}
.holder {
  background: #FFF;
  width: 800px;
}

ul {
  margin: 0;
  padding: 0;
  list-style-type: none;
}

ul li {
  padding: 20px;
  font-size: 1.3em;
  background-color: #E0EDF4;
  border-left: 5px solid #3EB3F6;
  margin-bottom: 2px;
  color: #3E5252;
  width: 750px;
}

p {
  text-align: center;
  padding: 30px 0;
  color: gray;
}

.container {
  box-shadow: 0px 0px 40px lightgray;
}

input {
  width: calc(100% - 40px);
  border: 0;
  padding: 20px;
  font-size: 1.3em;
  background-color: #323333;
  color: #687F7F;
}
.alert{
  background: #FDF2CE;
  font-weight: bold;
  display: inline-block;
  padding: 5px;
  margin-top: -20px;
}

.alert-in-enter-active {
  animation: bounce-in .5s;
}
.alert-in-leave-active {
  animation: bounce-in .5s reverse;
}

@keyframes bounce-in {
  0% {
    transform: scale(0);
  }
  50% {
    transform: scale(1.2);
  }
  100% {
    transform: scale(1);
  }
}

i {
  float: right;
  cursor: pointer;
}
</style>
