<script>
import { store } from "../store.js";

export default {
    name: 'DropDown',
    data() {
        return {
            store,
            emptyString: "",
        }
    },
    methods: {
        // archSelectFunc(string) {
        //     store.archSelect = string;
        // }
    },
}

</script>

<template>

    <!-- SELECT MENU -->
    <select name="archetypes" id="archetype-select" v-model="store.archSelect" @change="$emit('archSelected')"
        class="btn btn-secondary btn-sm dropdown-toggle my-3 bg-white text-black">
        <!-- Option to reset -->
        <option value="">Select all</option>
        <!-- List of archetypes -->
        <option v-for="(item, idx) in store.archList" :key="idx" :value="item.archetype_name">{{ item.archetype_name }}
        </option>
    </select>
</template>

<style lang="scss" scoped>

</style>