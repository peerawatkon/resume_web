<!-- <template>
  <div class="section" data-theme="cupcake">
    <div class="flex h-screen">
      <div class="m-auto">
        <h3 class="text-9xl">Profile</h3>
        <div class="mockup-window border border-base-300">
          <div class="px-4 py-16 border-t border-base-300">
            <div class="avatar">
              <div class="w-24 rounded">
                <img src="./img/earth.jpg" />
              </div>
            </div>
            <div>
              <h2>Name : Peerawat Konpa</h2>
            </div>
            <div>
              <h2>ID Number : 6314110023</h2>
            </div>
            <div> 
              <h2>Gmail : 6314110023@mut.ac.th</h2>
            </div>
            <div>
              <h2>
                <select class="select w-full max-w-xs">
                  <option disabled selected>Sex</option>
                  <option>male</option>
                  <option>female</option>
                </select>
              </h2>
            </div>
            <div>
              <h2>old : 22</h2>
            </div>
            <div>
              <h2>High school education : Setthabutbampen</h2>
            </div>
            <div>
              <h2>University :MahanakornUniversity of Technology</h2>
            </div>
            <div>
              <h2>Line : peerawat konpa</h2>
            </div>
            <div>
              <h2>facebook : peerawat konpa</h2>
            </div>
            <div>
              <h2>
                instagram : pe_earth
                <button class="btn">
                  IG
                  <div class="badge">+99</div>
                </button>
              </h2>
            </div>
            <div class="rating">
              <input type="radio" name="rating-1" class="mask mask-star" />
              <input
                type="radio"
                name="rating-1"
                class="mask mask-star"
                checked
              />
              <input type="radio" name="rating-1" class="mask mask-star" />
              <input type="radio" name="rating-1" class="mask mask-star" />
              <input type="radio" name="rating-1" class="mask mask-star" />
            </div>
            <div class="form-control">
              <label class="label cursor-pointer">
                <input type="checkbox" class="toggle" checked />
              </label>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
  <div class="section" data-theme="valentine">
    <div class="flex h-screen">
      <div class="m-auto">
        <h3 class="text-9xl">section two</h3>
      </div>
    </div>
  </div>
</template>

<script setup>
</script>

<style scoped>
.section {
  height: 100vh;
}
</style> -->
<template>
  <header>
    <div class="navbar bg-base-100">
      <div class="navbar-start">
        <div class="dropdown">
          <label tabindex="0" class="btn btn-ghost lg:hidden">
            <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5" fill="none" viewBox="0 0 24 24" stroke="currentColor"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 6h16M4 12h8m-8 6h16" /></svg>
          </label>
          <ul tabindex="0" class="menu menu-sm dropdown-content mt-3 z-[1] p-2 shadow bg-base-100 rounded-box w-52">
            <li v-for="menu in menuList" :key="menu.name"><RouterLink :to="menu.path">{{ menu.name }}</RouterLink></li>
          </ul>
        </div>
        <a class="btn btn-ghost normal-case text-xl">daisyUI</a>
      </div>
      <div class="navbar-center hidden lg:flex">
        <ul class="menu menu-horizontal px-1">
          <li v-for="menu in menuList" :key="menu.name"><RouterLink :to="menu.path">{{ menu.name }}</RouterLink></li>
        </ul>
      </div>
      <!-- <div class="navbar-end">
        <a class="btn">Button</a>
      </div> -->
    </div>
  </header>
  <div class="container mx-auto">
    <RouterView :key="router.currentRoute.value.name"></RouterView>
  </div>
</template>

<script setup>
import { RouterView, RouterLink } from 'vue-router';
import { useRouter } from 'vue-router';
const router = useRouter();
const menuList = [
  { path:"/", name: "home"},
  { path:"/create", name: "Create"}
]

</script>

<style scoped>

</style>
