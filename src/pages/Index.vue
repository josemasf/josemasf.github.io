<template>
  <Layout>
    <div class="bg-content-background">
      <!-- about us -->
      <section id="about" class="flex-center h-full  m-auto border-b-4">
        <div class="flex-center flex-col container h-full m-auto">
          <div class="flex flex-col md:flex-row mx-8">
            <div class="flex flex-col items-center w-2/3 md:w-1/3 my-4 md:my-0 w-auto">
              <g-image src="~/assets/img/yo-gif.gif"
                class="w-1/2 md:w-auto"
                
              />
              <div class="flex flex-col items-center">
                <h2 class="font-medium mt-4 text-xl md:text-2xl">
                  {{ $static.metadata.author }}
                </h2>
                <p class="text-sm md:text-base">
                  Me gusta investigar, crear y formar.
                </p>
              </div>
            </div>
            <div
              class="flex-center border-t-1 md:border-t-0 border-l-0 md:border-l-1 w-auto md:w-2/3"
            >
              <p class="leading-relaxed text-base md:text-lg mx-auto md:mx-12 my-4 md:my-0">
                Arquitecto orientado al Frontend, aunque mis primeros 13 años laborales estuve desarrollando aplicaciones web con C#, por lo que tengo un alto conocimiento sobre arquitectura backend. <br /><br />

                Durante mi vida laboral he tenido la oportunidad de desarrollar tanto proyectos ecommerce como aplicaciones web para la gestión y administración de empresas. Tengo experiencia en integración de servicios de terceros para la obtención de datos o sincronizanción de servicios.<br /><br />

                Me considero una persona resolutiva e implicada en cada una de las tareas que realizo en mi día a día. Implicándome activamente en resolver problemas.<br /><br />

                Tengo mucha curiosidad en investigar nuevas arquitecturas y técnicas modernas, intentando aplicarlas en mi día a día o haciendo pruebas de concepto personales para poder profundizar en su estudio.<br /><br />

                Me gusta aprender y enseñar lo aprendido siempre que tengo ocasión<br />
              </p>
            </div>
          </div>
        </div>
      </section>
      <!-- experiences -->
      <section id="experiences" class="flex-center h-full  m-auto border-b-4">
        <div class="flex-center flex-col container h-full m-auto">
          <div
            class="flex relative py-6 md:py12 md:w-2/3 m-auto"
            v-for="edge in $page.allExperiences.edges"
            :key="edge.node.id"
          >
            <div class="flex-center w-18 md:w-28 h-full absolute inset-0">
              <div class="h-full w-1 bg-current pointer-events-none"></div>
            </div>
            <div
              class="flex-center-items flex-shrink-0 w-18 h-18 md:w-28 md:h-28 rounded-full bg-content-highlight z-1"
            >
              <div
                class="flex flex-col text-center leading-none text-xs md:text-base font-weight-500"
              >
                <span>{{ edge.node.from }}</span>
                <span>-</span>
                <span>{{ edge.node.to }}</span>
              </div>
            </div>
            <div class="flex flex-grow pl-4 md:pl-8 items-start">
              <div class="flex-grow mt-0 md:mt-6 pl-2 md:pl-8">
                <h2 class="font-medium text-base md:text-3xl mb-2 ">
                  {{ edge.node.company }}
                </h2>
                <div
                  class="leading-relaxed text-base md:text-lg prose"
                  v-html="edge.node.sumary"
                />
              </div>
            </div>
          </div>
        </div>
      </section>
      <!-- projects -->
      <section id="projects" class="flex-center h-full  m-auto border-b-4">
        <div class="flex-center flex-col container h-full m-auto">
          <div class="text-center w-full">
            <h1 class="font-medium text-base md:text-lg mb-4">
              Cosas que he construido
            </h1>
            <p
              class="mx-auto leading-relaxed text-xs md:text-base lg:w-2/3 mb-4"
            >
              Estos son unos pocos proyectos que he realizado como prueba de concepto o encargo a terceros.
            </p>
          </div>
          <!-- each project -->
          <div class="flex-wrap flex-center">
            <div
              class="m-4 md:w-1/3 lg:w-1/4"
              v-for="edge in $page.allProjects.edges"
              :key="edge.node.id"
            >
              <div class="flex flex-row md:flex-col">
                <div
                  class="flex flex-col justify-start md:justify-center items-start md:items-center w-1/3 md:w-auto"
                >
                  <g-image
                    class="rounded-lg object-contain min-h-200px"
                    :src="edge.node.imgurl"
                    :alt="edge.node.title"
                  />
                  <div class="flex-center space-x-2 md:space-x-4 m-4">
                    <a
                      :href="edge.node.github"
                      target="_blank"
                      rel="noopener noreferrer"
                      title="Github"
                    >
                      <GithubIcon class="icon" />
                    </a>
                    <a
                      :href="edge.node.url"
                      target="_blank"
                      rel="noopener noreferrer"
                      :title="edge.node.title"
                    >
                      <OpenInNewIcon class="icon" />
                    </a>
                  </div>
                </div>
                <div class="ml-4 md:ml-0 w-auto">
                  <h2 class="font-medium text-base md:text-lg">
                    {{ edge.node.title }}
                  </h2>
                  <div
                    class="mx-auto leading-relaxed text-xs md:text-base prose"
                    v-html="edge.node.content"
                  />
                </div>
              </div>
            </div>
          </div>
        </div>
      </section>
      <!-- presentations -->
      <section id="presentations" class="flex-center h-full  m-auto border-b-4">
        <div class="flex-center flex-col container h-full m-auto">
          <div class="text-center w-full">
            <h1 class="font-medium text-base md:text-lg mb-4">
              Cosas de las que he hablado
            </h1>
            <p
              class="mx-auto leading-relaxed text-xs md:text-base lg:w-2/3 mb-4"
            >
              Algunas de las ponencias que he tenido la oportunidad de presentar en eventos coorporativos
            </p>
          </div>
          <!-- each presentation -->
          <div class="flex-center flex-wrap">
            <div
              class="m-4 md:w-1/3 lg:w-1/4"
              v-for="edge in $page.allPresentations.edges"
              :key="edge.node.id"
            >
              <div class="flex flex-row md:flex-col">
                <div
                  class="flex flex-col justify-start md:justify-center items-start md:items-center w-1/3 md:w-auto"
                >
                  <g-image
                    class="rounded-lg object-contain min-h-200px"
                    :src="edge.node.imgurl"
                    :alt="edge.node.title"
                  />
                  <div class="flex-center space-x-2 md:space-x-4 m-4">
                    <a
                      :href="edge.node.github"
                      target="_blank"
                      rel="noopener noreferrer"
                      title="Github"
                    >
                      <GithubIcon class="icon" />
                    </a>
                    <a
                      :href="edge.node.url"
                      target="_blank"
                      rel="noopener noreferrer"
                      :title="edge.node.title"
                    >
                      <OpenInNewIcon class="icon" />
                    </a>
                  </div>
                </div>
                <div class="ml-4 md:ml-0 w-auto">
                  <h2 class="font-medium text-base md:text-lg">
                    {{ edge.node.title }}
                  </h2>
                  <div
                    class="mx-auto leading-relaxed text-xs md:text-base"
                    v-html="edge.node.content"
                  />
                </div>
              </div>
            </div>
          </div>
        </div>
      </section>
      <!-- contact section -->
      <section id="contact" class="flex-center h-full  m-auto border-b-4">
        <div class="flex-center flex-col container h-full m-auto">
          <div>
            <div class="flex flex-col text-center w-full mb-4">
              <h1 class="font-medium text-base md:text-lg mb-4">
                Contacta conmigo
              </h1>
              
            </div>
            <div class="lg:w-1/2 md:w-2/3 mx-auto">
              <div class="flex flex-wrap">                
                <Social class="mt-4 w-full" />
              </div>
            </div>
          </div>
        </div>
      </section>
    </div>
  </Layout>
</template>

<page-query>
query {
  allExperiences(sortBy: "from", order: DESC) {
    edges {
      node {
        id
        company
        from
        to
        content
        sumary
      }
    }
  }
  allProjects(sortBy: "title", order: ASC) {
    edges {
      node {
        id
        title
        url
        github
        content
        imgurl
      }
    }
  }
  allPresentations(sortBy: "title", order: ASC) {
    edges {
      node {
        id
        title
        url
        github
        content
        imgurl
      }
    }
  }
}
</page-query>

<static-query>
query {
  metadata {
    author
  }
}
</static-query>

<script>
import GithubIcon from "vue-material-design-icons/Github"
import OpenInNewIcon from "vue-material-design-icons/OpenInNew"
import Social from "~/components/Social.vue"

export default {
  components: {
    GithubIcon,
    OpenInNewIcon,
    Social,
  },
}
</script>
