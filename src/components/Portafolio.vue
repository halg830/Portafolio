<script setup>
import logoJs from '../assets/logo_js.png'
import logoVue from '../assets/logo_vue.png'
import logoPython from '../assets/logo_python.png'
import logoSql from '../assets/logo_sql.png'
import logoMongoDB from '../assets/logo_mongoDB.png'
import logoFlutter from '../assets/logo_flutter.png'
import iconVeterinaria from '../assets/icon_veterinaria.png'
import iconTransporte from '../assets/icon_transporte.png'
import iconPokedex from '../assets/icon_pokedex.png'
import pdfCurriculum from '../assets/Curriculum_Hector_Aguilar.pdf'
import foto from '../assets/fotoc.png'

const habilidades = [
  {
    img: logoJs,
    nombre: "JAVASCRIPT",
  },
  {
    img: logoVue,
    nombre: "VUE",
  },
  {
    img: logoPython,
    nombre: "PYTHON",
  },
  {
    img: logoSql,
    nombre: "SQL",
  },
  {
    img: logoMongoDB,
    nombre: "MongoDB",
  },
  {
    img: logoFlutter,
    nombre: "FLUTTER",
  },
];

const proyectos = [
  { nombre: "Veterinaria", img: iconVeterinaria, link: { deploy: "https://halg830.github.io/proyectosSena.github.io/Proyectos/Veterinaria/index.html", gitHub: "https://github.com/halg830/proyectosSena.github.io/tree/main/Proyectos/Veterinaria" }, descripcion: "Uno de mis proyectos (realizado en JavaScript puro), para la programación de citas de una clínica veterinaria." },
  { nombre: "Transportes", img: iconTransporte, link: { deploy: "https://transporte-frontend.onrender.com", frontend: "https://github.com/halg830/TransporteBackend", backend: "https://github.com/halg830/TransporteBackend" }, descripcion: "Un proyecto para administrar y generar tickets de una terminal de buses (realizado con Vue.js, Axios, Pinia y Quasar)." },
  { nombre: "Pokedex", img: iconPokedex, link: { deploy: "https://pokedex-wof5.onrender.com", frontend: "https://github.com/halg830/apiPoquemon", backend: "https://pokeapi.co" }, descripcion: "En esta pokedex se pueden observar todos los pokemones registrados en pokeapi.com, permitiendo filtrarlos y buscarlos por su nombre (realizado con Vue.js y Axios)." },
];

const perfiles = [{ img: '', link: '' }]

function mostrarPDF() {
  window.open(pdfCurriculum, '_blank');
}
</script>

<template>
  <main>
    <section id="sectionPresentacion">
      <img :src="foto" alt="Foto" id="foto"/>
      <article id="presentacion">
        <h1>Hola!!</h1>
        <h1>Soy Héctor Aguilar</h1>
        <h1>Desarrollador Full Stack</h1>
      </article>
    </section>
    <section id="sectionSobreMi">
      <article id="artSobreMi">
        <h2>Sobre mí</h2>
        <h4>¿Quién soy?</h4>
        <p>
          Soy un desarrollador de software apasionado y comprometido, dedicado a
          enfrentar desafíos y encontrar soluciones efectivas. Mi enfoque se
          centra en la resolución de problemas, utilizando habilidades
          analíticas y creativas para superar obstáculos y lograr resultados
          satisfactorios.
        </p>
        <q-btn @click="mostrarPDF">Descargar CV</q-btn>
      </article>
      <article id="artHabilidades">
        <h2 style="padding: 30px;">Mis habilidades</h2>
        <div id="habilidades">
          <!-- Cuando pase el mouse por encima que el se muestre una barra de progreso -->
          <div v-for="(h, i) in habilidades" :key="i" class="habilidad">
            <img :src="h.img" alt="" />
            <span>{{ h.nombre }}</span>
          </div>
        </div>
      </article>
    </section>
    <section id="sectionProyectos">
      <h2>Proyectos</h2>
      <article id="secProyectos">
        <div class="card" v-for="proyecto in proyectos" :key="proyecto.link">
          <div class="icon">
            <img :src="proyecto.img" alt="icon proyecto" style="height:40px; width:40px" />
          </div>
          <strong> {{ proyecto.nombre }}
          </strong>
          <div class="card__body">
            {{ proyecto.descripcion }}
          </div>

          <div class="btnOpciones">
            <a :href="proyecto.link.deploy" class="links" target="_blank"><q-btn>Deploy</q-btn></a>
            <a :href="proyecto.link.gitHub" v-if="proyecto.link.gitHub" class="links"
              target="_blank"><q-btn>GitHub</q-btn></a>
            <div v-else class="contLinks">
              <a :href="proyecto.link.frontend" class="links" target="_blank"><q-btn>Frontend</q-btn></a>
              <a :href="proyecto.link.backend" class="links" target="_blank"><q-btn>Backend</q-btn></a>
            </div>
          </div>
        </div>
      </article>
    </section>
    <footer>
      <a href="perfil.link" target="_blank" rel="noopener noreferrer" v-for="(perfil, i) in perfiles" :key="i">
        <img :src="perfil.img" />
      </a>
    </footer>
  </main>
