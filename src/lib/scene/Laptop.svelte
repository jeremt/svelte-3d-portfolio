<script lang="ts">
    import {T, useLoader} from '@threlte/core';
    import {TextureLoader} from 'three';

    export let progress: number;
    export let screenSrc: string;

    $: screenMap = useLoader(TextureLoader).load(screenSrc);
    $: opacity = progress < 0.8 ? 1 : 1 - (progress - 0.8) * 5;
</script>

<T.Group name="Laptop" position.x={progress < 0.8 ? 0 : (progress - 0.8) * 15} position.y={0.5} rotation.x={0.2} rotation.y={progress * 26}>
    <T.Group rotation.x={-0.2}>
        <T.Mesh name="Screen">
            <T.BoxGeometry args={[1, 0.6, 0.02]} />
            {#if $screenMap}
                <T.MeshPhysicalMaterial map={$screenMap} roughness={0} metalness={0.2} {opacity} transparent={true} />
            {/if}
        </T.Mesh>
        <T.Mesh name="Screen-Back" position.z={-0.01}>
            <T.BoxGeometry args={[1.1, 0.7, 0.03]} />
            <T.MeshPhysicalMaterial color="#eeeeee" metalness={0.9} roughness={0.3} {opacity} transparent={true} />
        </T.Mesh>
    </T.Group>
    <T.Mesh name="Screen-Bottom" position={[0, -0.35, 0.4]}>
        <T.BoxGeometry args={[1.1, 0.03, 0.7]} />
        <T.MeshPhysicalMaterial metalness={0.9} roughness={0.4} {opacity} transparent={true} />
    </T.Mesh>
    <T.Mesh name="Keyboard" position={[0, -0.33, 0.35]}>
        <T.BoxGeometry args={[0.9, 0.01, 0.4]} />
        <T.MeshPhysicalMaterial color="#555555" metalness={0.5} {opacity} transparent={true} />
    </T.Mesh>
</T.Group>
