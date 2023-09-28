<template>
    <div>
        <v-dialog v-model="opendialog" width="auto" transition="dialog-bottom-transition" persistent>
            <v-container>
                <v-card class="mx-auto">
                    <v-card-text class="mx-8">
                        <v-row align="center" no-gutters>
                            <v-col cols="6">
                                <v-img :src="viewPerson.thumbnail.path + '.' + viewPerson.thumbnail.extension"
                                    max-height="500" width="850" cover />
                            </v-col>
                            <v-col cols="6">
                                <div class="mx-10">
                                    <h1 class="text-center">{{ viewPerson.name }}</h1>
                                    <h3 class="my-3"> Description </h3>
                                    <p class="my-2" >{{ viewPerson.description || "Not found description" }}</p>
                                    <ul>
                                        <li class="my-2" v-if="viewPerson.comics.returned != 0">
                                            <h3 class="d-inline"> Number of comics: </h3>
                                            <p class="d-inline">{{ viewPerson.comics.returned }}</p>
                                        </li>
                                        <li class="my-2" v-if="viewPerson.events.returned != 0">
                                            <h3 class="d-inline"> Number of events: </h3>
                                            <p class="d-inline">{{ viewPerson.events.returned }}</p>
                                        </li>
                                        <li class="my-2" v-if="viewPerson.stories.returned != 0">
                                            <h3 class="d-inline"> Number of stories: </h3>
                                            <p class="d-inline">{{ viewPerson.stories.returned }}</p>
                                        </li>
                                        <li class="my-2" v-if="viewPerson.series.returned != 0">
                                            <h3 class="d-inline"> number of series: </h3>
                                            <p class="d-inline">{{ viewPerson.series.returned }}</p>
                                        </li>
                                    </ul>
                                    <h3 v-if="viewPerson.series.returned != 0"> Some series </h3>
                                    <v-list lines="one">
                                        <v-list-item v-for="(serie, i ) in viewPerson.series.items.slice(0, 3)" :key="serie">
                                            <h3> {{ serie.name }} </h3>
                                        </v-list-item>
                                    </v-list>
                                </div>
                            </v-col>
                        </v-row>
                    </v-card-text>
                    <v-btn block color="red" variant="flat" @click="closeDialog()">Close</v-btn>
                </v-card>
            </v-container>
        </v-dialog>
    </div>
</template>
<script setup>

const props = defineProps({
    viewdialog: {
        type: Boolean,
        required: true
    },
    person: {
        type: Object,
        required: true
    }
})

const emit = defineEmits(['close'])

onBeforeMount(() => {
    viewPerson.value = props.person
    opendialog.value = props.viewdialog
})

const viewPerson = ref({})
const opendialog = ref(false)


const closeDialog = () => {
    opendialog.value = false
    emit('close')
}

</script>
