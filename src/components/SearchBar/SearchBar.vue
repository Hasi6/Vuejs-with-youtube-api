<template>
  <div>
    <input @input="$emit('termChange', $event.target.value)" />
  </div>
</template>

<script>

export default {
  name: "Search_Bar"
};
</script>