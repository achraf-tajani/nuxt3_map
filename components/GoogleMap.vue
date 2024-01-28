<template>
    <div>
        <div ref="map_element" id="map"></div>
    </div>
</template>

<script>
import mapStore from "~~/stores/MapStore.ts";

export default defineComponent({
    setup() {
        // Stores
        const map_store = mapStore();
        // Exemple de positions de marqueurs
        const markerPositions = [
            { lat: 60.3913, lng: 5.3221 },  // Exemple de coordonnées
            { lat: 59.9139, lng: 10.7522 }, // Autre exemple
        ]
        // Refs
        const map_element = ref();

        onMounted(() => {
            map_store.google_map_html = map_element.value;
            map_store.initializeGoogleMap();
            markerPositions.forEach(position => {
                map_store.addMarker(position);
            });
        });

        return { map_element };
    },
});
</script>

<style scoped>
#map {
    /* Define Map measures */
    height: 400px;
    width: 50%;

    /* Center Map */
    margin: auto;
}
</style>