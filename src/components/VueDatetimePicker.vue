<template>
  <div ref='pickerContainer' class='vue-simple-date-time-picker'>
    <input ref='pickerField' :value='value' v-on:focus='lazyInitialisePicker()' />
  </div>
</template>

<script>
import DPicker from 'dpicker/dist/dpicker.datetime.min'
import adapter from './adapter.js'

DPicker.dateAdapter = adapter

export default {
  name: 'VueSimpleDatetimePicker',
  props: ['options', 'value', 'format', 'type'],
  data () {
    return {
      date: '',
      thePicker: false,
      defaultOptions: {
        format: this.format,
        time: true
      }
    }
  },
  computed: {
    model () {
      if (this.value) {
        let date = new Date(this.value)
        return adapter.format(date, this.format)
      }
      return false
    },
    optionSet () {
      return {
        ...this.defaultOptions,
        model: this.model,
        time: this.$props.type && (this.$props.type === 'time' || this.$props.type === 'datetime') || false,
        ...this.options
      }
    }
  },
  mounted () {
    if (this.value) {
      this.initialisePicker()
    }
  },
  methods: {
    lazyInitialisePicker () {
      if (!this.thePicker) {
        this.initialisePicker()
        this.thePicker.display = true
      }
    },
    initialisePicker () {
      this.thePicker = new DPicker(this.$refs.pickerField, this.optionSet)
      this.thePicker.onChange = this.updateParent
    },
    updateParent () {
      this.$emit('input', this.thePicker.input)
    }
  }
}
</script>
<style lang="scss">
$grey: #e6e6e6;
$highlight: #ffab40;
.vue-simple-date-time-picker {
  position:relative;
  width: auto;
  display:table;
  font-size: 1em;
  font-family: inherit;
}
.vue-simple-date-time-picker input {
  z-index: 1;
}
.dpicker-container {
  z-index: 2;
}
.dpicker-invisible {
  display: none;
}
.dpicker-visible {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
  position: absolute;
  top: 100%;
  left: 0;
  min-width: 300px;
  background-color: white;
  border: 1px solid $grey;
  padding: 1em;
}

.dpicker-month, .dpicker-year {
  order: 1;
}
table {
  order: 2;
}
.dpicker-time {
  order: 3;
}

select {
  margin: 0 1em;
}

.dpicker-inactive {
  color: $grey;
}
table button {
  appearance: none;
  border: none;
  background-color: transparent;
  font-size: inherit;
  font-family: inherit;
  padding: 0.5em 1em;
  &:hover {
    background-color: $grey;
  }
  &.dpicker-active {
    font-weight: bold;
    background-color: $highlight;
  }
}
</style>