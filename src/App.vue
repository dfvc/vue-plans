<template>
    <div id="app">
        <section class="hero is-info is-bold ">
            <div class="hero-body">
                <div class="container">
                    <h1 class="title">Company Name</h1>
                    <h2 class="subtitle">Choose your plan...</h2>
                </div>
            </div>
        </section>
        <plans></plans>
    </div>
</template>


<script>
    import Plans from './components/Plans.vue';

    export default {
        name: 'app',

        components: {
            Plans
        }
    }
</script>


<style lang="scss">
    html,
    body {
        background-color: #f0f3f5;
    }
</style>
