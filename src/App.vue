<script setup>
import { ref } from "vue";
</script>

<template>
  <q-layout view="hHh lpR fFf">
    <q-header elevated class="bg-primary text-white">
      <q-toolbar>
        <q-toolbar-title> &lt;HLAG /&gt; </q-toolbar-title>
        <q-tabs align="left">
          <q-btn flat color="danger" label="holav" href="#contenedor"/>
          <q-btn flat color="danger" label="hola" href="#contenedor"/>
          <q-btn flat color="danger" label="hola" href="#contenedor"/>
        </q-tabs>
      </q-toolbar>
    </q-header>

    <q-page-container >
      <div style="height: 150vh;"><h1>h</h1></div>
      <div id="contenedor" style="height: 100vh"><h1>2</h1></div>
      <router-view />
    </q-page-container>
  </q-layout>
</template>

<style scoped></style>
