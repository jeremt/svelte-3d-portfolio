<script lang="ts">
    import {T, useThrelte} from '@threlte/core';
    import {Environment, Float, useTexture} from '@threlte/extras';
    import Macbook from './Macbook.svelte';
    import {onMount} from 'svelte';

    export let scroll: number;

    let screenSrc = '/portfolio.png';
    $: {
        if (scroll >= 0.1 && scroll <= 0.35) {
            screenSrc = '/voltapp.png';
        } else if (scroll > 0.35 && scroll <= 0.6) {
            screenSrc = '/codepassport.png';
        } else if (scroll > 0.6) {
            screenSrc = '/ttmc.png';
        } else {
            screenSrc = '/portfolio.png';
        }
    }

    const {scene} = useThrelte();

    let fov = 40;
    onMount(() => {
        if (window.innerWidth > 640) {
            fov = 35;
        }
    });
</script>

<svelte:window
    on:resize={() => {
        if (window.innerWidth > 640) {
            fov = 35;
        } else {
            fov = 40;
        }
    }}
/>

<T.PerspectiveCamera makeDefault position={[0, 0, 5]} {fov} rotation={[0, 0, 0]} />

<T.DirectionalLight castShadow intensity={0.8} position={[10, 8, 4]} />
<T.DirectionalLight castShadow intensity={0.3} position={[-5, 6, 15]} />
<T.AmbientLight intensity={0.3} />

<T.Fog
    on:create={({ref}) => {
        scene.fog = ref;
    }}
    on:cleanup={() => {
        scene.fog = null;
    }}
    color="#1b1b1b"
    near={1}
    far={20}
/>
<Environment files="/env.hdr" />

<Float floatingRange={[-0.05, 0.05]} speed={5} rotationSpeed={2} rotationIntensity={0.3}>
    <Macbook {screenSrc} {scroll} />
</Float>
