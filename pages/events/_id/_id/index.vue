<template>
  <v-container>
    <v-row>
      <v-col>
        hi
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
import { uuid } from 'vue-uuid'

export default {
  name: "ActDetail",
  data() {
    return {
      act: {
        id: uuid.v4(),
          event: {
            id: uuid.v4(),
            name: 'Event',
          },
          start: new Date('2022-04-08 14:00:00'),
          end: new Date('2022-04-08 15:00:00'),
          name: 'Band',
          stage: 'Stagename',
      }
    }
  }
}

</script>