
<template>
  <title>Weather App</title>

  <br>
  <v-card

    class= "mx-auto"
    max-width="500"
    color="blue">
    

    <v-card-item title="Kingston">
      <template v-slot: subtitle>
        <Icon 
        name="mdi-alert"
        size="25"
        color="red"
        class="me-1 pb-1"></Icon>
        
        Hurricane Alert!
      </template>
    </v-card-item>

    <v-card-text class="py-0">
      <v-row align="center" no gutters>
        <v-col
        class="text-h2"
        cols="6">

        64&deg;F
          
        </v-col>

        <v-col cols="6" class="text-right">
          <Icon
          name="mdi-weather-hurricane"
          color="orange"
          size="88"

          >

          </Icon>
        </v-col>
      </v-row>
    </v-card-text>

    <div class="d-flex py-3 justify-space-between">
      <v-list-item
      density="compact"
      prepend-icon="mdi-weather-windy"
      >
      <v-list-item-subtitle>Wind Speed:138 km/h</v-list-item-subtitle>

      </v-list-item>

      <v-list-item
      density="compact"
      prepend-icon="mdi-weather-pouring">

      <v-list-item-subtitle>Precipitation:48%</v-list-item-subtitle>

      </v-list-item>
    </div>

    <v-expand-transition>
      <div v-if="expand">
        <div class="py-2">
          <v-slider
            v-model="time"
            :max="6"
            :step="1"
            :ticks="labels"
            class="mx-4"
            color="primary"
            density="compact"
            hide-details
            show-ticks="always"
            thumb-size="10"
          ></v-slider>
        </div>

        <v-list class="bg-transparent">
          <v-list-item
            v-for="item in forecast"
            :key="item.day"
            :title="item.day"
            :append-icon="item.icon"
            :subtitle="item.temp"
          >
          </v-list-item>
        </v-list>
      </div>
    </v-expand-transition>

    <v-divider></v-divider>

    <v-card-actions>
      <v-btn @click="expand = !expand">
        {{ !expand ? 'Full Report' : 'Hide Report' }}
      </v-btn>
    </v-card-actions>

     

  </v-card><br>

  <v-row justify="center" align="center">
    <v-col cols="auto">

      <v-card
    class="pa-4"
    flat
    height="89px"
    width="320px"
    color="amber"
    >

    <v-toolbar
      dense
      floating
    >
      <v-text-field
        hide-details
        single-line
      ></v-text-field>
      <v-btn
      rounded="xs"
      size="small"
      density="comfortable"
      variant="plain"
      >
        <Icon name="mdi-magnify"/>
      </v-btn>
    </v-toolbar>

  </v-card>
      
    </v-col>
  </v-row>
  
  
  
</template>

<script >

export default {
    data: () => ({
      labels: { 0: 'SU', 1: 'MO', 2: 'TU', 3: 'WED', 4: 'TH', 5: 'FR', 6: 'SA' },
      expand: false,
      time: 0,
      forecast: [
        { day: 'Tuesday', icon: 'mdi-white-balance-sunny', temp: '24\xB0/12\xB0' },
        { day: 'Wednesday', icon: 'mdi-white-balance-sunny', temp: '22\xB0/14\xB0' },
        { day: 'Thursday', icon: 'mdi-cloud', temp: '25\xB0/15\xB0' },
      ],
    }),
  }

  
</script>

 

<style>

body {
  background-color: #1e5bac84;
  color: white;
}
</style>