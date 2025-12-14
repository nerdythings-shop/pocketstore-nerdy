<template>
  <!-- Footer -->
  <footer class="footer mx-auto max-w-6xl footer-center p-10 bg-base-300 text-base-content rounded">
    <div class="grid grid-flow-col gap-4">
      <a class="link link-hover font-mono">About</a>
      <a class="link link-hover font-mono">Catalog</a>
      <a class="link link-hover font-mono">Contact</a>
      <a class="link link-hover font-mono">Blog</a>
    </div>
    <div>
      <div class="grid grid-flow-col gap-4">
        <a class="btn btn-ghost btn-circle">
          <font-awesome-icon :icon="['fab', 'instagram']" size="2x"></font-awesome-icon>
        </a>
        <a class="btn btn-ghost btn-circle">
          <font-awesome-icon :icon="['fab', 'github']" size="2x"></font-awesome-icon>
        </a>
      </div>
    </div>
    <div>
      <p class="font-mono">Copyright © {{ currentYear }} - Made with ❤️ by nerds, for nerds</p>
      <p class="text-xs opacity-60 font-mono mt-2">console.log("Built with Vue.js + Tailwind + DaisyUI")</p>
    </div>
  </footer>
</template>
<script setup lang="ts">
import { FontAwesomeIcon } from "@fortawesome/vue-fontawesome";

const currentYear = new Date().getFullYear()
</script>