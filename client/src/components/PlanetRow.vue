<template>
<!--    create template element; provide object locations-->
    <tr v-bind:key="planet.resource1">
        <td>{{ planet.name }}</td>
        <td>{{ planet.weather }}</td>
        <td>{{ planet.resource1 }}</td>
        <td>{{ planet.resource2 }}</td>
        <td>{{ planet.resource3 }}</td>
        <td>{{ planet.galacticCoords }}</td>
        <td>{{ planet.glyphs }}</td>
        <td>{{ planet.comments }}</td>
<!--        admin menu to only show delete option when clicked-->
        <td v-show="admin">
            <img class='delete-icon' v-on:click="deletePlanet(planet)" src="@/assets/delete2.png">
        </td>
    </tr>
</template>

<script>

    export default {
        name: 'PlanetRow',
        props: {
            planet: Object,
            admin: Boolean,
        },
        methods: {
            // emit back to app.vue to delete planet
            deletePlanet(planet) {
                if(confirm(`Purge ${planet.name}?`)) {
                    this.$emit('delete-planet', planet)
                }
            },
        }
    }
</script>

<style>
    .delete-icon {
        width: 15%;
    }
</style>