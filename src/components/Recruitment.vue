<template>
  <v-row align="left" justify="left">
    <v-flex just>
      <v-container>
        <v-row align="left" justify="left">
          <v-card
            :elevation="5"
            class="recruitment-card">
            <div 
              :class="{'display-3 font-weight-bold ': $vuetify.breakpoint.smAndUp, 'display-2 font-weight-bold': $vuetify.breakpoint.smAndDown}">
              Wanna join LiQ?
              </div>
            <div
              :class="{'subtitle-1': $vuetify.breakpoint.smAndDown}"
              class="opacity-text">
              We are always looking for new members. If you are interested in joining, please read the steps below on 
              how to become a member or contact one of the recruiters in our discord.
            </div>
          </v-card>
        </v-row>
      </v-container>
    </v-flex>
    <v-flex just>
      <v-row align="left" justify="left" class="contentRow">
        <v-timeline align-top :dense="$vuetify.breakpoint.smAndDown">
            <v-timeline-item
            v-for="(item, index) in stepsForRecruitment"
            :key="index"
            :color="item.color"
            :icon="item.icon"
            fill-dot>
            <v-card dark>
                <v-card-title>{{item.title}}</v-card-title>
                <v-card-text class="#272727 text--primary preWrapped">{{item.content}}</v-card-text>
            </v-card>
            </v-timeline-item>
        </v-timeline>
      </v-row>
    </v-flex>
  </v-row>
</template>

<script>
import mediaLinks from "@/assets/json/mediaLinks.json"
export default {
  data: () => ({
      mediaLinks: mediaLinks,
      squadCompetitiveLink: mediaLinks.find(o=>{
        return o.name === "squadCompetitive";
      }),
      competitiveTrelloLink: mediaLinks.find(o=>{
        return o.name === "competitiveTrello";
      })
    }),
  props: {
    stepsForRecruitment: {
      type: Array,
      default: function () {
        return {};
      },
    },
  },
};
</script>

<style lang="scss" scoped>
.v-card__text,
.v-card__title {
  word-break: normal !important;
}
.preWrapped {
  white-space: pre-wrap;
}
.recruitment-card{
  background:#222222 !important;
  padding:30px !important;
  border-radius: 10px !important;
  margin:0 10px 0 10px !important;
  width:100% !important;
}
.competitive-card{
  background:#222222 !important;
  padding:30px !important;
  border-radius: 10px !important;
  margin:30px 10px 0 10px !important;
}
.opacity-text{
  opacity: 0.75 !important; 
  margin-top:10px !important;
}
.contentRow{
  margin:0 10px 0 10px !important;
}
</style>
