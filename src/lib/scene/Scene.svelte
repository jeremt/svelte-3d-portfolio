<script lang="ts">
    import {T} from '@threlte/core';
    import Laptop from '$lib/scene/Laptop.svelte';
    import {Environment, Float} from '@threlte/extras';

    export let progress: number;

    let screenSrc = '/portfolio.png';
    $: {
        if (progress >= 0.1 && progress <= 0.35) {
            screenSrc = '/voltapp.png';
        } else if (progress > 0.35 && progress <= 0.6) {
            screenSrc = '/codepassport.png';
        } else if (progress > 0.6) {
            screenSrc = '/ttmc.png';
        } else {
            screenSrc = '/portfolio.png';
        }
    }
</script>

<T.PerspectiveCamera makeDefault position={[0, 0, 5]} fov={35} rotation={[0, 0, 0]} />

<T.DirectionalLight castShadow intensity={0.8} position={[3, 8, 12]} />
<T.DirectionalLight castShadow intensity={0.3} position={[0, 6, 15]} />
<T.AmbientLight intensity={0.3} />

<Environment files="/env.hdr" />

<Float floatingRange={[-0.05, 0.05]} speed={5}>
    <Laptop {screenSrc} {progress} />
</Float>
