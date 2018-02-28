# vue-simple-datetime-picker

> Finally a simple, lightweight and **self-contatined** date, time, and datetime picker for Vue

This simple datetime picker takes advantage of the tiny dpicker and Moment libraries to provide robust, flexible date, time and datetime picker components for use in Vue. Bootstrap free-zone.

## Installation

``` bash
# install dependencies
npm i vue-simple-datetime-picker -s 

# import components where required
import SimpleDateTimePicker from 'vue-simple-datetime-picker'

export default {
  component: {
    SimpleDateTimePicker
  },
  render () {
    return <SimpleDateTimePicker v-model='date/time/datetime string' options={options} format='YYYY-MM-DD HH:mm' />
  }
}

```

## Options and settings

Vue Simple Datetime Picker supports all options offered by DPicker, more information available here:
https://soyuka.github.io/dpicker/#/_api

Pass an object to the 'options' prop on the SimpleDateTimePicker to override defaults.

## Todo

* Add support for Pickerjs events and methods
* Include CSS in component automatically
* Add some (any!) tests