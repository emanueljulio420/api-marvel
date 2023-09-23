<template>
    <div>
        <v-card class="mx-auto" max-width="344">
            <v-img src="https://cdn.vuetifyjs.com/images/cards/sunshine.jpg" height="200px" cover></v-img>
            <v-card-title>Top western road trips</v-card-title>
            <v-card-subtitle>1,000 miles of wonder</v-card-subtitle>
            <v-card-actions>
                <v-btn color="red" variant="flat" @click="viewCharacter()">Explore</v-btn>
            </v-card-actions>
        </v-card>
        <v-dialog v-model="dialog" width="auto" transition="dialog-bottom-transition">
            <character-person/>
        </v-dialog>
    </div>
</template>
<script setup>

const dialog = ref(false);

const viewCharacter = () => {
    dialog.value = true
};
</script>