<template>
     <header class="bg-gray-800 text-white p-4">
          <div class="container mx-auto flex justify-between items-center">
               <h1 class="text-xl font-bold">
                    <NuxtLink to="/" class="hover:text-gray-300">
                         My Todo App
                    </NuxtLink>
               </h1>
               <nav>
                    <NuxtLink to="/todo" class="text-gray-200 hover:text-gray-300 mx-3">
                         Todo
                    </NuxtLink>
               </nav>
          </div>
     </header>
</template>

<script setup lang="ts">
// This component doesn't require any special script setup now,
// but you can add any necessary imports or logic in the future.
</script>

<style scoped>
/* You can add additional styles here if needed */
</style>