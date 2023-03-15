<template>
  <div class="h-screen">
    <div class="text-center mt-16">


      <v-card
        class="mx-auto text-center"
        max-width="344"
        variant="outlined"

      >

        <v-card-item>
          <div>
            <div class="text-overline mb-1">
              Hi !
            </div>
            <div class="text-h6 mb-1">
              Dexter Bagtang
            </div>
            <div class="text-caption mb-1">Web Developer</div>
          </div>

        </v-card-item>

        <v-card-actions class="justify-center">
          <v-dialog
            transition="dialog-top-transition"
            width="auto"
          >
            <template v-slot:activator="{ props }">
              <v-btn
                variant="outlined"
                v-bind="props"
                class="mb-1"
                size="x-small"
              >Let's Connect</v-btn>
            </template>
            <template v-slot:default="{ isActive }">
              <v-card max-width="444" width="384">
                <!-- <v-toolbar
                  title="Let's Connect"
                ></v-toolbar> -->
                <v-card-text>
                  <div class="text-h5 pa-2">Let's Connect</div>
                </v-card-text>

                <v-container>
                  <v-text-field
                    label="Email address"
                    placeholder="johndoe@gmail.com"
                    type="email"
                    variant="outlined"
                    density="compact"
                  ></v-text-field>

                    <v-textarea
                      clearable
                      clear-icon="mdi-close-circle"
                      label="Message"
                      model-value=""
                      variant="outlined"
                      density="compact"
                      rows="3"
                    ></v-textarea>
                </v-container>

                <v-card-actions class="justify-end">

                  <v-btn
                    variant="outlined"
                    size="small"
                    @click="isActive.value = false;"
                  >Submit</v-btn>



                  <v-btn
                    variant="outlined"
                    size="small"
                    @click="isActive.value = false"
                  >Close</v-btn>
                </v-card-actions>
              </v-card>
            </template>
          </v-dialog>
<!--          <v-btn variant="outlined">-->
<!--            Know more-->
<!--          </v-btn>-->
        </v-card-actions>
        <v-expansion-panels>
          <v-expansion-panel
            variant="accordion"
            title="About"
            class="text-caption text-left"
            text="Lorem ipsum dolor sit amet consectetur adipisicing elit. Commodi, ratione debitis quis est labore voluptatibus! Eaque cupiditate minima"
          >
          </v-expansion-panel>
          <v-expansion-panel
            title="Projects"
            class="text-caption"
            text="Lorem ipsum dolor sit amet consectetur adipisicing elit. Commodi, ratione debitis quis est labore voluptatibus! Eaque cupiditate minima"
          >
          </v-expansion-panel>

          <v-expansion-panel
            title="Skills"
            class="text-caption"
          >

            <v-expansion-panel-text class="text-left">
              <v-chip
                class="ma-2"
                prepend-icon="mdi-laravel"
                color="red"
                variant="outlined"
              >
                Laravel
              </v-chip>

              <v-chip
                class="ma-2"
                color="primary"
                text-color="black"
                prepend-icon="mdi-language-php"
              >
                PHP
              </v-chip>

              <v-chip
                class="ma-2"
                color="deep-orange"
                text-color="white"
                append-icon="mdi-language-html5"
              >
                HTML
              </v-chip>

              <v-chip
                class="ma-2"
                color="blue-darken-3"
                text-color="white"
                append-icon="mdi-language-css3"
              >
                CSS
              </v-chip>

              <v-chip
                class="ma-2"
                color="yellow"
                text-color="black"
                variant="flat"
                append-icon="mdi-language-javascript"
              >
                Javascript
              </v-chip>



              <v-chip
                class="ma-2"
                color="deep-purple"
                text-color="white"
                prepend-icon="mdi-bootstrap"
                :model-value="true"

              >
                Bootstrap
              </v-chip>

              <v-chip
                class="ma-2"
                color="cyan"
                text-color="white"
                prepend-icon="mdi-database-search"
                :model-value="true"
              >
                MySQL
              </v-chip>

              <v-chip
                class="ma-2"
                color="teal"
                text-color="white"
                prepend-icon="mdi-vuejs"
                :model-value="true"
              >
                Vue
              </v-chip>

              <v-chip
                class="ma-2"
                color="light-blue"
                text-color="white"
                prepend-icon="mdi-tailwind"
                :model-value="true"
              >
                Tailwind
              </v-chip>

              <v-chip
                class="ma-2"
                color="deep-orange-accent-3"
                text-color="black"
                prepend-icon="mdi-web"
                :model-value="true"
                variant="flat"
              >
                Apache
              </v-chip>

              <v-chip
                class="ma-2"
                color="red"
                text-color="white"
                prepend-icon="mdi-redhat"
                variant="outlined"
                :model-value="true"
              >
                CentOS AlmaLinux
              </v-chip>

            </v-expansion-panel-text>

          </v-expansion-panel>
        </v-expansion-panels>
      </v-card>
    </div>



    <div class="w-75 mx-auto mt-5 flex-wrap justify-lg-center">
      <v-text-field
        :loading="loading"
        density="compact"
        variant="outlined"
        label="Search templates"
        :append-inner-icon="loading ? '' : 'mdi-send'"
        single-line
        hide-details
        v-model="prompt"
        @click:append-inner="generateText"
      ></v-text-field>
    <hr>
      <v-container v-for="result in results.choices" v-text="result.text">
      </v-container>
    <hr>
  </div>
  </div>
</template>

<script>
import axios from 'axios';

export default {
  data(){
    return{
      prompt:'',
      results:'',
      loaded: false,
      loading: false,

    }
  },


  methods:{
    async generateText() {
      this.loading=true;
      const apiKey = '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';
      const url = 'https://api.openai.com/v1/engines/text-davinci-003/completions';

      const prompt = this.prompt;
      const maxTokens = 1024;
      const n = 1;
      const temperature = 0.7;

      try {
        const response = await axios.post(url, {
          prompt,
          max_tokens: maxTokens,
          n: n,
          temperature: temperature
        }, {
          headers: {
            'Authorization': `Bearer ${apiKey}`,
            'Content-Type': 'application/json'
          }
        });
        console.log(response.data.choices[0].text);
        this.results = response.data;
        this.loading=false;
      } catch (error) {
        console.error(error);
      }
    },
    // onClick () {
    //   this.loading = true
    // },

  }
}
</script>


