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
  }),
};
</script>
