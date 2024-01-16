<template>
    <div v-for="event, i in sortedEvents" :key="i">
        <div class="block">
            <h3>{{event.name}}</h3>
            <b>{{event.date}}</b>
            <i>{{event.description}}</i>
        </div>
    </div>
</template>

<script setup>
import { ref, onMounted, watchEffect } from 'vue';

const props = defineProps({
    events: {
        type: Array,
        required: true,
    },
    units: {
        type: Array,
        default: () => (["BC, AC"])
    },
})

const sortedEvents = ref([]);

// Méthode computed pour trier le tableau
const computeSortedEvents = () => {
    sortedEvents.value = [...props.events].sort((a, b) => {
        // Assurez-vous d'ajuster cela en fonction de la logique de tri souhaitée
        return new Date(a.date) - new Date(b.date);
    });
};

// Appelez la méthode computed lors de la création du composant et à chaque modification de `props.events`
onMounted(computeSortedEvents);
watchEffect(() => {
    computeSortedEvents();
});
</script>

<style>
.block{
    display: flex;
    flex-direction :column;
    border: 1px solid beige;
    border-radius: 5px;
    margin: 10px;
    padding: 5px 10px;
}
</style>