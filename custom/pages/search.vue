<template>
  <section class="grid grid-cols-6 gap-3">
    <div class="col-span-6 px-3 py-3 bg-red-400">
      <label class="floating-label">
        <span>Wonach suchst du ?</span>
        <input type="search" v-model="query" class="input w-full" />
      </label>
    </div>
    <div v-for="item in 6" class="col-span-6 xs:col-span-3">
      <div class="card shadow-sm bg-gray-300">
        <figure>
          <img
              src="https://img.daisyui.com/images/stock/photo-1606107557195-0e29a4b5b4aa.webp"
              alt="Shoes" />
        </figure>
        <div class="card-body">
          <h2 class="card-title">Card Title</h2>
          <p>A card component has a figure, a body part, and inside body there are title and actions parts</p>
          <div class="card-actions justify-end">
            <button class="btn btn-primary">Buy Now</button>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup lang="ts">
import {ref} from 'vue'
import {addBreadcrumb} from '@/util/breadcrumbs'

const query = ref('');

onMounted(()=>{
  addBreadcrumb({
    label: 'Search',
    icon: 'magnifying-glass',
    link: 'search',
  });
});
</script>