<template>
  <div class="h-screen">
    <div class="text-center mt-16">
<!--      <v-app-bar :elevation="2">-->
        <v-system-bar>
          <v-icon icon="mdi-wifi-strength-4"></v-icon>
          <v-icon icon="mdi-signal" class="ms-2"></v-icon>
          <v-icon icon="mdi-battery" class="ms-2"></v-icon>

          <span class="ms-2">3:13PM</span>
        </v-system-bar>
<!--      </v-app-bar>-->

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
                    @click="isActive.value = false"
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
            text="My skill is to make my sweetheart happy"
          >
          </v-expansion-panel>
        </v-expansion-panels>
      </v-card>



    </div>

  </div>
  <v-footer border class="text-caption">2023 - Dexter Bagtang </v-footer>
</template>

<script setup>
  //
</script>
