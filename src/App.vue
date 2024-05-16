<template>
  <div class="centeral">
    Hi There, {{ firstName }} {{  lastName }}
    <div>

      Hi from Computed Property, {{ fullName }}
    </div>
    <div v-for="item in items" :key="item.id">
      <div v-if="item.price > 2000">
        <h2>{{ item.id }} - {{ item.title }} - {{ item.price }}</h2>

      </div>


    </div>
    <div>
      <h2>Watcher Prperty in Vue</h2>
      current - volume - {{ volume }}
    </div>
    <button @click="volume+=2">Increase</button>
    <button @click="volume-=2">Decrease</button>
  
  </div>
  <div>
    <Greet name="Rohan" />
    <Greet name="Raul"/>
    <Greet name="Cristiano"/>

  </div>
</template>
<script >
import Greet from './components/Greet.vue';

export default{
    name: 'App',
    data() {
        return {
            firstName: 'Rohan',
            lastName: 'George',
            volume: 0,
            items: [
                {
                    id: 1,
                    title: "TV",
                    price: 2501
                },
                {
                    id: 2,
                    title: "Football jabulani",
                    price: 2334
                },
                {
                    id: 3,
                    title: "Adidas jabulani",
                    price: 1334
                },
                {
                    id: 4,
                    title: "Football El  jabulani",
                    price: 2634
                },
            ]
        };
    },
    methods: {},
    computed: {
        fullName() {
            return `${this.firstName} ${this.lastName}`;
        }
    },
    watch: {
        volume(newVal, oldValue) {
            if (newVal > oldValue && newVal === 16) {
                alert('High Volume Warning !!!');
            }
        }
    },
    components: { Greet }
}

</script>
<style>  

.centeral{
  display: flex;
  flex-direction: column;
  justify-content: space-around;
  
}

</style>