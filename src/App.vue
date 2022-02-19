<template>
  <v-app>
    <v-main>
      <div id="app">
        <v-container fluid class="pa-0">
          <v-container fluid class="mt-4">
            <v-container class="my-md-10">
              <v-row class="mt-md-16">
                <v-col>
                  <h1
                    class="
                      text-h1
                      font-weight-black
                      mb-3
                      primary--text
                      text-center
                    "
                  >
                    Hello, I'm Chris.
                  </h1>
                </v-col>
              </v-row>
              <v-row>
                <v-col>
                  <p class="mt-10 text-h4 font-weight-light text-center">
                    I'm a technical analyst and program manager, specialising in
                    cyber security.
                  </p>
                  <p class="mt-10 text-h4 font-weight-light text-center">
                    I develop engaging and intuitive programs to drive safer
                    user behaviours using my blend of data science, software
                    engineering, and design skills.
                  </p>
                </v-col>
              </v-row>
            </v-container>
          </v-container>
          <v-container fluid style="background: #fff8ef" class="pt-15">
            <v-container class="text-center">
              <h3 class="text-h3">Project snapshots</h3>
              <p class="mt-5">
                Click for a summary. For more details, get in touch.
              </p>
              <v-row class="my-10 justify-center">
                <v-chip-group v-model="skills" column multiple>
                  <v-icon class="mx-3">mdi-filter-variant</v-icon>
                  <v-chip filter label value="cyber">cyber security</v-chip>
                  <v-chip filter label value="design">design</v-chip>
                  <v-chip filter label value="data">data science</v-chip>
                  <v-chip filter label value="pm">program management</v-chip>
                  <v-chip filter label value="swe">software engineering</v-chip>
                  <v-chip filter label value="writing"
                    >technical writing</v-chip
                  >
                  <v-chip filter label value="privacy">privacy</v-chip>
                </v-chip-group>
              </v-row>
              <v-row>
                <transition-group name="project-cards" class="row">
                  <v-col
                    v-for="(item, idx) in projects"
                    :key="item.id"
                    cols="12"
                    sm="4"
                    lg="4"
                    xl="4"
                    class="project-cards-item"
                  >
                    <v-card
                      max-width="379"
                      justify="center"
                      hover
                      v-bind:style="[
                        idx === selectedCard ? { elevation: 10 } : {},
                        {
                          transform: 'rotate(' + getRotation(idx, 2.5) + 'deg)',
                        },
                      ]"
                    >
                      <v-responsive
                        :aspect-ratio="0.83"
                        @click="selectedCard = idx"
                      >
                        <v-img
                          :src="getImgUrl(item.img)"
                          class="mx-5 mt-5"
                          aspect-ratio="1"
                        ></v-img>
                        <v-card-title class="text-center justify-center">{{
                          item.title
                        }}</v-card-title>
                        <v-card-subtitle class="text-center">{{
                          item.text
                        }}</v-card-subtitle>
                      </v-responsive>
                      <v-expand-transition>
                        <v-sheet
                          v-if="selectedCard === idx"
                          class="
                            transition-fast-in-fast-out
                            v-card--reveal
                            pa-3
                            d-flex
                            flex-column
                            justify-center
                          "
                          style="height: 100%"
                          @click="selectedCard = null"
                        >
                          <v-card-text class="pb-0 text-center">
                            <p class="text-h5 text--primary">
                              {{ item.title }}
                            </p>
                            <p class="text-body-1">{{ item.description }}</p>
                          </v-card-text>
                        </v-sheet>
                      </v-expand-transition>
                    </v-card>
                  </v-col>
                </transition-group>
              </v-row>
            </v-container>
          </v-container>
          <v-container>
            <v-container text-center>
              <v-icon class="mx-3">mdi-open-in-new</v-icon>
              <v-btn
                class="ma-1"
                color="primary"
                outlined
                v-for="(item, index) in socials"
                :key="index"
                :href="item.link"
                target="_blank"
              >
                {{ item.name }}
              </v-btn>
            </v-container>
          </v-container>
        </v-container>
      </div>
    </v-main>
  </v-app>
</template>

