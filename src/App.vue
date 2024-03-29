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
                    user behaviours using my blend of
                    <span class="data-sci highlight">data science</span>,
                    <span class="software-dev highlight"
                      >software engineering</span
                    >, and <span class="design highlight">design</span> skills.
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
                    <Polaroid :idx="idx" :item="item" />
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
import Polaroid from "@/components/Polaroid.vue";

export default {
  name: "App",

  components: { Polaroid },

  data: () => ({
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
          "Office Add-in web app to intuitively report suspicious messages and inspect email header fields such as DMARC values and originating IPs. Developed with Office JavaScript and Microsoft Graph APIs, hosted on AWS, and deployed centrally via O365 Admin Center to 16,000 users across Windows, MacOS, Web, iOS, and Android clients. Progress was personally briefed up to CISO.",
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
        id: 8,
        title: "The Short Life of a Secret",
        text: "Learning experience web app",
        img: "short-life-secret",
        categories: ["design", "swe", "writing", "pm", "cyber"],
        description:
          "Designed and developed an in-browser web app to educate users about passphrase security. Interactivity built around a narrative written by a colleague, and leveraged Dropbox's zxcvbn and the Pwned Passwords API.",
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
        id: 6,
        title: "ANU Human-Centred Computing Workshop",
        text: "Interactive outreach web app",
        img: "hcc-workshop",
        categories: ["design", "pm", "swe", "privacy", "cyber", "writing"],
        description:
          "Developed Django and JavaScript web app containing interactive learning experiences which showcased areas of computer science research at The Australian National University. Managed deployment, administration, and security of build pipeline and VPS hosting.",
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

.highlight {
  background-size: 110% 60%;
  background-position: 100% 90%;
  transition: background-size 0.25s ease-in;
  font-weight: 500;
}

.highlight:hover {
  background-size: 100% 250%;
  color: black;
  text-shadow: none;
}

.data-sci {
  background-image: linear-gradient(
    0,
    rgba(5, 166, 107, 0.4) 50%,
    transparent 50%
  );
}
.software-dev {
  background-image: linear-gradient(
    0,
    rgba(242, 107, 107, 0.4) 50%,
    transparent 50%
  );
}
.design {
  background-image: linear-gradient(
    0,
    rgba(91, 181, 217, 0.4) 50%,
    transparent 50%
  );
}
</style>