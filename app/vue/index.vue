<template>
    <div class="global-container">
        <top-container></top-container>
        <bottom-container></bottom-container>
    </div>
</template>


<script>
    module.exports = {
        components: {
            'bottom-container': require('./components/bottom-container.vue'),
            'top-container': require('./components/top-container.vue') 
        }
    }
</script>