</template>

<style scoped>
#sectionPresentacion {
  display: flex;
  min-height: 90vh;
  justify-content: space-evenly;
  align-items: center;
  /* background-color: #f4f4f4; */
  /* box-shadow: 10px black; */
}

#foto{
  margin-bottom: 30px;
  border-radius: 100%;
  border: 3px solid black;
  background-color: rgb(0, 225, 255);
}

#presentacion>h1 {
  font-size: 5vw;
  margin: 30px
}

#sectionSobreMi {
  display: grid;
  grid-template-columns: 43% 57%;
}

#artSobreMi {
  display: flex;
  flex-direction: column;
  align-items: flex-start;
  justify-content: center;
  padding: 10px 40px;
  margin-top: 50px;
}

#artSobreMi>h2 {
  margin: 20px 10px;
}

#artSobreMi>h4 {
  margin: 20px 10px;
}

#artHabilidades {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  flex-grow: 1;
}

#habilidades {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
}

.habilidad {
  display: flex;
  flex-direction: column;
  padding: 10px;
  text-align: center;
  margin: 10px
}

.habilidad:hover {
  transform: scale(1.2);
  /* background-color: #f4f4f4; */
}

.habilidad>img {
  height: 80px;
  margin-bottom: 5px;
}

#sectionProyectos {
  padding: 40px;
  display: flex;
  flex-direction: column;
  align-items: center;
}

#secProyectos {
  display: flex;
  flex-direction: row;
  flex-wrap: wrap;
  gap: 20px;
}

#secProyectos>* {
  width: 400px;
}

.card {
  --bg: #f7f7f8;
  --hover-bg: #FFE5F4;
  --hover-text: #E50087;
  max-width: 35ch;
  text-align: left;
  background: var(--bg);
  padding: 1.5em;
  padding-block: 1.8em;
  border-radius: 5px;
  position: relative;
  overflow: hidden;
  transition: .3s cubic-bezier(.6, .4, 0, 1), transform .15s ease;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  gap: 1em;
}

.card__body {
  color: #464853;
  line-height: 1.5em;
  font-size: 1em;
}

.card> :not(a) {
  transition: .3s cubic-bezier(.6, .4, 0, 1);
}

.card> :not(button) {
  transition: .3s cubic-bezier(.6, .4, 0, 1);
}

.card>strong {
  display: block;
  font-size: 1.4rem;
  letter-spacing: -.035em;
}

.card .btnOpciones {
  position: absolute;
  inset: 0;
  width: 10%;
  height: 10%;
  display: flex;
  justify-content: center;
  border-radius: 5px;
  font-weight: bold;
  top: 100%;
  transition: all .3s cubic-bezier(.6, .4, 0, 1);
  gap: 10px;
  flex-wrap: wrap;
}

.card:hover .btnOpciones {
  opacity: 100;
  top: 35%;
  left: 45%;
  font-size: 1.2em;
}

.card:hover {
  background: #eeeeee;
}

.card:hover>div,
.card:hover>strong {
  opacity: 0;
}

.contLinks {
  display: flex;
}

.links {
  text-decoration: none;
}

@media (max-width:800px) {
  #sectionPresentacion {
    flex-direction: column;
    justify-content: center;
    padding-top: 20px;
  }

  #presentacion>h1 {
    font-size: 7vw;
    margin: -30px;
  }

  #sectionSobreMi {
    grid-template-columns: 100%;
  }

  #artSobreMi {
    margin-top: 0;
  }

  #secProyectos {
    justify-content: center;
  }
}
</style>