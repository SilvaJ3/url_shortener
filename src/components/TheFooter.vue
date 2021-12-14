<template>
  <footer>
    <div class="flex justify-center items-center w-full py-14 px-10 footer">

      <div class="w-2/5 flex justify-center items-start h-44">
        <h1 class="text-white font-bold text-3xl">Shortly</h1>
      </div>

      <div class="w-2/5 flex justify-start items-start h-44">
        <div class="w-1/3 flex flex-col items-start">
          <h1 class="font-bold text-white mb-3">Features</h1>
          <ul class="flex flex-col justify-evenly items-start list-none">
            <li class="text-gray-500">Link Shortening</li>
            <li class="text-gray-500 my-2">Branded Links</li>
            <li class="text-gray-500">Analytics</li>
          </ul>
        </div>
        <div class="w-1/3 flex flex-col items-start">
          <h1 class="font-bold text-white mb-3">Resources</h1>
          <ul class="flex flex-col justify-evenly items-start list-none">
            <li class="text-gray-500">Blog</li>
            <li class="text-gray-500 my-2">Developers</li>
            <li class="text-gray-500">Support</li>
          </ul>
        </div>
        <div class="w-1/3 flex flex-col items-start">
          <h1 class="font-bold text-white mb-3">Company</h1>
          <ul class="flex flex-col justify-evenly items-start list-none">
            <li class="text-gray-500">About</li>
            <li class="text-gray-500 my-2">Our Team</li>
            <li class="text-gray-500">Careers</li>
            <li class="text-gray-500 my-2">Contact</li>
          </ul>
        </div>
      </div>

      <div class="w-1/5 flex items-start">
        <div class="flex justify-start items-start w-full h-44">
          <img src="../assets/icon-facebook.svg" alt="" class="mx-2">
          <img src="../assets/icon-twitter.svg" alt="" class="mx-2">
          <img src="../assets/icon-pinterest.svg" alt="" class="mx-2">
          <img src="../assets/icon-instagram.svg" alt="" class="mx-2">
        </div>
      </div>
    </div>
  </footer>
</template>

<script>
export default {
  name: "TheFooter",
}
</script>

<style scoped>
.footer {
  background-color: #232027;
}

.footer li {
  color: #a3a1a4;
}

</style>