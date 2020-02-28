<template>
    <v-card
            class="mx-auto"
            max-width="400"
    >
        <v-img
                class="white--text align-end"
                height="200px"
                v-bind:src="img"
        >

        </v-img>
        <v-card-title class="black--text">{{name}}</v-card-title>
        <v-card-text class="text--primary">
           <p>{{description}}</p>
        </v-card-text>
    </v-card>
</template>

<script>
    export default {
        name: "character",
        props:{
            name:String,
            description:String,
            img:String,
        }
    }

</script>

<style scoped>

</style>