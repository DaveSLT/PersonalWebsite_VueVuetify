<template>
  <v-app>
    <!-- App Bar -->
    <v-app-bar app elevation="1" color="light-pink">
      <v-app-bar-nav-icon
        @click="drawer = !drawer"
        class="d-flex d-sm-none"
      ></v-app-bar-nav-icon>
      <v-app-bar-title class="text-h5 font-weight-bold">Dave Salte</v-app-bar-title>
      <v-spacer></v-spacer>
      <v-btn
        v-for="item in menuItems"
        :key="item.title"
        :href="item.href"
        text
        class="text-none text-subtitle-1 d-none d-sm-flex"
      >
        {{ item.title }}
      </v-btn>
    </v-app-bar>

    <!-- Navigation Drawer -->
    <v-navigation-drawer v-model="drawer" temporary>
      <v-list>
        <v-list-item
          v-for="item in menuItems"
          :key="item.title"
          :href="item.href"
          @click="drawer = false"
        >
          <v-list-item-title>{{ item.title }}</v-list-item-title>
        </v-list-item>
      </v-list>
    </v-navigation-drawer>

    <v-main>
      <!-- Introduction Section -->
      <v-container
        fluid
        id="home"
        class="section-intro"
        style="background-color: #ffe4e1; min-height: 100vh"
      >
        <v-row align="center" justify="center" style="min-height: 100vh">
          <v-col cols="12" md="8" class="text-center">
            <v-avatar size="200" class="mb-4 float-animation">
              <v-img :src="daveImage" alt="Dave Jason B. Salte"></v-img>
            </v-avatar>
            <h1 class="text-h2 font-weight-bold mb-4" style="color: #333">
              Dave Jason B. Salte
            </h1>
            <span
              class="text-h5 typing"
              style="
                color: #666;
                margin-top: 20px;
                height: 20px;
                width: 100%;
                margin-bottom: 30px;
              "
            ></span>
            <br />

            <v-btn
              size="x-large"
              color="gold"
              href="#contact"
              elevation="2"
              class="text-none"
            >
              Get In Touch
            </v-btn>
          </v-col>
        </v-row>
      </v-container>

      <!-- Skills Section -->
      <v-container id="skills" class="py-12 my-12">
        <h2
          class="techt text-h3 mb-6 text-center font-weight-bold pt-12"
          style="color: #333"
        >
          Technical Expertise
        </h2>
        <v-row>
          <v-col v-for="skill in skills" :key="skill.name" cols="12" sm="6" md="4">
            <v-hover v-slot="{ isHovering, props }">
              <v-card
                v-bind="props"
                :elevation="isHovering ? 8 : 2"
                :class="{ 'on-hover': isHovering }"
                height="100%"
                class="wow"
              >
                <v-card-title class="text-h5 techmagic">
                  <v-icon
                    :icon="skill.icon"
                    size="large"
                    color="light-pink"
                    class="mr-2"
                  ></v-icon>
                  {{ skill.name }}
                </v-card-title>
                <v-card-text class="text-body-1 techmagic1">{{
                  skill.description
                }}</v-card-text>
              </v-card>
            </v-hover>
          </v-col>
        </v-row>
      </v-container>

      <!-- Testimonials Section -->
      <v-container id="testimonials" class="py-12 testimonial-section">
        <h2
          class="text-h3 mb-6 text-center font-weight-bold testimonial"
          style="color: #333"
        >
          Testimonials
        </h2>
        <v-row class="testimonial-container">
          <v-col
            v-for="testimonial in testimonials"
            :key="testimonial.name"
            cols="12"
            md="6"
          >
            <v-card elevation="4" class="testimonial-card">
              <v-card-text>
                <v-row no-gutters align="center" class="mb-4 testimonial-head">
                  <v-avatar size="48" class="mr-4">
                    <v-img :src="testimonial.avatar" :alt="testimonial.name"></v-img>
                  </v-avatar>
                  <v-card-title class="text-h6 pa-0">{{ testimonial.name }}</v-card-title>
                </v-row>
                <v-card-text class="text-body-1 font-italic testimonial-feedback">
                  "{{ testimonial.feedback }}"
                </v-card-text>
              </v-card-text>
            </v-card>
          </v-col>
        </v-row>
      </v-container>

      <!-- Projects Section -->
      <v-container id="projects" class="py-12" style="background-color: #fdf5e6">
        <h2 class="text-h3 mb-6 text-center font-weight-bold mt-8" style="color: #333">
          Featured Projects
        </h2>
        <v-row>
          <v-col v-for="project in projects" :key="project.title" cols="12" md="6">
            <v-hover v-slot="{ isHovering, props }">
              <v-card v-bind="props" :elevation="isHovering ? 12 : 2" height="100%">
                <v-img :src="project.image" height="250" cover></v-img>
                <v-card-title class="text-h5">{{ project.title }}</v-card-title>
                <v-card-text class="text-body-1">{{ project.description }}</v-card-text>
                <v-card-text>
                  <v-chip
                    v-for="tech in project.technologies"
                    :key="tech"
                    class="mr-2 mb-2"
                    color="light-pink"
                    text-color="white"
                  >
                    {{ tech }}
                  </v-chip>
                </v-card-text>
                <v-card-actions>
                  <v-btn
                    :href="project.link"
                    target="_blank"
                    color="light-pink"
                    variant="tonal"
                    class="text-none"
                  >
                    View Project
                  </v-btn>
                </v-card-actions>
              </v-card>
            </v-hover>
          </v-col>
        </v-row>
      </v-container>

      <!-- Contact Section -->
      <v-container id="contact" class="py-12">
        <h2 class="text-h3 mb-6 text-center font-weight-bold" style="color: #333">
          Get In Touch
        </h2>
        <v-row justify="center">
          <v-col cols="12" md="8" class="text-center">
            <p class="text-h5 mb-6">
              Feel free to contact me through the following platforms:
            </p>
            <v-row justify="center">
              <v-col cols="12" sm="6" class="d-flex justify-center">
                <v-btn
                  href="mailto:davejasonbulan2003@gmail.com"
                  color="light-pink"
                  size="large"
                  class="text-none"
                  elevation="2"
                  target="_blank"
                >
                  <v-icon left class="mr-2">mdi-email</v-icon>
                  Email Me
                </v-btn>
              </v-col>
              <v-col cols="12" sm="6" class="d-flex justify-center">
                <v-btn
                  href="https://www.facebook.com/AccuSiDave"
                  color="light-pink"
                  size="large"
                  class="text-none"
                  elevation="2"
                  target="_blank"
                >
                  <v-icon left class="mr-2">mdi-facebook</v-icon>
                  Contact via Facebook
                </v-btn>
              </v-col>
            </v-row>
          </v-col>
        </v-row>
      </v-container>
    </v-main>

    <!-- Footer -->
    <v-footer
      app
      class="d-flex justify-center text-center py-4"
      style="background-color: #ffebcd"
    >
      <span class="text-dark">
        &copy; {{ new Date().getFullYear() }} Dave Salte. All rights reserved.
      </span>
    </v-footer>
  </v-app>
