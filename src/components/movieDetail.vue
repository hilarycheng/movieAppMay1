<template>
<div>
    <ul>
        <li v-for="ninja in ninjas" :key="ninja.name" @click="ninja.show =!ninja.show">
            <h2>{{ ninja.name }}</h2>
            <h3 v-show="ninja.show">{{ ninja.speciality }}</h3>
        </li>
    </ul>
</div>
</template>

<script>
export default {
    data() {
        return {
            ninjas: [
                {name: 'Ryu', speciality:'Vue Components', show: false},
                {name: 'Louis', speciality:'HTML', show: false},
                {name: 'Peter', speciality:'JS', show: false},
            ],
            show: false,
        }
    }

}
</script>

<style>

</style>