<script>
export default {
  name: "App",

  components: {},

  data: () => ({
    selectedCard: null,
    skills: [],
    socials: [
      {
        id: 1,
        name: "LinkedIn",
        link: "https://www.linkedin.com/in/chow-c/",
      },
      {
        id: 2,
        name: "GitHub",
        link: "https://github.com/chow-c",
      },
      {
        id: 3,
        name: "Google Scholar",
        link: "https://scholar.google.com/citations?hl=en&user=TNhT7zkAAAAJ",
      },
    ],
    all_projects: [
      {
        id: 1,
        title: "Inferring Implicit Relevance from Physiological Signals",
        text: "PhD thesis",
        img: "phd",
        categories: ["design", "data", "privacy", "pm", "swe", "writing"],
        description:
          "Researched whether artificial intelligence could infer someone's perceived relevance of information from their biometrics. Machine learning models could be useful for augmenting intelligence analysis by offering an element of objectivity to an inherently subjective task, and thus improve introspection and collaboration. Final results indicated performance was not commensurate to privacy risks.",
      },
      {
        id: 2,
        title: "Phishing Tacklebox",
        text: "Outlook add-in web app",
        img: "tacklebox",
        categories: ["design", "privacy", "cyber", "swe", "pm", "writing"],
        description:
          "Office Add-in web app to intuitively report suspicious messages and inspect email header fields such as DMARC values and originating IPs. Developed with Office JavaScript and Microsoft Graph APIs, hosted on AWS, and deployed centrally via O365 Admin Center to 30,000 users across Windows, MacOS, Web, iOS, and Android clients. Progress was personally briefed up to CISO.",
      },
      {
        id: 3,
        title: "Hall of Phame",
        text: "Phishing awareness program",
        img: "hall-of-phame",
        categories: [
          "design",
          "data",
          "privacy",
          "pm",
          "swe",
          "writing",
          "cyber",
        ],
        description:
          "Designed, developed, and managed a year-long phishing and malspam simulation teaching users about email-based threats. Involved customising phishing simulation software to model TTPs of different real-world threat actors each month. Results were personally briefed up to CISO.",
      },
      {
        id: 4,
        title: "Tail-gator",
        text: "Physical security poster campaign",
        img: "tailgator",
        categories: ["design", "pm"],
        description:
          "Designed simple slogan and graphic for posters placed at all points of entry to reinforce use of swipe passes.",
      },
      {
        id: 5,
        title: "IRAP training materials",
        text: "Australian Government policy",
        img: "irap",
        categories: ["writing", "cyber"],
        description:
          "Oversaw the technical qualification, training, and examination framework of the Australian Government's Information Security Registered Assessors Program from 2012-2018.",
      },
      {
        id: 6,
        title: "ANU Human-Centred Computing Workshop",
        text: "Interactive outreach web app",
        img: "hcc-workshop",
        categories: ["design", "pm", "swe", "privacy", "cyber", "writing"],
        description:
          "Developed Django and JavaScript web app containing interactive learning experiences which showcased areas of computer science research at The Australian National University. Managed deployment, administration, and security of build pipeline and VPS hosting.",
      },
      {
        id: 7,
        title: "Australasian Computer Science Week - ACSW 2016",
        text: "Conference program",
        img: "acsw",
        categories: ["design", "swe", "writing"],
        description:
          "Web chair for ACSW 2016, responsible for developing the web conference timetable and program using JavaScript. Designed the physical conference handout.",
      },
    ],
  }),
  methods: {
    getImgUrl: function (pic) {
      return require("@/assets/" + pic + ".png");
    },
    getRotation: function (idx, bound) {
      let direction = idx % 2 ? 1 : -1;
      return Math.random() * direction * bound;
    },
  },
  computed: {
    projects: function () {
      if (this.skills.length) {
        let searchValue = this.skills;
        return this.all_projects.filter(function (project) {
          return searchValue.some((r) => project.categories.includes(r));
        });
      } else {
        return this.all_projects;
      }
    },
  },
};
</script>

<style scoped>
.project-cards-item {
  transition: all 0.8s;
}

.project-cards-enter,
.project-cards-leave-to {
  opacity: 0;
  transform: translate(50%, 200%);
}
.project-cards-leave-active {
  position: absolute;
}

.v-card__title {
  word-break: normal !important;
}

.v-image__image {
  border: 0.5px solid grey;
}

.v-card--reveal {
  bottom: 0;
  opacity: 1 !important;
  position: absolute;
  width: 100%;
}
</style>