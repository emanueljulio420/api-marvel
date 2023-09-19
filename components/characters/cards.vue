<template>
    <div v-for="character of characters" class="d-flex">
        <v-card class="mx-auto my-8" max-width="400">
            <v-img src="https://cdn.vuetifyjs.com/images/cards/sunshine.jpg" height="400" width="400" cover />
            <v-card-title>{{ character.name }}</v-card-title>
            <v-card-actions>
                <v-btn color="red" variant="flat">
                    Mas informacion
                </v-btn>
            </v-card-actions>
        </v-card>
    </div>
</template>
<script setup>

import axios from 'axios';

const characters = ref({})

onBeforeMount(() => {
    loadCharacters();
});

const loadCharacters = async () => {
    const url = "https://gateway.marvel.com:443/v1/public/characters?ts=1&apikey=6bf50acb86ffa16f4efaa1bb5a49c59a&hash=d3ed7be405fe7b5dfaa8483c5ec45f07";
    const { data } = await axios.get(url);
    characters.value = data.data.results
    console.log(characters.value)
};
</script>
