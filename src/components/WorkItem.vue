<template>
  <v-card>
    <v-img :src="url"></v-img>
    <v-card v-if="work.caption" class="caption">
      <p v-if="work.title" class="title">{{ work.title }}</p>
      <p v-if="work.englishTitle" class="english-title">
        {{ work.englishTitle }}
      </p>
      <v-spacer></v-spacer>
      <p v-if="creator" class="creator">{{ creator }}</p>
      <p v-if="work.materials" class="materials">{{ work.materials[0] }}</p>
      <p v-if="work.comment" class="comment">{{ work.comment }}</p>
    </v-card>
  </v-card>
</template>

<script>
export default {
  props: {
    work: Object,
  },
  computed: {
    url() {
      return this.work.work.url + "?q=10&fm=webp";
    },
    creator() {
      return this.work.creator.join(" ");
    }
  },
};
</script>

<style scoped>
.caption {
  margin: 10px;
}
.title {
  margin: 0;
  font-size: 0.9em;
}

.english-title {
  margin: 0 5 0 0;
}
.creator,
.comment {
  margin: 0;
  font-size: 0.7em;
}
.materials {
  margin: 0;
  font-size: 0.65em;
}
</style>
