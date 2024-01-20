<template>
  <div>
    <div class="sidebar">
      <Vueform v-model="paramsForm">
        <StaticElement name="h32" tag="h3" content="Update params" />
        <TextElement name="unit" label="Unit" />
        <TextElement name="originName" label="Origin name" />
        <ButtonElement name="submit" button-label="Update" @click="updateParams" :submits="false" align="center"
          :full="true" />
      </Vueform>
      <hr>
      <Vueform v-model="createForm">
        <StaticElement name="h3" tag="h3" content="New event" />
        <TextElement name="name" label="Name" />
        <TextElement name="date" input-type="number" :rules="[
          'nullable',
          'numeric',
        ]" autocomplete="off" label="Date" />
        <TextareaElement name="description" label="Description" />
        <ButtonElement name="submit" button-label="Create" @click="createEvent" :submits="false" align="center"
          :full="true" />
      </Vueform>
    </div>
    <div class="timeline">
      <CustomTimeline :events="events" />
    </div>
  </div>
</template>

<script>
import { ref } from 'vue';
import '../components/CustomTimeline.vue'
import CustomTimeline from '../components/CustomTimeline.vue';

export default {
  data() {
    return {
      paramsForm: {},
      createForm: {},
      events: ref([]),
      originName: 'Christ',
      unit: 'year',
    }
  },
  methods: {
    createEvent() {
      this.events.append(this.createForm);
      this.createForm = {}
    },
    updateParams() {
      console.log('update')
    }
  },
  components: { CustomTimeline }
}
</script>

<style lang="scss" scoped>
hr {
  margin-top: 20px;
  margin-bottom: 20px;
}

.sidebar {
  background-color: gray;
  width: 350px;
  padding: 20px;
  height: auto;
  position: absolute;
  left: 0;
  top: 0;
  bottom: 0;
}

.timeline {
  padding-left: 350px;
  display: flex;
  flex-direction: column;
  align-items: center;
}
</style>
