<template>
  <div id="stations" ref="container">
    <rad-station
      v-for="(station, index) in currentList"
      :key="station.id"
      :index="index"
      :station="station"
    />
  </div>
</template>

<script lang="ts">
import { Component, Ref, Vue } from "vue-property-decorator";
import { Getter } from "vuex-class";

import RadStation from "./RadStation.vue";

@Component({
  components: {
    RadStation,
  },
})
export default class RadStationList extends Vue {
  @Ref() readonly container!: HTMLTableSectionElement;

  @Getter readonly currentList!: Station[];

  get heights(): number[] {
    const stationRows = [...this.container.childNodes] as HTMLTableRowElement[];
    return stationRows.map(item => item.offsetHeight);
  }
}
</script>
