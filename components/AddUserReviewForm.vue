<script setup>
const dialog = ref(false);
const rating = ref(0);
</script>
<template>
  <v-row justify="center">
    <v-dialog v-model="dialog" width="1024">
      <template v-slot:activator="{ props }">
        <v-btn color="primary" v-bind="props"> Clicca qui </v-btn>
      </template>
      <v-card>
        <v-card-title>
          <span class="text-h5">Scrivici la tua opinione!</span>
        </v-card-title>
        <v-card-text>
          <v-container>
            <v-row>
              <v-col cols="12" sm="6" md="4">
                <v-text-field label="Nome*"  variant="solo" required></v-text-field>
              </v-col>
              <v-col cols="12" sm="6" md="4">
                <v-text-field
                  label="Cognome*"
                  hint="example of persistent helper text"
                  persistent-hint
                  variant="solo"
                  required
                ></v-text-field>
              </v-col>
              <v-col cols="12" sm="6" md="4">
                <v-text-field label="Email*"  variant="solo" required></v-text-field>
              </v-col>

              <v-col cols="12" sm="8">
                <v-textarea label="Scrivi qualcosa ecc ecc"  variant="solo"></v-textarea>
              </v-col>
              <v-col cols="12" sm="4">
                <div class="text-center">
                <span class="text-h5">Dai un voto!</span>
                  <v-rating v-model="rating" hover></v-rating>
                </div>
              </v-col>
            </v-row>
          </v-container>
          <small>*campi obbligatori</small>
        </v-card-text>
        <v-card-actions>
          <v-spacer></v-spacer>
          <v-btn color="red" variant="text" @click="dialog = false">
            Chiudi
          </v-btn>
          <v-btn color="primary" variant="text" @click="dialog = false">
            Salva
          </v-btn>
        </v-card-actions>
      </v-card>
    </v-dialog>
  </v-row>
</template>
