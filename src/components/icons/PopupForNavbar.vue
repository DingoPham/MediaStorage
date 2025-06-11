<script setup>
defineProps({
    isOpen: Boolean
})
defineEmits(['toggle'])
</script>

<template>
    <div @click="$emit('toggle')" class="button">
        {{ isOpen ? '<' : '>' }}
    </div>
</template>

<style scoped>
.button{
  padding: 10px 20px;
  margin: 10px;
  color: white;
  border: none;
  cursor: pointer;
}
</style>