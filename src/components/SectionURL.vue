<template>
  <div class="sectionUrl w-full px-40 flex flex-col justify-evenly items-center">
    <div class="url_form w-full px-16 py-10 rounded-xl">
      <form action="" @submit.prevent class="flex flex-col justify-center items-center">
        <div class="flex justify-center items-center w-full">
          <input type="text" v-model="inputUrl" class="rounded-xl w-full h-16 px-4 text-xl" placeholder="Shorten a link here...">
          <div class="rounded-xl flex justify-center items-center button h-16 w-44 ml-6 cursor-pointer" @click="shortenUrl">
            <span class="text-white font-bold text-xl pointer-events-none">Shorten It!</span>
          </div>
        </div>
        <div class="mt-3 mb-0 p-0" v-show="invalidUrl">
          <span class="text-red-500 font-bold">{{invalidUrlText}}</span>
        </div>
        <div class="mt-3 mb-0 p-0" v-show="shortUrl">
          <p class="text-green-500 font-bold">Voici votre lien : <span @click="copyURL" class="cursor-pointer" ref="shortLink">{{shortUrl}}</span></p>
        </div>
      </form>
    </div>
    <div class="flex flex-col justify-center items-center px-24 mb-16">
      <h1 class="text-4xl font-bold mb-4">Advanced Statistics</h1>
      <p class="text-lg text-gray-400 px-48">Track how your links are perfoming across the web with our advanced statistics dashboard</p>
    </div>
    <div class="flex justify-center mb-36">
      <!-- Card Branding -->
      <div class="rounded-md bg-white relative flex flex-col justify-start items-start py-6 px-10 w-1/3 card-branding">
        <div class="rounded-full flex justify-center items-center icon p-6 absolute">
          <img src="../assets/icon-brand-recognition.svg" alt="">
        </div>
        <h1 class="mb-7 mt-12 text-2xl title font-bold">Detailed Records</h1>
        <p class="text-left">Boost your brand recognition with each click. Generic links don't mean a thing. Branded links help instil confidence in your content.</p>
      </div>
      <!-- Bande latérale -->
      <div class="flex justify-center items-center">
        <span class="barre my-5"></span>
      </div>
      <!-- Card Records -->
      <div class="rounded-md bg-white relative flex flex-col justify-start items-start py-6 px-10 w-1/3 card-records">
        <div class="rounded-full flex justify-center items-center icon p-6 absolute">
          <img src="../assets/icon-detailed-records.svg" alt="">
        </div>
        <h1 class="mb-7 mt-12 text-2xl title font-bold">Brand Recognition</h1>
        <p class="text-left">Gain insights into who is clicking your links. Knowing when and where people engage with your content helps inform better decisions.</p>
      </div>
      <!-- Bande latérale -->
      <div class="flex justify-center items-center">
        <span class="barre my-5"></span>
      </div>
      <!-- Card Customizable -->
      <div class="rounded-md bg-white relative flex flex-col justify-start items-start py-6 px-10 w-1/3 card-customizable">
        <div class="rounded-full flex justify-center items-center icon p-6 absolute">
          <img src="../assets/icon-fully-customizable.svg" alt="">
        </div>
        <h1 class="mb-7 mt-12 text-2xl title font-bold">Brand Recognition</h1>
        <p class="text-left">Improve brand awareness and content discoverability through customizable links, supercharging audience engagement.</p>
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";

export default {
  name: "SectionURL",
  data(){
    return {
      inputUrl: "",
      shortUrl: "",
      invalidUrl: false,
      invalidUrlText: ""
    }
  },
  methods: {
    shortenUrl() {
      if (this.inputUrl) {
        this.invalidUrl = false;
        var pattern = /(ftp|http|https):(\w+:{0,1}\w*@)?(\S+)(:[0-9]+)?(|([\w#!:.?+=&%@!]))?/;
        let res = pattern.test(this.inputUrl);
        if (res) {
          console.log("hello");
          axios.get(`https://api.shrtco.de/v2/shorten?url=${this.inputUrl}`)
            .then(response => {
              this.shortUrl = response.data.result.short_link
              })
        } else {
          this.invalidUrl = true;
          this.invalidUrlText = "Url invalid"
        }
      } else {
        this.invalidUrl = true;
        this.invalidUrlText = "Please insert an Url"
      }
    },
    copyURL(){
      let Url = this.$refs.shortLink;
      // Copy to clipboard
      navigator.clipboard.writeText(Url.innerText)
    }
  }
}
</script>

<style scoped>

.sectionUrl {
  background-color: hsl(0, 0%, 90%);
  /* height: 800px; */
}

.url_form {
  background-image: url("../assets/bg-shorten-desktop.svg");
  background-repeat: no-repeat;
  background-size: cover;
  background-color: #3a3053;
  transform: translateY(-50%);
}

.icon {
  background-color: hsl(257, 27%, 26%);
  top: -20%;
}

.barre {
  height: 10px;
  width: 20px;
  background-color: #2bd1d1;
}

.title {
  color: hsl(257, 27%, 26%)
}

.card-records {
  transform: translateY(15%);
}

.card-customizable {
  transform: translateY(30%);
}
</style>