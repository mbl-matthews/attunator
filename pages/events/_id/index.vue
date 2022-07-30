<template>
  <v-container>
    <v-row>
      <v-col>
        <h1>{{ currentEvent.name }}</h1>
        <span>
          {{
            `${formatDate(currentEvent.startdate)} bis ${formatDate(
              currentEvent.enddate
            )}`
          }}
        </span>
      </v-col>
    </v-row>
    <v-row class="mb-n5">
      <v-col>
        <v-divider/>
      </v-col>
    </v-row>
    <v-row>
      <v-col>
        <h3>{{ 'Acts' }}</h3>
        <v-container class="pa-0 mt-3">
        <v-row v-for="act in acts" :key="act.id" class="my-n3">
          <v-col>
            <v-card style="border: 1px solid #000090;" :to="`/events/${act.event.id}/${act.id}/`">
              <v-card-title class="mb-n5">
                {{ act.name }}
                <v-spacer />
                <v-icon> mdi-bell-outline </v-icon>
              </v-card-title>
              <v-container>
                <v-row class="mb-n7">
                  <v-col>
                    <span>
                      <i><b>{{ 'Start ' }}</b></i>
                    </span>
                    <span>
                      {{ `${formatDate(act.start)}` }}
                    </span>
                  </v-col>
                </v-row>
                <v-row class="my-n7">
                  <v-col>
                    <span>
                      <i><b>{{ 'End ' }}</b></i>
                    </span>
                    <span>
                      {{ `${formatDate(act.end)}` }}
                    </span>
                  </v-col>
                </v-row>
                <v-row class="mt-n7">
                  <v-col>
                    <span>
                      <i><b>{{ 'Stage ' }}</b></i>
                    </span>
                    <span>
                      {{ `${act.stage}` }}
                    </span>
                  </v-col>
                </v-row>
              </v-container>
            </v-card>
          </v-col>
        </v-row>
      </v-container>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
import { uuid } from 'vue-uuid'

export default {
  name: 'EventDetail',
  data() {
    return {
      eventId: this.$route.params.id,
      currentEvent: {
        id: this.$route.params.id,
        name: 'Wacken Open Air',
        startdate: new Date('2022-08-04'),
        enddate: new Date('2022-08-06'),
      },
      acts: [
        {
          id: uuid.v4(),
          event: {
            id: uuid.v4(),
            name: 'Event',
          },
          start: new Date('2022-04-08 14:00:00'),
          end: new Date('2022-04-08 15:00:00'),
          name: 'Band',
          stage: 'Stagename',
        },
        {
          id: uuid.v4(),
          event: {
            id: uuid.v4(),
            name: 'Event 2',
          },
          start: new Date('2022-04-08 15:15:00'),
          end: new Date('2022-04-08 16:00:00'),
          name: 'Band 2',
          stage: 'Stagename 2',
        },
        {
          id: uuid.v4(),
          event: {
            id: uuid.v4(),
            name: 'Event 3',
          },
          start: new Date('2022-04-08 20:00:00'),
          end: new Date('2022-04-08 22:15:00'),
          name: 'Band 3',
          stage: 'Stagename Main',
        },
      ],
    }
  },
  methods: {
    formatDate(date) {
      const year = date.getFullYear()
      const month = date.getMonth()
      const day = date.getDate()

      let mStr = ''
      if (month < 10) {
        mStr = '0'
      }
      mStr += month.toString()

      let dStr = ''
      if (day < 10) {
        dStr = '0'
      }
      dStr += day.toString()

      return `${dStr}.${mStr}.${year}`
    },
  },
}
</script>