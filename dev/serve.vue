<template>
  <div>
    <div class="container pt-5 pb-5">
      <h1>
        Vue Bottom Sheet
      </h1>
      <p>
        A nice clean and touch-friendly bottom sheet component based on
        <a target="_blank" href="https://vuejs.org/">Vue.js</a> and
        <a target="_blank" href="https://hammerjs.github.io/">Hammer.js</a>
      </p>
      <h3 class="mb-3">Settings</h3>
      <hr style="opacity: 0.1">
      <div class="row">
        <div class="col-md-4 col-12">
          <div class="form-check form-switch mb-3">
            <input
                class="form-check-input"
                type="checkbox"
                id="flexSwitchCheckChecked"
                v-model="overlay"
                checked
            />
            <label class="form-check-label" for="flexSwitchCheckChecked"
            >Overlay</label
            >
          </div>
          <div class="form-check form-switch mb-3">
            <input
                class="form-check-input"
                type="checkbox"
                id="closeSwitchCheckChecked"
                v-model="clickToClose"
                checked
            />
            <label class="form-check-label" for="closeSwitchCheckChecked"
            >Click outside card to close</label
            >
          </div>
          <div class="form-check form-switch mb-3">
            <input
                class="form-check-input"
                type="checkbox"
                id="roundedCheckChecked"
                v-model="rounded"
                checked
            />
            <label class="form-check-label" for="roundedCheckChecked"
            >Rounded top corners</label
            >
          </div>
          <div class="form-check form-switch mb-3">
            <input
                class="form-check-input"
                type="checkbox"
                id="swipeSwitchCheckChecked"
                v-model="swipeAble"
                checked
            />
            <label class="form-check-label" for="swipeSwitchCheckChecked"
            >Swipe Able</label
            >
          </div>
          <div class="form-check form-switch mb-3">
            <input
                class="form-check-input"
                type="checkbox"
                id="fullscreenSwitchCheckChecked"
                v-model="isFullScreen"
            />
            <label class="form-check-label" for="fullscreenSwitchCheckChecked"
            >Full Screen</label
            >
          </div>
          <div class="form-check form-switch mb-3">
            <input
                class="form-check-input"
                type="checkbox"
                id="srollableSwitchCheckChecked"
                v-model="backgroundScrollable"
            />
            <label class="form-check-label" for="srollableSwitchCheckChecked"
            >Background scrollable</label
            >
          </div>
          <div class="form-check form-switch mb-3">
            <input
                class="form-check-input"
                type="checkbox"
                id="clickableSwitchCheckChecked"
                v-model="backgroundClickable"
            />
            <label class="form-check-label" for="clickableSwitchCheckChecked"
            >Background clickable</label
            >
          </div>
        </div>
        <div class="col-md-4 col-12">
          <div class="mb-3">
            <h6> Overlay Color</h6>
            <sketch-picker v-model="overlayColorSelect"/>
          </div>
        </div>
        <div class="col-md-4 col-12">

          <div class="form-group mb-3">
            <label for="maxWidthInput" class="form-label">Max width:</label>
            <input
                name="maxWidthInput"
                id="maxWidthInput"
                v-model="maxWidth"
                type="text"
                class="form-control"
            />
          </div>
          <div class="form-group mb-3">
            <label for="maxHeightInput" class="form-label">Max height:</label>
            <input
                name="maxHeightInput"
                id="maxHeightInput"
                v-model="maxHeight"
                type="text"
                class="form-control"
            />
          </div>
          <div class="form-group mb-3">
            <label for="effectSelect" class="form-label">Effects:</label>
            <select
                v-model="effect"
                class="form-select"
                name="effectSelect"
                id="effectSelect"
            >
              <option selected value="fx-default">fx-default</option>
              <option selected value="fx-fadein-scale">fx-fadein-scale</option>
              <option selected value="fx-slide-from-right"
              >fx-slide-from-right
              </option
              >
              <option selected value="fx-slide-from-left"
              >fx-slide-from-left
              </option
              >
            </select>
          </div>
        </div>
      </div>
      <button class="btn btn-primary" type="button" @click="open">
        Open bottom sheet
      </button>
      <vue-bottom-sheet
          :max-width="maxWidth"
          :max-height="maxHeight"
          :overlay="overlay"
          :click-to-close="clickToClose"
          :effect="effect"
          :rounded="rounded"
          :swipeAble="swipeAble"
          :overlayColor="overlyHexColor"
          :isFullScreen="isFullScreen"
          :backgroundScrollable="backgroundScrollable"
          :backgroundClickable="backgroundClickable"
          ref="myBottomSheet"
      >
        <div class="sheet-content">
          <h1>Lorem Ipsum</h1>
          <p>
            Lorem ipsum dolor sit amet, consectetur adipisicing elit. Maxime
            neque sed tempore ullam. Accusamus animi at autem beatae est, hic
            inventore iste minima, non quibusdam quisquam quos velit veritatis
            voluptatem?
          </p>
          <p>
            Lorem ipsum dolor sit amet, consectetur adipisicing elit. Maxime
            neque sed tempore ullam. Accusamus animi at autem beatae est, hic
            inventore iste minima, non quibusdam quisquam quos velit veritatis
            voluptatem?
          </p>
          <p>
            Lorem ipsum dolor sit amet, consectetur adipisicing elit. Maxime
            neque sed tempore ullam. Accusamus animi at autem beatae est, hic
            inventore iste minima, non quibusdam quisquam quos velit veritatis
            voluptatem?
          </p>
          <p>
            Lorem ipsum dolor sit amet, consectetur adipisicing elit. Maxime
            neque sed tempore ullam. Accusamus animi at autem beatae est, hic
            inventore iste minima, non quibusdam quisquam quos velit veritatis
            voluptatem?
          </p>
          <h2>
            Lorem Ipsum
          </h2>
          <p>
            Lorem ipsum dolor sit amet, consectetur adipisicing elit. Animi
            excepturi explicabo id illum magnam possimus provident quae
            recusandae rerum tempore. Ab adipisci beatae, distinctio ea nemo
            omnis sed similique veniam.
          </p>
          <button type="button" class="btn btn-danger" @click="close">
            Close
          </button>
        </div>
      </vue-bottom-sheet>
    </div>
  </div>
</template>

<script>
import Vue from 'vue';
import VueBottomSheet from '@/vue-bottom-sheet.vue';
import sketch from 'vue-color/src/components/Chrome'

export default Vue.extend({
  name: 'ServeDev',

  data() {
    return {
      overlay: true,
      maxWidth: "640px",
      maxHeight: "90%",
      clickToClose: true,
      effect: "fx-default",
      rounded: true,
      swipeAble: true,
      isFullScreen: false,
      overlayColorSelect: "#0000004D",
      backgroundScrollable: false,
      backgroundClickable: false,
    };
  },
  components: {
    VueBottomSheet,
    'sketch-picker': sketch,
  },
  methods: {
    open() {
      this.$refs.myBottomSheet.open();
    },
    close() {
      this.$refs.myBottomSheet.close();
    }
  },
  computed: {
    overlyHexColor() {
      if (this.overlayColorSelect != null)
        return this.overlayColorSelect.hex8;
    }
  }
});
</script>

<style>
@import "https://cdn.jsdelivr.net/npm/bootstrap@5.0.0-beta2/dist/css/bootstrap.min.css";

.sheet-content {
  padding: 20px;
}
</style>
