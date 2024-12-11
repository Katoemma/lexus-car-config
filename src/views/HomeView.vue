<script setup>
import { ref } from "vue";

const rim = ref(1);
const side = ref("back");
const color = ref("black");
const interiorColor = ref("black")


const rims = [1, 2];
const sides = ["front", "back"];
const colors = ["black", "white", "red", "blue", "grey", "darkgrey", "orange"];
const interiorColors = ["black", "red"]
</script>

<template>
  <main class="w-full mt-6" style="background-image: url(../assets/user/store.jpg);">
    <div class="flex items center">
      <div class="flex flex-col w-2/3 bg-red-400">
        <img :src="side === 'front' ? `src/assets/images/front ${color}.jpg` : `src/assets/images/rim ${rim} ${side} ${color}.jpg`" alt="">

        <img :src="`src/assets/images/interior ${interiorColor}.jpg`">
      </div>

      <!-- Configurator Section -->
      <div class="mt-4">
        <label for="rim-select" class="font-bold">Exterior color</label>
        <div class="flex space-x-2">
          <div v-for="c in colors" :key="c" :style="{ backgroundColor: c }"
            class="w-12 h-12 rounded-full cursor-pointer border-2 border-gray-400" @click="color = c">
          </div>
        </div>
        <div class="flex">
          <div v-for="r in rims">
            <button >
              <div class="text-gray-500 bg-gray-200 rounded-lg shadow px-4 mx-1">
                {{ r }}
              </div>
            </button>

          </div>
        </div>
        <select id="rim-select" v-model="rim">
          <option v-for="r in rims" :key="r" :value="r">{{ r }}</option>
        </select>

        <label>Select View position</label>
        <div class="flex gap">


          <button @click="side = 'front'" :class="{ 'active': side === 'front' }"><img src="@/assets/user/front.png"
              alt="" class="w-16"></button>
          <button @click="side = 'back'" :class="{ 'active': side === 'back' }"><img src="@/assets/user/back.png" alt=""
              class="w-16"></button>
        </div>

        <label for="rim-select" class="font-bold">Interior color</label>
        <div class="flex space-x-2">
          <div v-for="c in interiorColors" :key="c" :style="{ backgroundColor: c }"
            class="w-12 h-12 rounded-full cursor-pointer border-2 border-black" @click="interiorColor = c">
          </div>
        </div>
      </div>

    </div>
  </main>
</template>

<style>
.active {
  border: 2px solid black;
  /* Highlight active side selection */
}
</style>
