<body>
        <div id="app">
                <div v-for="artist in artists" :key="artist.name">
                  <h1>{{ artist.name }} - <small>{{ artist.Album }}</small></h1>
              
                  <span v-for="star in artist.rating">❤️</span>
              
                  <div v-if="artist.rating > 5">Wow, this game must be <b>REALLY</b> good</div>
                </div>
              </div>
      
        <script src="https://cdn.jsdelivr.net/npm/vue/dist/vue.js"></script>
      
        <script>
             Vue.component('awesome-button', {
                template: `<button @click="clickHandler">Click me for some awesomeness</button>`,
                methods: {
                    clickHandler() {
                    alert('YAAAS 😎');
                    }
                }
                });
          const app = new Vue({
            el: '#app',
            data: {
                artists:[
                { name: 'Nipsey Hussle', Album: 'Victory Lap', rating: 10 },
                { name: 'Jay-Z', Album: 'Blueprin 2', rating: 10 },
                { name: 'Rick Ross', Album: 'Port of Miami', rating: 8 },
                { name: 'J Cole', Album: 'KOD', rating: 9 }
                ]
            },
            methods: {
      
            }
          });
        </script>
      </body>
          Vue.component('awesome-button', {
                template: `<button @click="clickHandler">Click me for some awesomeness</button>`,
                methods: {
                    clickHandler() {
                    alert('YAAAS 😎');
                    }
                }
                });
    Vue.component('artists-card', {
      //never modify a 'prop' from inside the component
        props: ['artistsData'],
        //data property for components must be a function
        data() {
            return {
              //{...artistsData} is a spread operator and makes a copy of artistsData 'prop'
              artists: {...this.artistsData}
            }
          },
        template: `
          <div style="border-radius: .25rem; border: 1px solid #ECECEC;">
            <h2>{{ artists.name }} - <small>{{ artists.console }}</small></h2>

            <span v-for="heart in artists.rating">❤️</span>

            <button @click="increaseRating">Increase Rating</button>
          </div>
        `,
        methods: {
          increaseRating() {
            this.artists.rating++
          }
        }
      });
    const app = new Vue({
      el: '#app',
      data: {
        artists:[
                { name: 'Nipsey Hussle', Album: 'Victory Lap', rating: 10 },
                { name: 'Jay-Z', Album: 'Blueprin 2', rating: 10 },
                { name: 'Rick Ross', Album: 'Port of Miami', rating: 8 },
                { name: 'J Cole', Album: 'KOD', rating: 9 }
                ]
      }
    });

    <!-- : before artists-data => (this is a shorthand for v-bind:!)-->
    <artists-card v-for="artist in artists" :artists-data="artist" :key="artists.name"></artists-card>


    <age-calculator  v-for="person in people" :person="person" :key="person.name"></age-calculator>
    Vue.component('age-calculator', {
       //prop contains a type declaration to show whether its a object, string, array, or number.
        props: {
          person: {
            type: Object,
            required: true
          }
        },
      template: `
        <p>
          {{person.name}} has been kicking butt for {{daysAlive}} days!
        </p>
      `,
      //computed props are ran only when something changes in the code, methods run every time like functions.
      computed: {
        daysAlive(){
          return this.person.age * 365
        }
      }
    });

    const app = new Vue({
      el: '#app',
      data: {
        people: [
          { name: 'Mario', age: 38 },
          { name: 'Luigi', age: 38 },
          { name: 'Samus', age: 31 },
          { name: 'Link', age: 20 },
          { name: 'Marina', age: 32 },
          //Add yourself here :)
        ]
      }
    });