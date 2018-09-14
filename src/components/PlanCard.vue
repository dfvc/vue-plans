<template>
    <div :id="'plan-' + id" @mouseenter="onEnterCard" @mouseleave="onExitCard" class="card">
        <header class="card-header has-background-info">
            <p class="card-header-title has-text-white">{{ name }}</p>
        </header>
        <div class="card-content">
            <div class="content">
                <div class="plan__price is-size-1 has-text-centered has-text-weight-bold" v-html="price"></div>
                <div class="plan__description has-text-justified has-text-grey">{{ description }}</div>
                <ul class="plan__highlights has-text-grey">
                    <li v-for="highlight in highlights">{{ highlight }}</li>
                </ul>
            </div>
        </div>
        <footer class="card-footer">
            <a :href="subscribeAction.url" class="card-footer-item has-background-grey-darker has-text-white">
                {{ subscribeAction.label }}
                <span v-if="subscribeAction.iconCls != ''" class="icon">
                    <i :class="subscribeAction.iconCls" aria-hidden="true"></i>
                </span>
            </a>
            <a v-if="moreAction" :href="moreAction.url" class="card-footer-item has-background-grey-darker has-text-white">
                {{ moreAction.label }}
                <span v-if="moreAction.iconCls != ''" class="icon">
                    <i :class="moreAction.iconCls" aria-hidden="true"></i>
                </span>
            </a>
        </footer>
    </div>
</template>


<script>
    export default {
        props: {
            id: {
                type: Number,
                required: true
            },
            name: {
                type: String,
                required: true
            },
            image: {
                type: String,
                required: false
            },
            description: {
                type: String,
                required: false
            },
            highlights: {
                type: Array,
                required: true
            },
            price: {
                type: String,
                required: true
            },
            specs: {
                type: Object,
                required: true
            },
            subscribeAction: {
                type: Object,
                required: true
            },
            moreAction: {
                type: Object,
                required: false
            },
            enabled: {
                type: Boolean,
                required: true
            }
        },

        methods: {
            onEnterCard: function() {
                Event.$emit('enterPlanCard', this.specs);
            },

            onExitCard: function() {
                Event.$emit('exitPlanCard');
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

    .card-header-title {
      justify-content: center;
    }

    .plan {

        &__card {

            .card {
                margin-top: $spacing-sm;
                transition: all $transition-speed $transition-function;

                &:hover {
                    margin-top: 0;
                    box-shadow: 0 8px 30px rgba(10, 10, 10, 0.1), 0 0 0 1px rgba(10, 10, 10, 0.1);
                }
            }

            .plan {

                &__price {
                    line-height: 1;
                }

                &__description {
                    margin-top: $spacing-sm * 3;
                }

                &__highlights {
                    margin-left: $spacing-sm;
                    list-style: none;
                }
            }
        }
    }
</style>
