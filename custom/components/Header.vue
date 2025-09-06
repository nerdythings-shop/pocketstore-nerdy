<template>
  <header
      class="w-full mb-3 flex flex-col md:flex-row items-center justify-between px-6 py-4 bg-gradient-to-r from-purple-700 via-indigo-900 to-blue-800 shadow-xl">
    <div class="flex items-center gap-3">
      <a href="/">
        <img src="/nerdy-logo-symbol.svg" alt="Logo NerdyThings.shop" class="h-16 px-3 py-3 bg-white rounded-lg"/>
      </a>
      <a href="/">
        <span class="text-white text-lg font-bold">NerdyThings.shop</span>
      </a>
    </div>

    <nav class="flex items-center gap-6 mt-4 md:mt-0">
      <ul class="menu menu-horizontal bg-transparent p-0">
        <li class="md:hidden">
          <button class="text-white hover:bg-cyan-700 hover:text-white transition-colors">
            <FontAwesomeIcon size="1x" :icon="faBars"/>
            <span class="font-bold">Navigation</span>
          </button>
        </li>
        <li>
          <a href="/de/search" class="text-white hover:bg-cyan-700 hover:text-white transition-colors">
            <FontAwesomeIcon size="1x" :icon="faMagnifyingGlass"/>
            <span class="font-bold">Suche</span>
          </a>
        </li>
        <li>
          <a href="/de/categories" class="text-white hover:bg-cyan-700 hover:text-white transition-colors">
            <FontAwesomeIcon size="1x" :icon="faBoxes"/>
            <span class="font-bold">Kategorien</span>
          </a>
        </li>
      </ul>
    </nav>
  </header>
</template>

<script setup lang="ts">
import {FontAwesomeIcon} from '@fortawesome/vue-fontawesome'
import {faMagnifyingGlass, faBoxes, faBars} from '@fortawesome/free-solid-svg-icons'
</script>