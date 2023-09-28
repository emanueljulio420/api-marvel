<template>
    <div class="aling-center">
        <v-container class="text-center">
            <h1>Characters</h1>
            <v-row class="my-10">
                <v-col v-for="character of characters" :key="character.id" cols="4" class="my-5">
                    <v-card class="mx-auto" max-width="344">
                        <v-img :src="character.thumbnail.path + '.' + character.thumbnail.extension" height="400" width="auto" cover />
                        <v-card-title>{{ character.name }}</v-card-title>
                        <v-card-actions>
                            <v-btn color="red" variant="flat" @click="viewCharacter(character)">More information</v-btn>
                        </v-card-actions>
                    </v-card>
                </v-col>
            </v-row>
        </v-container>
        <character-person v-if="dialog == true" :viewdialog="dialog" :person="viewPerson" @close="closeCharacter" />
    </div>
</template>
<script setup>

const dialog = ref(false);
const characters = ref({})
const viewPerson = ref(null)

onBeforeMount(() => {
    loadCharacters();
});

import axios from 'axios';

const loadCharacters = async () => {
    const url = "https://gateway.marvel.com:443/v1/public/characters?ts=1&apikey=6bf50acb86ffa16f4efaa1bb5a49c59a&hash=d3ed7be405fe7b5dfaa8483c5ec45f07&limit=30";
    const { data } = await axios.get(url);
    characters.value = data.data.results
    console.log(characters.value)
};

const viewCharacter = (item) => {
    viewPerson.value = { ...item}
    dialog.value = true;
};

const closeCharacter = () => {
    dialog.value = false;
}

</script>
