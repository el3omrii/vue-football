<template>
  <div class="pitch responsive" :style="pitchStyle()">
    <div class="teams">
      <team
        v-for="(team, index) in teams" v-bind:key="index"
        :players="team.startXI"
        :formation="team.formation"
        :colors="team.team.colors"
        :away="index === 1"
      />
    </div>
  </div>
</template>
<script>
import Team from "../team";

import groundBackground from "./img/pitch.png"
import pitchPattern from "./img/lines.png"
export default {
  name: "pitch",
  components: { Team },
  props: {
    color: {
      type: String,
      default: "#588f58",
    },
    pattern: {
      type: String,
      default: "lines",
    },
    teams: {
      type: Array,
      default: () => [],
    },
  },
  setup(props) {
    const pitchStyle = () => {
      let style = `background-color: ${props.color};`;
      style += `background-image: url(${groundBackground}), url(${pitchPattern});`;
      return style;
    };
    return {
      pitchStyle,
    };
  },
};
</script>
<style lang="scss" scoped>
@import "./pitch.scss";
</style>