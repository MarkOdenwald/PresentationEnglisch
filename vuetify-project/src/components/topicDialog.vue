<template>
  <div>
    <globalDialog :title="dialogTitle" @close="$emit('close')">
      <!-- Basics of Vue -->
      <div v-if="dialogTopicKey === 1">
        <div
          class="d-flex flex-column-right align-center justify-space-between pr-3 pb-4"
        >
          <v-card width="500px">
            <v-card-text>
              <v-row>
                <v-col cols="12" class="py-0">
                  <v-text-field
                    prepend-icon="mdi-nodejs"
                    variant="underlined"
                    readonly
                  >
                    Progressive Javascript Framework
                  </v-text-field>
                </v-col>
                <v-col cols="12" class="py-0">
                  <v-text-field
                    prepend-icon="mdi-api"
                    variant="underlined"
                    readonly
                  >
                    Composition/Options API
                  </v-text-field>
                </v-col>
                <v-col cols="12" class="py-0">
                  <v-text-field
                    prepend-icon="mdi-speedometer"
                    variant="underlined"
                    readonly
                  >
                    High Performance
                  </v-text-field>
                </v-col>
                <v-col cols="12" class="py-0">
                  <v-text-field
                    prepend-icon="mdi-react"
                    variant="underlined"
                    readonly
                  >
                    New Reactivity System
                  </v-text-field>
                </v-col>
                <v-col cols="12" class="py-0">
                  <v-text-field
                    prepend-icon="mdi-language-typescript"
                    variant="underlined"
                    readonly
                  >
                    Enhanced TypeScript support
                  </v-text-field>
                </v-col>
              </v-row>
            </v-card-text>
          </v-card>
          <div>
            <v-img src="../assets/new-vue-3-img-fi.webp" width="300px"> </v-img>
          </div>
        </div>
        <v-expansion-panels>
          <!------------------------------------ v-if ------------------------------------------------------------------------------------------>
          <v-expansion-panel>
            <v-expansion-panel-title>v-if</v-expansion-panel-title>
            <v-expansion-panel-text>
              <v-row>
                <v-col cols="1">
                  <v-switch v-model="switchState" inset color="primary">
                  </v-switch>
                </v-col>
                <v-col cols="11">
                  <v-alert
                    v-if="switchState"
                    text="The switch is true"
                    title="Success"
                    type="success"
                  ></v-alert>
                </v-col>
              </v-row>
            </v-expansion-panel-text>
          </v-expansion-panel>

          <!------------------------------------ v-for ------------------------------------------------------------------------------------------>

          <v-expansion-panel>
            <v-expansion-panel-title>v-for</v-expansion-panel-title>
            <v-expansion-panel-text>
              <v-row>
                <v-col>
                  <ul>
                    <li v-for="(item, index) in items" :key="index">
                      {{ item }}
                    </li>
                  </ul>
                </v-col>
              </v-row>
            </v-expansion-panel-text>
          </v-expansion-panel>

          <!------------------------------------ v-model ------------------------------------------------------------------------------------------>

          <v-expansion-panel>
            <v-expansion-panel-title>v-model</v-expansion-panel-title>
            <v-expansion-panel-text>
              <v-row>
                <v-col cols="12">
                  <v-text-field
                    class="pt-4"
                    label="Enter your name"
                    variant="outlined"
                    v-model="userName"
                  ></v-text-field>
                </v-col>
                <v-col>
                  <v-checkbox
                    v-model="isSubscribed"
                    label="Subscribe to newsletter"
                  ></v-checkbox>
                </v-col>
                <v-col>
                  <p>Your name: {{ userName }}</p>
                  <p>Subscribed: {{ isSubscribed ? "Yes" : "No" }}</p>
                </v-col>
              </v-row>
            </v-expansion-panel-text>
          </v-expansion-panel>

          <!------------------------------------ computed ------------------------------------------------------------------------------------------>

          <v-expansion-panel>
            <v-expansion-panel-title
              >computed properties</v-expansion-panel-title
            >
            <v-expansion-panel-text>
              <v-text-field
                variant="outlined"
                label="Enter your first name"
                v-model="firstName"
                class="pt-4"
              ></v-text-field>
              <v-text-field
                variant="outlined"
                label="Enter your last name"
                v-model="lastName"
              ></v-text-field>
              <p>Full Name: {{ fullName }}</p>
            </v-expansion-panel-text>
          </v-expansion-panel>

          <!------------------------------------ watcher ------------------------------------------------------------------------------------------>

          <v-expansion-panel>
            <v-expansion-panel-title>watcher</v-expansion-panel-title>
            <v-expansion-panel-text>
              <v-text-field
                label="Enter a number"
                v-model="number"
                type="number"
                variant="outlined"
                class="pt-4"
              ></v-text-field>
              <p>Square of the number: {{ squaredNumber }}</p>
            </v-expansion-panel-text>
          </v-expansion-panel>
        </v-expansion-panels>
      </div>

      <!-- Vuetify -->
      <div v-if="dialogTopicKey === 2">
        <div class="d-flex flex-column-right justify-space-between pr-8 mr-8">
          <v-card width="500px" elevation="9">
            <v-card-text>
              <v-row>
                <v-col cols="12" class="py-0">
                  <v-text-field
                    prepend-icon="mdi-material-design"
                    variant="underlined"
                    readonly
                  >
                    Material Design framework for Vue.js
                  </v-text-field>
                </v-col>
                <v-col cols="12" class="py-0">
                  <v-text-field
                    prepend-icon="mdi-wrench-outline"
                    variant="underlined"
                    readonly
                  >
                    Prebuilt Material Design components
                  </v-text-field>
                </v-col>
                <v-col cols="12" class="py-0">
                  <v-text-field
                    prepend-icon="mdi-timer-check-outline"
                    variant="underlined"
                    readonly
                  >
                    Fast prototyping and production-ready
                  </v-text-field>
                </v-col>
                <v-col cols="12" class="py-0">
                  <v-text-field
                    prepend-icon="mdi-responsive"
                    variant="underlined"
                    readonly
                  >
                    Built-in responsiveness and accessibility
                  </v-text-field>
                </v-col>
              </v-row>
            </v-card-text>
          </v-card>
          <div class="d-flex align-center justify-center">
            <v-img src="../assets/logo.png" width="200px"></v-img>
          </div>
        </div>
      </div>

      <!-- Getting Started -->
      <div v-if="dialogTopicKey === 3">
        <v-carousel hide-delimiters show-arrows="hover">
          <v-carousel-item>
            <v-img src="../assets/step1.png" style="width: 100%; height: 100%">
            </v-img>
          </v-carousel-item>
          <v-carousel-item>
            <v-img src="../assets/step2.png" style="width: 100%; height: 100%">
            </v-img>
          </v-carousel-item>
          <v-carousel-item>
            <v-img src="../assets/step3.png" style="width: 100%; height: 100%">
            </v-img>
          </v-carousel-item>
          <v-carousel-item>
            <v-img src="../assets/step4.png" style="width: 100%; height: 100%">
            </v-img>
          </v-carousel-item>
          <v-carousel-item>
            <v-img src="../assets/step5.png" style="width: 100%; height: 100%">
            </v-img>
          </v-carousel-item>
          <v-carousel-item>
            <v-img src="../assets/step6.png" style="width: 100%; height: 100%">
            </v-img>
          </v-carousel-item>
        </v-carousel>
      </div>

      <!-- Benefits -->
      <div v-if="dialogTopicKey === 4">
        <div
          class="d-flex flex-column-right align-center justify-space-between pr-3"
        >
          <v-card width="500px" elevation="9">
            <v-card-text>
              <v-row>
                <v-col cols="12" class="py-0">
                  <v-text-field
                    prepend-icon="mdi-developer-board"
                    variant="underlined"
                    readonly
                  >
                    Rapid development with reusable components
                  </v-text-field>
                </v-col>
                <v-col cols="12" class="py-0">
                  <v-text-field
                    prepend-icon="mdi-material-ui"
                    variant="underlined"
                    readonly
                  >
                    Consistent UI
                  </v-text-field>
                </v-col>
                <v-col cols="12" class="py-0">
                  <v-text-field
                    prepend-icon="mdi-speedometer"
                    variant="underlined"
                    readonly
                  >
                    Performance boosts from Vue 3
                  </v-text-field>
                </v-col>
                <v-col cols="12" class="py-0">
                  <v-text-field
                    prepend-icon="mdi-face-agent"
                    variant="underlined"
                    readonly
                  >
                    Strong community support
                  </v-text-field>
                </v-col>
              </v-row>
            </v-card-text>
          </v-card>
          <div>
            <v-img src="../assets/benefitsBackground.avif" width="300px">
            </v-img>
          </div>
        </div>
      </div>
    </globalDialog>
  </div>
</template>

<script>
import globalDialog from "./globalDialog.vue";

export default {
  components: {
    globalDialog,
  },
  props: {
    dialogTitle: {
      type: String,
      default: "",
    },
    dialogTopicKey: {
      type: Number,
      default: null,
    },
  },
  data() {
    return {
      switchState: false,
      items: ["Item 1", "Item 2", "Item 3", "Item 4"],
      userName: "",
      isSubscribed: false,
      firstName: "",
      lastName: "",
      number: 0,
      squaredNumber: 0,
    };
  },
  computed: {
    fullName() {
      return `${this.firstName} ${this.lastName}`.trim();
    },
  },
  watch: {
    number(newValue) {
      this.squaredNumber = newValue * newValue;
    },
  },
};
</script>
