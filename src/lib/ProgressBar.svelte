<script lang="ts">
    export let progress = 0;
</script>

<div class="bar" style:--progress={progress} />

<style>
    .bar {
        position: absolute;
        width: 20rem;
        height: 1rem;
        background-color: rgba(0, 0, 0, 0.3);
    }
    .bar::after {
        display: block;
        content: '';
        position: relative;
        width: calc(var(--progress) * 100%);
        height: 100%;
        background-color: var(--color-accent);
    }
</style>
