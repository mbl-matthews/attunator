<template>
  <v-container>
    <v-row>
      <v-col>
        <h3>
          {{ 'Events' }}
        </h3>
        <v-container>
          <v-row v-for="event in events" :key="event.id">
            <v-col>
              <v-card :to="`${event.id}`">
                <v-card-title class="mb-n2">{{ event.name }}</v-card-title>
                <v-container>
                  <v-row>
                    <v-col>
                      <span>
                        {{
                          `${formatDate(event.startdate)} bis ${formatDate(
                            event.enddate
                          )}`
                        }}
                      </span>
                    </v-col>
                  </v-row>
                </v-container>
              </v-card>
            </v-col>
          </v-row>
        </v-container>
      </v-col>
    </v-row></v-container
  >
</template>

<script>
import { uuid } from 'vue-uuid'

export default {
  name: 'EventOverview',
  data() {
    return {
      events: [
        {
          id: uuid.v4(),
          name: 'Wacken Open Air',
          startdate: new Date('2022-08-04'),
          enddate: new Date('2022-08-06'),
        },
        {
          id: uuid.v4(),
          name: 'Reload Festival',
          startdate: new Date('2022-08-19'),
          enddate: new Date('2022-08-20'),
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