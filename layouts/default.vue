<template>
  <v-layout class="rounded rounded-md">
    <v-app-bar color="black">
      <v-app-bar-title class="text-white mx-8" to="/">
        Marvel
      </v-app-bar-title>
      <NuxtLink to="/">
        <v-btn class="mx-5" variant="flat" color="red">Home</v-btn>
      </NuxtLink>
      <NuxtLink to="/characters">
        <v-btn class="mx-5" variant="flat" color="red">Characters</v-btn>
      </NuxtLink>
    </v-app-bar>
    <v-main class="d-flex align-center justify-center" style="min-height: 300px;">
      <slot/>
    </v-main>
  </v-layout>
</template>