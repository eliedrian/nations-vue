<template>
  <g>
    <path v-for="nation in nations" :key="nation.name" :d="scale.line(zip(nation))"
      fill="none" :stroke="scale.color(nation.region)" stroke-miter-limit="1"
      stroke-width="1.5" opacity="0.3" />
  </g>
</template>

<script>
export default {
  name: 'NationsLines',

  props: {
    nations: {
      type: Array,
      required: true
    },
    scale: {
      type: Object,
      required: true
    }
  },

  methods: {
    zip: function(nation) {
      return nation.income.map((income, index) => ({
        'income': income,
        'lifeExpectancy': nation.lifeExpectancy[index]
      }));
    }
  }
}
</script>
