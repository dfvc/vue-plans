<template>
    <div class="plan__meter">
        <div class="plan__meter-item">
            <span class="plan__meter-item-min is-size-7 is-pulled-left">{{ config.minEmailAccounts }}</span>
            <span class="plan__meter-item-max is-size-7 is-pulled-right">{{ config.maxEmailAccounts }}</span>
            <progress class="progress is-info is-radiusless" :value="emailAccounts" :max="config.maxEmailAccounts"></progress>
        </div>
        <div class="plan__meter-item">
            <span class="plan__meter-item-min is-size-7 is-pulled-left">{{ config.minStorage }}</span>
            <span class="plan__meter-item-max is-size-7 is-pulled-right">{{ config.maxStorage }}</span>
            <progress class="progress is-info is-radiusless" :value="storage" :max="config.maxStorage"></progress>
        </div>
        <div class="plan__meter-item">
            <span class="plan__meter-item-min is-size-7 is-pulled-left">{{ config.minProjects }}</span>
            <span class="plan__meter-item-max is-size-7 is-pulled-right">{{ config.maxProjects }}</span>
            <progress class="progress is-info is-radiusless" :value="projects" :max="config.maxProjects"></progress>
        </div>
    </div>
</template>


<script>
    export default {
        data() {
            return {
                config: {
                    minEmailAccounts: 0,
                    maxEmailAccounts: 20,
                    minStorage: 0,
                    maxStorage: 100,
                    minProjects: 0,
                    maxProjects: 15
                },
                emailAccounts: 0,
                storage: 0,
                projects: 0
            }
        },

        created() {
            Event.$on('enterPlanCard', (specs) => {
                this.updateSpecs(specs);
            });

            Event.$on('exitPlanCard', () => {
                this.resetSpecs();
            });
        },

        methods: {
            resetSpecs() {
                this.emailAccounts = 0;
                this.storage = 0;
                this.projects = 0;
            },

            updateSpecs(specs) {
                this.emailAccounts = specs.emailAccounts;
                this.storage = specs.storage;
                this.projects = specs.projects;
            }
        }
    }
</script>


<style lang="scss">
    $spacing-md: 16px;
    $spacing-sm: $spacing-md / 2;
    $spacing-lg: $spacing-md * 2;

    $transition-speed:    .15s;
    $transition-function: ease;

    .plan {

        &__meter {
            padding: $spacing-md;
            background-color: #fff;
            box-shadow: 0 2px 3px rgba(10, 10, 10, 0.1), 0 0 0 1px rgba(10, 10, 10, 0.1);
        }

        &__meter-item {
            margin-top: $spacing-md;
        }
    }

    .progress {

        &::-webkit-progress-value {
            transition: width $transition-speed $transition-function;
        }
    }
</style>
