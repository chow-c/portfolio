<template>
  <v-card
    max-width="379"
    justify="center"
    hover
    v-bind:style="[
      {
        transform: 'rotate(' + getRotation(idx, 2.5) + 'deg)',
      },
    ]"
    @click="selected = !selected"
    :ripple="false"
  >
    <v-responsive :aspect-ratio="0.83">
      <v-img
        :src="getImgUrl(item.img)"
        class="mx-5 mt-5"
        aspect-ratio="1"
      ></v-img>
      <v-card-title class="text-center justify-center">{{
        item.title
      }}</v-card-title>
      <v-card-subtitle class="text-center">{{ item.text }}</v-card-subtitle>
    </v-responsive>
    <v-expand-transition>
      <v-sheet
        v-if="selected"
        class="
          transition-fast-in-fast-out
          v-card--reveal
          pa-3
          d-flex
          flex-column
          justify-center
        "
        style="height: 100%"
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
</template>

<script>
export default {
  name: "Polaroid",
  props: ["item", "idx"],
  data: () => ({
    selected: false,
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
};
</script>

<style scoped>
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