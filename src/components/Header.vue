<script setup>
defineProps({
  msg: {
    type: String,
    required: true
  }
})
</script>

<template>
        <div class="greetings">
            <h1 class="green">{{ msg }}</h1>
            <p> <h4>    This website show images created by AI of people that does not exist.   </h4> </p>

        </div>
</template>