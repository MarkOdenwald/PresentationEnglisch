<template>
  <div class="fill-height">
    <v-layout>
      <v-app-bar>
        <template #prepend>
          <v-img src="../assets/vue-js-logo-png-transparent-png.png" />
        </template>
        <v-app-bar-title>
          <template #prepend>
            <v-img src="../assets/vue-js-logo-png-transparent-png.png" />
          </template>
          English Presentation
        </v-app-bar-title>
        <v-spacer />
        <v-btn icon @click="changeIconColor">
          <v-icon :style="{ color: iconColor }">mdi-heart</v-icon>
        </v-btn>
        <v-btn icon>
          <v-icon>mdi-dots-vertical</v-icon>
        </v-btn>
      </v-app-bar>
      <v-main>
        <v-card
          class="mt-4 mx-4 mr-4 d-flex align-center justify-center"
          height="100px"
        >
          <h1>Welcome to my website about Vue 3</h1>
        </v-card>
        <v-card class="mt-4 mx-4 mr-4">
          <v-card-title class="d-flex justify-center pb-0">
            <h2>Topics</h2>
          </v-card-title>
          <v-card-text class="d-flex align-center justify-center">
            <v-slide-group
              class="pa-4"
              next-icon="mdi-arrow-right"
              prev-icon="mdi-arrow-left"
              selected-class="bg-primary"
              show-arrows
            >
              <v-slide-group-item v-for="topic in topics" :key="topic.key">
                <v-card
                  class="ma-4 d-flex align-center justify-center justify-space-evenly"
                  color="grey-lighten-1"
                  height="400"
                  width="700"
                  image="../assets/greenBackground.jpg"
                  @click="openDialog(topic.title, topic.key)"
                >
                  <v-card-title>
                    <h2>{{ getTitle(topic.key) }}</h2>
                  </v-card-title>

                  <v-card-subtitle
                    ><h3>{{ topic.subtitle }}</h3></v-card-subtitle
                  >
                </v-card>
              </v-slide-group-item>
            </v-slide-group>
          </v-card-text>
        </v-card>
      </v-main>
    </v-layout>

    <topicDialog
      v-if="dg_topic.show"
      :dialog-title="dg_topic.title"
      :dialog-topic-key="dg_topic.key"
      @close="dg_topic.show = false"
    />
  </div>
</template>

<script>
import topicDialog from "./topicDialog.vue";

export default {
  components: {
    topicDialog,
  },
  data() {
    return {
      topics: [
        {
          title: "VueBasics",
          subtitle: "An introduction to Vue 3.",
          key: 1,
        },
        {
          title: "Vuetify",
          subtitle: "An introduction to Vuetify.",
          key: 2,
        },
        {
          title: "FirstSteps",
          subtitle: "How to create your first project.",
          key: 3,
        },
        {
          title: "Benefits",
          subtitle: "Why you should use Vue with Vuetify.",
          key: 4,
        },
      ],
      dg_topic: {
        show: false,
        title: null,
        key: null,
      },
      iconColor: "#FFFFFF",
    };
  },
  methods: {
    openDialog(title, key) {
      this.dg_topic.show = true;
      this.dg_topic.title = title;
      this.dg_topic.key = key;
    },
    getTitle(key) {
      if (key === 1) return "Vue Basics";
      if (key === 2) return "Vuetify";
      if (key === 3) return "First Steps";
      if (key === 4) return "Benefits";
    },
    changeIconColor() {
      this.iconColor = `#${Math.floor(Math.random() * 16777215).toString(16)}`;
    },
  },
};
</script>
