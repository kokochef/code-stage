<template>
  <div class="card">
    <header class="card-header">
      <p class="card-header-title">
        Output
      </p>
      <div
        class="card-header-icon tooltip is-tooltip-bottom is-tooltip-left-mobile"
        data-tooltip="Copy"
        v-clipboard:copy="output"
        v-clipboard:success="onCopy"
        v-clipboard:error="onError"
      >
        <span class="card-header-icon icon">
          <i class="fa fa-clipboard"></i>
        </span>
      </div>
    </header>
    <div class="card-content output-container">
      <pre class="output-text">{{ output }}</pre>
    </div>
    <footer class="card-footer">
      <div class="card-footer-item">
        <div class="buttons">
          <button class="button is-primary is-rounded" @click="clearOutput">
            <span class="icon"><i class="fa fa-trash-o"></i></span>
            <span>Clear Output</span>
          </button>
        </div>
      </div>
    </footer>
  </div>
</template>

<script>
import { copyHandlers } from "@/shared/mixins/copyHandlers";
import { mapState } from "vuex";

export default {
  name: "output-card",
  mixins: [copyHandlers],
  computed: {
    ...mapState("plg", ["output"])
  },
  methods: {
    clearOutput: function() {
      this.$store.commit("plg/@SET_OUTPUT", "");
    }
  }
};
</script>

<style scoped>
.card {
  height: 100%;
  background-color: #1e1e1e;
  border-radius: 5px;
  box-shadow: 0px 4px 4px rgba(0, 0, 0, 0.5);
}

.card-header-title {
  color: rgba(255, 255, 255, 0.87);
}

.card-header {
  color: rgba(255, 255, 255, 0.87);
  box-shadow: 0px 5px 6px 0px rgba(0, 0, 0, 0.8);
  z-index: 5;
}

.card-footer {
  border-top: none;
}

.card-footer-item:first-child {
  justify-content: left;
}

.output-container {
  padding: 0;
}

pre {
  white-space: pre;
  max-height: 45vh;
  min-height: 45vh;
  height: 100%;
  overflow: auto;
  word-break: normal !important;
  word-wrap: normal !important;
}

.output-text {
  color: rgba(255, 255, 255, 0.87);
  background-color: #252525;
}
</style>
