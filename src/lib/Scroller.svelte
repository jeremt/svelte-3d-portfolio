<script lang="ts">
    /**
     * The number of pages you want to scroll.
     */
    export let pages: number = 5;

    /**
     * The current scroll progress value (between 0 and 1).
     */
    export let scroll = 0;

    let wrapperEl: HTMLDivElement;

    // update the scroll from outside
    $: if (wrapperEl) {
        wrapperEl.scrollTop = scroll * (wrapperEl.scrollHeight - wrapperEl.clientHeight);
    }

    function updateProgress(event: UIEvent) {
        const el = event.currentTarget as HTMLElement;
        if (el !== null) {
            scroll = Math.floor(el.scrollTop) / (el.scrollHeight - el.clientHeight);
        }
    }
</script>

<div bind:this={wrapperEl} class="wrapper" on:scroll={updateProgress}>
    <div class="background"><slot /></div>
    <div class="foreground" style="--pages: {pages}"><slot name="foreground" /></div>
</div>

<style>
    .wrapper {
        position: absolute;
        top: 0;
        width: 100%;
        height: 100%;
        overflow: auto;
    }
    .background {
        position: sticky;
        top: 0;
        width: 100%;
        height: 100%;
        overflow: hidden;
    }
    .foreground {
        top: 0;
        width: 100%;
        height: calc(var(--pages) * 100%);
        position: absolute;
        pointer-events: none;
    }
</style>