</template>

<script>
import { nextTick } from "vue";
import Typed from "typed.js";
import ScrollReveal from "scrollreveal";

export default {
  name: "App",

  mounted() {
    // Wait for the DOM to finish updating with Vue's `nextTick`
    nextTick(() => {
      const element = document.querySelector(".typing");
      if (element) {
        // Typed.js for typing animations
        new Typed(".typing", {
          strings: [
            "Full Stack Developer",
            "Project Manager",
            "Software Engineer",
            "Web Designer",
          ],
          loop: true,
          typeSpeed: 120,
          backSpeed: 80,
          backDelay: 2000,
        });
      } else {
        console.error("Element with class 'typing' not found.");
      }
    });

    /* ----- ## -- SCROLL REVEAL ANIMATION -- ## ----- */
    const sr = ScrollReveal({
      origin: "top",
      distance: "80px",
      duration: 2000,
      reset: true,
    });

    sr.reveal("#home", { delay: 100 });
    sr.reveal("#projects", { delay: 200 });
    sr.reveal("#testimonials", { delay: 100 });
    sr.reveal(".testimonial", { delay: 250 });
    sr.reveal(".testimonial-card", { delay: 400 });
    sr.reveal(".techt", { delay: 200 });
    sr.reveal(".wow", { delay: 200 });

    const srLeft = ScrollReveal({
      origin: "left",
      distance: "80px",
      duration: 2000,
      reset: true,
    });

    srLeft.reveal(".techmagic", { delay: 350 });
    srLeft.reveal(".techmagic1", { delay: 550 });
    srLeft.reveal(".testimonial-head", { delay: 550 });
    srLeft.reveal(".testimonial-feedback", { delay: 750 });

    const srRight = ScrollReveal({
      origin: "bottom",
      distance: "80px",
      duration: 2000,
      reset: true,
    });

    srRight.reveal("#contact", { delay: 200 });
  },
};
</script>

