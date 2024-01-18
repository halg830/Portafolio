<script setup>
import {ref} from 'vue'
import Portafolio from "./components/Portafolio.vue";

const secciones = ref([{ label: "Inicio", id: "sectionPresentacion" }, { label: "Sobre Mí", id: "sectionSobreMi" }, {label: "Proyectos", id:'sectionProyectos'}])

function deshabilitarBtn(id){
  secciones.value.forEach(seccion=>seccion.disable=false)

  const indexSeccion = secciones.value.findIndex(seccion=>seccion.id===id)

  secciones.value[indexSeccion].disable = true
}
</script>

<template>
  <q-layout view="hHh lpR fFf">
    <q-header elevated class="bg-primary text-white">
      <q-toolbar>
        <q-toolbar-title> &lt;HECTOR /&gt; </q-toolbar-title>
        <q-tabs align="left" id="btnSecciones">
          <q-btn flat v-for="seccion in secciones" :key="seccion.id" color="danger" :label="seccion.label" :disable="seccion.disable"
            :href="'#' + seccion.id" class="secciones" @click="deshabilitarBtn(seccion.id)"/>
        </q-tabs>
      </q-toolbar>
    </q-header>

    <q-page-container>
      <Portafolio />
      <router-view />
    </q-page-container>
  </q-layout>
</template>

<style scoped>
.secciones:hover {
  background-color: rgb(0, 113, 188);

}
</style>
