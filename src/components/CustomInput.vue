<template>
  <div>
    <label>
      {{ label }}
      <input :value="value" @input="$emit('input',$event.target.value)"/>
    </label>
  </div>
</template>

<script>
export default{
  name: "CustomInput",
  props: {
    label: {
      type: String,
      required: true
    },
    value: {
      type: String,
      required: true
    }
  }
}
</script>