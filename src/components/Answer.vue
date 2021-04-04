<template>
    <div class="self-card text-center">
        <h3>Isn't it pretty ?</h3>
        <hr>
        <button class="btn btn-primary" @click="onNextQuestion">Flip back!</button>
    </div>
</template>
<style>

</style>
<script>

    export default{
        methods: {
            onNextQuestion() {
                this.$emit('confirmed');
            }
        }
    }
</script>
