<template>
  <v-dialog
    v-model="dialog"
    persistent
    :fullscreen="isMobile"
    :max-width="width"
    @keydown.esc="close"
  >
    <!-- <v-card
      v-touch="{
        right: close,
        left: close
      }"
    > -->
    <v-card :loading="loading">
      <template #loader>
        <v-row
          v-if="loading"
          class="fill-height ma-0"
          align="center"
          justify="center"
        >
          <v-progress-linear indeterminate color="primary" />
        </v-row>
      </template>
      <v-card-title class="pa-0">
        <v-toolbar
          :elevation="isMobile ? 1 : 0"
          :color="!isDarkMode ? 'white' : ''"
        >
          <v-btn
            v-if="isMobile && !hideCancelButton"
            :disabled="saving"
            icon
            @click="close"
          >
            <v-icon>mdi-close</v-icon>
          </v-btn>

          <v-toolbar-title class="pt-1">
            {{ title }}
            <v-spacer />
            <slot name="subtitle" />
          </v-toolbar-title>

          <slot v-if="isMobile" name="actions" />
        </v-toolbar>
      </v-card-title>
      <v-card-text :class="noPadding ? 'pa-0' : 'mt-4 pt-0 pa-6'">
        <v-container v-if="subtitle" class="pa-0 pb-4">
          {{ subtitle }}
        </v-container>
        <slot />
      </v-card-text>
      <v-card-actions v-if="!isMobile">
        <v-btn
          v-if="!hideCancelButton"
          color="secondary"
          :disabled="saving"
          variant="text"
          @click="close"
        >
          Cancel
        </v-btn>
        <v-spacer />
        <slot name="actions" />
      </v-card-actions>
    </v-card>
  </v-dialog>
</template>

<script>
export default {
  name: "GlobalDialog",
  props: {
    title: {
      type: String,
      default: "Title",
    },
    subtitle: {
      type: String,
      default: null,
    },
    fullscreen: {
      type: Boolean,
      default: false,
    },
    noPadding: {
      type: Boolean,
      default: false,
    },
    width: {
      type: String,
      default: "900px",
    },
    compact: {
      type: Boolean,
      default: false,
    },
    saving: {
      type: Boolean,
      default: false,
    },
    loading: {
      type: Boolean,
      default: false,
    },
    hideCancelButton: {
      type: Boolean,
      default: false,
    },
  },
  emits: ["close"],
  data() {
    return {
      dialog: true,
    };
  },
  computed: {
    /**
     * Check if the device is mobile
     * @returns {boolean} True if mobile
     */
    isMobile() {
      if (this.compact) return false; // disable fullscreen on mobile devices if compact is true
      return this.fullscreen || this.$vuetify.display.xs;
    },
    /**
     * Check if darkMode is enabled
     * @returns {boolean} True if darkMode
     */
    isDarkMode() {
      return this.$vuetify.theme.current.dark;
    },
  },
  methods: {
    /**
     * Show the dialog
     */
    show() {
      this.dialog = true;
    },
    /**
     * Close the dialog
     */
    close() {
      //if saving prop is true then don't close, because we are saving
      if (this.saving) return;
      this.dialog = false;
      this.$emit("close");
    },
  },
};
</script>
