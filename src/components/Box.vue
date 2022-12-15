<template>
    <div class="box has-text-weight-bold">
        <slot></slot>
    </div>
</template>
<script lang="ts">
import { defineComponent } from 'vue';
export default defineComponent ({
    name: 'BoxView'
});
</script>

<style scoped>
.box{
    background-color: #48aed6;
    color: #FFFFFF;
}
</style>