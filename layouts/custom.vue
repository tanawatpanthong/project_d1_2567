<template>
    <v-layout class="rounded rounded-md" color="grey-darken-4">
      <v-app-bar color="surface-variant" title="Application bar"></v-app-bar>
  
      <v-navigation-drawer color="grey-darken-4">
        <v-list>
          <v-list-item ></v-list-item>
        </v-list>
      </v-navigation-drawer>
  
      <v-navigation-drawer location="right" color="grey-darken-4">
        <v-list>
          <v-list-item ></v-list-item>
        </v-list>
      </v-navigation-drawer>
  
      <v-main class="d-flex align-center justify-center" style="min-height: 300px; color: aqua; background-color:darkgray;" >
        <NuxtPage color: aqua; />
    
      </v-main>
    </v-layout>
  </template>