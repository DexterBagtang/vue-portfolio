<template>
  <div class="h-screen w-75 mx-auto">
    <div class="text-center mt-16">

      <v-alert
        v-if="sent"
        title="Thank You"
        icon="$success"
        closable
        close-label="Close Alert"
        density="compact"
        variant="outlined"
        class="mb-5 w-75 mx-auto"
        text="Lorem ipsum dolor sit amet consectetur adipisicing elit. Commodi, ratione debitis quis est labore voluptatibus! Eaque cupiditate minima, at placeat totam, magni doloremque veniam neque porro libero rerum unde voluptatem!"
      ></v-alert>


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
            v-model="modal"
          >
            <template v-slot:activator="{ props }">
              <v-btn
                v-if="!sent"
                variant="outlined"
                v-bind="props"
                class="mb-1"
                size="x-small"
              >Let's Connect
              </v-btn>
              <v-btn
                v-else
                variant="outlined"
                class="mb-1"
                size="x-small"
              >Thank You !
              </v-btn>
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
                      v-model="email"
                    ></v-text-field>

                    <v-textarea
                      clearable
                      auto-grow
                      clear-icon="mdi-close-circle"
                      label="Message"
                      model-value=""
                      variant="outlined"
                      density="compact"
                      rows="3"
                      v-model="message"
                    ></v-textarea>
                  </v-container>
                  <v-card-actions class="justify-end">

                    <v-btn
                      variant="outlined"
                      size="small"
                      type="submit"
                      @click="sendEmail"
                    >Submit
                    </v-btn>


                    <v-btn
                      variant="outlined"
                      size="small"
                      @click="isActive.value = false"
                    >Close
                    </v-btn>
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
                size="x-small"
              >
                Laravel
              </v-chip>

              <v-chip
                class="ma-2"
                color="primary"
                text-color="black"
                prepend-icon="mdi-language-php"
                size="x-small"
              >
                PHP
              </v-chip>

              <v-chip
                class="ma-2"
                color="deep-orange"
                text-color="white"
                append-icon="mdi-language-html5"
                size="x-small"
              >
                HTML
              </v-chip>

              <v-chip
                class="ma-2"
                color="blue-darken-3"
                text-color="white"
                append-icon="mdi-language-css3"
                size="x-small"
              >
                CSS
              </v-chip>

              <v-chip
                class="ma-2"
                color="yellow"
                text-color="black"
                variant="flat"
                append-icon="mdi-language-javascript"
                size="x-small"
              >
                Javascript
              </v-chip>


              <v-chip
                class="ma-2"
                color="deep-purple"
                text-color="white"
                prepend-icon="mdi-bootstrap"
                size="x-small"
                :model-value="true"

              >
                Bootstrap
              </v-chip>

              <v-chip
                class="ma-2"
                color="cyan"
                text-color="white"
                prepend-icon="mdi-database-search"
                size="x-small"
                :model-value="true"
              >
                MySQL
              </v-chip>

              <v-chip
                class="ma-2"
                color="teal"
                text-color="white"
                prepend-icon="mdi-vuejs"
                size="x-small"
                :model-value="true"
              >
                Vue
              </v-chip>

              <v-chip
                class="ma-2"
                color="light-blue"
                text-color="white"
                prepend-icon="mdi-tailwind"
                size="x-small"
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
                size="x-small"
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
                size="x-small"
              >
                CentOS AlmaLinux
              </v-chip>

            </v-expansion-panel-text>

          </v-expansion-panel>
        </v-expansion-panels>
      </v-card>
    </div>

    <v-container fluid class="mt-5 mb-2 flex-wrap justify-lg-center">

      <v-card variant="outlined" class="mb-5" v-if="submitted">

        <v-card-title class="text-caption" v-text="submittedPrompt" style="white-space: pre-wrap"></v-card-title>

        <v-card-text class="text-center" v-if="loading">
          <v-progress-circular
            :size="50"
            width="2"
            indeterminate

          ></v-progress-circular>
        </v-card-text>
        <v-card-text class="text-caption" v-text="results.slice(1)" style="white-space: pre-wrap" v-else></v-card-text>
      </v-card>

    </v-container>

    <v-textarea
      auto-grow
      rows="1"
      :loading="loading"
      density="compact"
      variant="outlined"
      label="Ask anything"
      :append-icon="loading ? '' : 'mdi-send'"
      clearable
      clear-icon="mdi-close-circle"
      v-model="prompt"
      @click:append="generateText"
      class="text-caption mx-auto"
    ></v-textarea>

  </div>

</template>

<script>
import axios from 'axios';

export default {
  data() {
    return {

      prompt: '',
      submitted: false,
      submittedPrompt: '',
      results: '',
      loaded: false,
      loading: false,
      email:'',
      message:'',
      sent:false,
      modal:false,

    }
  },
  watch: {
    sent (val) {
      if (!val) return
      setTimeout(() => (this.sent = false), 10000)
    },
  },


  methods: {
    async generateText() {
      this.submittedPrompt = this.prompt;
      this.prompt = '';
      this.submitted = true;
      this.loading = true;

      const apiKey = import.meta.env.VITE_API_KEY;
      const url = 'https://api.openai.com/v1/engines/text-davinci-003/completions';


      const prompt = this.submittedPrompt;
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
        console.log(response.data.choices[0]);
        this.results = response.data.choices[0].text;
        this.loading = false;
      } catch (error) {
        console.error(error);
      }
    },
    sendEmail() {
      let message = `from: ${this.email}\r\nSubject: New message from your website\r\n\r\n${this.message}`;
      Email.send({
        Host: 'smtp.elasticemail.com',
        Username: 'dexbag69@gmail.com',
        Password: import.meta.env.VITE_SMPT_PASSWORD,
        Port:2525,
        To: 'dexterbagtang@gmail.com',
        From: 'dexbag69@gmail.com',
        Subject: 'New message from your website',
        Body: message
      }).then(() => {
        console.log(this.email,this.body);
      });
      this.modal=false;
      this.email='';
      this.message='';
      this.sent=true;
    }

  }
}
</script>


