<template>
  <div id="app">
    <header>
      <nav class="navbar fixed-top navbar-expand-sm bg-light shadow-sm">
        <button
          class="navbar-toggler"
          type="button"
          data-toggle="collapse"
          data-target="#navbarsExample03"
          aria-controls="navbarsExample03"
          aria-expanded="false"
          aria-label="Toggle navigation"
        >
          <i class="fas fa-bars"></i>
        </button>

        <div class="collapse navbar-collapse" id="navbarsExample03">
          <ul class="navbar-nav mr-auto">
            <li class="nav-item active">
              <a class="nav-link" href="#experience">{{ui_lang.experience[currLoc]}}</a>
            </li>
            <li class="nav-item">
              <a class="nav-link" href="#education">{{ui_lang.education[currLoc]}}</a>
            </li>
            <li class="nav-item">
              <a class="nav-link" href="#extraskill">{{ui_lang.extraskill[currLoc]}}</a>
            </li>
          </ul>
          <div class="btn-group btn-group-sm">
            <button
              type="button"
              class="btn"
              v-bind:class="{'btn-primary' : locBtn_EN_active}"
              v-on:click="lang_toggle('location_en')"
            >En</button>
            <button
              type="button"
              class="btn"
              v-bind:class="{'btn-primary' : locBtn_RU_active}"
              v-on:click="lang_toggle('location_ru')"
            >Ру</button>
          </div>
        </div>
      </nav>
    </header>

    <main class="container">
      <div class="row">
        <div class="col-sm-4">
          <about
            :fio="info.fio[currLoc]"
            :position="info.position[currLoc]"
            :address="info.address[currLoc]"
            :contact="info.contact[currLoc]"
          ></about>
        </div>
        <div class="col-sm-8">
          <list id="experience" :data="exp">
            <template v-slot:ListHeader>
              <i :class="exp.icon"></i>
              {{ui_lang.experience[currLoc]}}
            </template>
            <template v-slot:ListBody>
              <div v-for="i in exp.data[currLoc]" v-bind:key="i.id">
                <expirience :data="i" />
              </div>
            </template>
          </list>
          <list id="education" :data="edu">
            <template v-slot:ListHeader>
              <i :class="edu.icon"></i>
              {{ui_lang.education[currLoc]}}
            </template>
            <template v-slot:ListBody>
              <div v-for="i in edu.data" v-bind:key="i.id">
                <eduсation :data="i" />
              </div>
            </template>
          </list>
          <list id="extraskill" :data="eskill">
            <template v-slot:ListHeader>
              <i :class="eskill.icon"></i>
               {{ui_lang.extraskill[currLoc]}}
            </template>
            <template v-slot:ListBody>
              <div class="row row-cols-1 row-cols-md-2">
                <template v-for="i in eskill.data">
                  <eskill :data="i" v-bind:key="i.id" />
                </template>
              </div>
            </template>
          </list>
        </div>
      </div>
    </main>

    <!-- Footer -->
    <footer class="page-footer font-small blue pt-4">
      <!-- Footer Links -->
      <div class="container-fluid text-center text-md-left">
        <!-- Grid row -->
        <div class="row">
          <!-- Grid column -->
          <div class="col-md-6 mt-md-0 mt-3">
            <!-- Content -->
            <h5 class="text-uppercase">Footer Content</h5>
            <p>Here you can use rows and columns to organize your footer content.</p>
          </div>
          <!-- Grid column -->
          <hr class="clearfix w-100 d-md-none pb-3" />
          <!-- Grid column -->
          <div class="col-md-3 mb-md-0 mb-3">
            <!-- Links -->
            <h5 class="text-uppercase">Links</h5>
            <ul class="list-unstyled">
              <li>
                <a href="#!">Link 1</a>
              </li>
              <li>
                <a href="#!">Link 2</a>
              </li>
              <li>
                <a href="#!">Link 3</a>
              </li>
              <li>
                <a href="#!">Link 4</a>
              </li>
            </ul>
          </div>
          <!-- Grid column -->
          <!-- Grid column -->
          <div class="col-md-3 mb-md-0 mb-3">
            <!-- Links -->
            <h5 class="text-uppercase">Links</h5>
            <ul class="list-unstyled">
              <li>
                <a href="#!">Link 1</a>
              </li>
              <li>
                <a href="#!">Link 2</a>
              </li>
              <li>
                <a href="#!">Link 3</a>
              </li>
              <li>
                <a href="#!">Link 4</a>
              </li>
            </ul>
          </div>
          <!-- Grid column -->
        </div>
        <!-- Grid row -->
      </div>
      <!-- Footer Links -->
      <!-- Copyright -->
      <!--<div class="footer-copyright text-center py-3">
        © 2020 Copyright:
        <a href="https://mdbootstrap.com/">MDBootstrap.com</a>
      </div>-->
      <!-- Copyright -->
    </footer>
    <!-- Footer -->
  </div>
</template>

<script>
import about from "./components/about.vue";

import list from "./components/list/list.vue";
import expirience from "./components/experience/expirience.vue"
import eduсation from "./components/education/education.vue";
import eskill from "./components/eskill/eskill.vue";

import ui_lang_package from "./assets/ui_lang.json";
import experienceInfo from "./assets/experience.json";
import aboutInfo from "./assets/about.json";
import educationInfo from "./assets/education.json";
import extraskillsInfo from "./assets/extraskills.json";

export default {
  name: "App",

  components: {
    list, 
    about,
    expirience,
    eduсation,
    eskill
  },

  data: function() {
    return {
      currLoc: "location_ru",
      langlist: [
        "location_ru",
        "location_en"
      ],
     ui_lang: "", 
     exp:"", //this.getExpienceInfo(currLoc),
     info:"",  //this.getAboutInfo(currLoc),
     edu:"",  //this.getEducationInfo(currLoc),
     eskill:"",  //this.getExtraSkills(currLoc)
    };
  },
  beforeCreated: function(){
     
  },
  
  created: function(){
    
    this.currLoc = "location_ru"; 
    this.ui_lang = this.getUiLang();
    this.exp = this.getExpienceInfo();
    this.info = this.getAboutInfo();
    this.edu = this.getEducationInfo();
    this.eskill = this.getExtraSkills();  

  },

  methods: {

    resetData: function(){
      this.exp = this.getExpienceInfo();
      this.info = this.getAboutInfo();
      this.edu = this.getEducationInfo();
      this.eskill = this.getExtraSkills();
    },
    getUiLang: function(){
       var out = ui_lang_package;
      return out;
    },
    getExpienceInfo: function() {
      var out = experienceInfo;
      return out;
    },
    getAboutInfo: function() {
      var out = aboutInfo;
      return out;
    },
    getEducationInfo: function() {
      var out = educationInfo;
      return out;
    },
    getExtraSkills: function() {
      var out = extraskillsInfo;
      return out;
    },
    
    lang_toggle: function(newLocation){
      this.currLoc = newLocation;
      this.resetData();
    },

  },
  computed: {
    locBtn_EN_active:function(){
      return this.currLoc == "location_en";
    },
    locBtn_RU_active:function(){
      return this.currLoc == "location_ru";
    }
  }

};
</script>

<style>
.container {
  margin-top: 55px;
}
.nav-link {
  color: black;
}
</style>
