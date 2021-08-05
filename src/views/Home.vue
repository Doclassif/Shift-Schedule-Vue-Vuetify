<template>
  <div class="mt-5">
    <v-sheet height="64">
      <v-toolbar flat>
        <v-btn outlined class="mr-4" color="grey darken-2" @click="value = ''">
          Сегодня
        </v-btn>
        <v-btn
          fab
          text
          small
          color="grey darken-2"
          @click="$refs.calendar.prev()"
        >
          <v-icon small> mdi-chevron-left </v-icon>
        </v-btn>
        <v-btn
          fab
          text
          small
          color="grey darken-2"
          @click="$refs.calendar.next()"
        >
          <v-icon small> mdi-chevron-right </v-icon>
        </v-btn>
        <v-toolbar-title v-if="$refs.calendar">
          {{ $refs.calendar.title }}
        </v-toolbar-title>
      </v-toolbar>
    </v-sheet>
    <v-sheet>
      <v-calendar
      
        color="warning"
        ref="calendar"
        v-model="value"
        :weekdays="weekday"
        :type="type"
        :events="events"
        :event-overlap-mode="mode"
        :event-overlap-threshold="30"
      ></v-calendar>
    </v-sheet>
    <v-spacer></v-spacer>
    <div class="ml-3 mt-2 text-caption">Shift Schedule From Doclassif v 0.1</div>
  </div>
</template>

<script>
export default {
  data: () => ({
    type: "month",
    mode: "stack",
    weekday: [1, 2, 3, 4, 5, 6, 0],
    value: "",
    events: [],
    colors: [
      "blue",
      "indigo",
      "deep-purple",
      "cyan",
      "green",
      "orange",
      "grey darken-1",
    ],
  }),
  methods: {},
  created() {
    let str = this.$route.params.json;
    console.log("STRING",str);
    this.events = JSON.parse(str);
    console.log("JSON",this.events);
  },
};
</script>