<script setup>
import { ref } from "vue";
import daveImage from "@/IMG/dave1.jpg";
import amazonImg from "@/IMG/amazon.jpg";
import taskManagementImg from "@/IMG/TMS.png";
import billy1 from "@/IMG/billy1.jpg";
import andre1 from "@/IMG/andre1.jpg";
import kurt1 from "@/IMG/kurt1.jpg";
import aedrian1 from "@/IMG/aedrian1.jpg";

const drawer = ref(false);

const menuItems = [
  { title: "Home", href: "#home" },
  { title: "Skills", href: "#skills" },
  { title: "Projects", href: "#projects" },
  { title: "Contact", href: "#contact" },
];

const skills = [
  {
    name: "Java",
    icon: "mdi-language-java",
    description: "Enterprise-level application development and Android app creation",
  },
  {
    name: "HTML",
    icon: "mdi-language-html5",
    description: "Semantic markup and structure for web applications",
  },
  {
    name: "CSS",
    icon: "mdi-language-css3",
    description: "Responsive design and modern layout techniques",
  },
  {
    name: "Vue.js",
    icon: "mdi-vuejs",
    description: "Building scalable and interactive user interfaces",
  },
  {
    name: "Vuetify",
    icon: "mdi-vuetify",
    description: "Creating beautiful Material Design applications",
  },
  {
    name: "JavaScript",
    icon: "mdi-language-javascript",
    description: "Dynamic client-side scripting and server-side development",
  },
];

const testimonials = ref([
  {
    name: "Billy Terante",
    feedback: "Dave's work is outstanding!",
    avatar: billy1,
  },
  {
    name: "Andre Salvador",
    feedback: "Highly skilled developer and team player.",
    avatar: andre1,
  },
  {
    name: "kurt Reserva",
    feedback: "Exceptional problem-solving skills and attention to detail.",
    avatar: kurt1,
  },
  {
    name: "Aedrian Puspus",
    feedback: "Dave consistently delivers high-quality code on time.",
    avatar: aedrian1,
  },
]);

const projects = [
  {
    title: "E-commerce Platform",
    description:
      "A full-stack e-commerce solution with a responsive front-end and robust back-end",
    image: amazonImg,
    link: "#",
    technologies: ["Vue.js", "Vuetify", "Java Spring Boot", "MySQL"],
  },
  {
    title: "Task Management System",
    description:
      "An intuitive task management application with real-time updates and team collaboration features",
    image: taskManagementImg,
    link: "#",
    technologies: ["Vue.js", "Vuetify", "Node.js", "MongoDB"],
  },
];
</script>

<style scoped>
.typing-h5 {
  font-size: 1.25rem; /* Match h5 size */
  font-weight: 500; /* Semi-bold to align with h5 styling */
}

.v-card {
  transition: all 0.3s ease-in-out;
}

.v-card.on-hover {
  transform: translateY(-5px);
}
.testimonial-section {
  background: linear-gradient(to right, #ffe4e1, #ffebcd);
}

.testimonial-container {
  max-height: 600px;
  overflow-y: auto;
  padding-right: 16px;
}

.testimonial-card {
  transition: box-shadow 0.3s ease-in-out;
}

.testimonial-card:hover {
  box-shadow: 0 8px 16px rgba(0, 0, 0, 0.2) !important;
}
@keyframes float {
  0%,
  100% {
    transform: translateY(0);
  }
  50% {
    transform: translateY(-5px); /* Adjust this value for the desired "raise" effect */
  }
}

.float-animation {
  animation: float 3s ease-in-out infinite;
}

/* Scrollbar Styles */
.testimonial-container::-webkit-scrollbar {
  width: 8px;
}

.testimonial-container::-webkit-scrollbar-track {
  background: #ffe4e1;
}

.testimonial-container::-webkit-scrollbar-thumb {
  background-color: #ffa07a;
  border-radius: 20px;
  border: 2px solid #ffe4e1;
}

.testimonial-container::-webkit-scrollbar-thumb:hover {
  background-color: #ff8c69;
}

/* For Firefox */
.testimonial-container {
  scrollbar-width: thin;
  scrollbar-color: #ffa07a #ffe4e1;
}
</style>
