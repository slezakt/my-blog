<template>
  <div class="embla">
    <div ref="container" class="embla embla__viewport">
      <div class="embla__container">
        <slot></slot>
      </div>
    </div>
    <div class="embla__dots">
      <dot-btn
        v-for="(snap, index) in scrollSnaps"
        :key="index"
        :selected="index === selectedScrollSnap"
        @click="embla.scrollTo(index)"
      ></dot-btn>
    </div>
    <prev-btn v-if="embla" :enabled="prevBtnEnabled" @click="embla.scrollPrev"></prev-btn>
    <next-btn v-if="embla" :enabled="nextBtnEnabled" @click="embla.scrollNext"></next-btn>
  </div>
</template>

<script>
import EmblaCarousel, { UserOptions } from "embla-carousel";
import "../css/embla.css";
import DotBtn from "./DotBtn";
import PrevBtn from "./PrevBtn";
import NextBtn from "./NextBtn";

export default {
  name: "EmblaCarousel",
  components: {
    DotBtn,
    PrevBtn,
    NextBtn
  },
  props: { options: UserOptions },
  data() {
    return {
      embla: null,
      scrollSnaps: [],
      selectedScrollSnap: null,
      prevBtnEnabled: false,
      nextBtnEnabled: true
    };
  },
  methods: {
    onSelect() {
      this.selectedScrollSnap = this.embla.selectedScrollSnap();
      this.prevBtnEnabled = this.embla.canScrollPrev();
      this.nexBtnEnabled = this.embla.canScrollNext();
    }
  },
  mounted() {
    this.embla = EmblaCarousel(this.$refs.container, this.options);
    this.embla.on("select", this.onSelect);
    this.scrollSnaps = this.embla.scrollSnapList();
    this.onSelect();
  }
};
</script>