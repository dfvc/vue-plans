<template>
    <section class="section">
          <div class="container">
              <div class="plan__cards columns">
                  <div v-for="plan in plans" v-if="plan.enabled" class="plan__card column">
                      <plan-card v-bind="plan"></plan-card>
                  </div>
              </div>

              <div class="plan__specs columns">
                  <div class="column">
                      <plan-specs></plan-specs>
                  </div>
              </div>
          </div>
    </section>
</template>


<script>
    import PlanCard from './PlanCard.vue';
    import PlanSpecs from './PlanSpecs.vue';

    export default {
        components: {
            PlanCard,
            PlanSpecs
        },

        data() {
            return {
                plans: [
                    {
                        id: 1,
                        name: 'Basic',
                        image: 'https://via.placeholder.com/256x256',
                        description: 'Plan A description',
                        highlights: [
                            'Plan A highlight 1',
                            'Plan A highlight 2',
                            'Plan C highlight 3'
                        ],
                        price: '15€<div class="is-size-7">per month</div>',
                        specs: {
                            emailAccounts: 1,
                            storage: 10,
                            projects: 1,
                        },
                        subscribeAction: {
                            label: 'Action 1',
                            iconCls: '',
                            url: '#'
                        },
                        moreAction: {
                            label: 'Action 2',
                            iconCls: '',
                            url: '#'
                        },
                        enabled: true
                    },
                    {
                        id: 2,
                        name: 'Standard',
                        image: 'https://via.placeholder.com/256x256',
                        description: 'Plan B description',
                        highlights: [
                            'Plan B highlight 1',
                            'Plan B highlight 2',
                            'Plan B highlight 3'
                        ],
                        price: '25€<div class="is-size-7">per month</div>',
                        specs: {
                            emailAccounts: 5,
                            storage: 50,
                            projects: 5,
                        },
                        subscribeAction: {
                            label: 'Action 1',
                            iconCls: '',
                            url: '#'
                        },
                        moreAction: {
                            label: 'Action 2',
                            iconCls: '',
                            url: '#'
                        },
                        enabled: true
                    },
                    {
                        id: 3,
                        name: 'Premium',
                        image: 'https://via.placeholder.com/256x256',
                        description: 'Plan C description',
                        highlights: [
                            'Plan C highlight 1',
                            'Plan C highlight 2',
                            'Plan C highlight 3'
                        ],
                        price: '50€<div class="is-size-7">per month</div>',
                        specs: {
                            emailAccounts: 20,
                            storage: 100,
                            projects: 15,
                        },
                        subscribeAction: {
                            label: 'Action 1',
                            iconCls: '',
                            url: '#'
                        },
                        moreAction: {
                            label: 'Action 2',
                            iconCls: '',
                            url: '#'
                        },
                        enabled: true
                    }
                ]
            }
        }
    }
</script>


<style lang="scss">
</style>
