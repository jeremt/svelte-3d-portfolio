<script>
    import {Canvas} from '@threlte/core';
    import Scene from '$lib/scene/Scene.svelte';
    import Scroller from '$lib/Scroller.svelte';
    import {useProgress} from '@threlte/extras';
    import {tweened} from 'svelte/motion';

    const {progress} = useProgress();
    const tweenedProgress = tweened($progress, {
        duration: 800,
    });
    $: tweenedProgress.set($progress);

    let scroll = 0;
</script>

<svelte:head>
    <title>Jeremie's Portfolio</title>
    <meta name="description" content="Simple 3D Porfolio made with Threlve for pegadogique purposes" />
</svelte:head>

<Scroller bind:scroll pages={3}>
    <div id="page" slot="foreground">
        <header>
            <h1>Salut, I'm Jérémie!</h1>
            <p class="subtitle">I write or teach code sometimes<br />Scroll to see what 👀</p>
        </header>
        <section id="voltapp">
            <h2>Voltapp</h2>
            <p>Voltapp is a no-code tool to create web apps using a graph based visual coding. This is my main project as a Co-founder of Celestory company.</p>
            <a role="button" href="https://voltapp.tech/" target="_blank">See project</a>
        </section>
        <section id="codepassport">
            <h2>Code Passport</h2>
            <p>
                Code Passport is an interactive website to learn code (JS, HTML & CSS). I'm developping it on my spare time with my friend <a
                    href="https://xvt.vercel.app">Vi</a
                >.
            </p>
            <a role="button" href="https://codepassport.dev" target="_blank">See project</a>
        </section>
        <section id="ttmc-for-devs">
            <h2>TTMC for devs</h2>
            <p>
                Open-source board game inspired by the french board game ttmc repurposed to learn dev/tech concepts. Add your own cards <a
                    href="https://ttmc-ui.vercel.app">here</a
                >.
            </p>
            <a role="button" href="https://ttmc-ui.vercel.app" target="_blank">See project</a>
        </section>
        <section id="contact">
            <h2>Let's get in touch!</h2>
            <footer>
                <a class="social" target="_blank" href="https://www.linkedin.com/in/jeremie-taboada-16495959/">
                    <svg xmlns="http://www.w3.org/2000/svg" height="16" width="14" viewBox="0 0 448 512"
                        ><!--!Font Awesome Free 6.5.1 by @fontawesome - https://fontawesome.com License - https://fontawesome.com/license/free Copyright 2023 Fonticons, Inc.--><path
                            d="M100.3 448H7.4V148.9h92.9zM53.8 108.1C24.1 108.1 0 83.5 0 53.8a53.8 53.8 0 0 1 107.6 0c0 29.7-24.1 54.3-53.8 54.3zM447.9 448h-92.7V302.4c0-34.7-.7-79.2-48.3-79.2-48.3 0-55.7 37.7-55.7 76.7V448h-92.8V148.9h89.1v40.8h1.3c12.4-23.5 42.7-48.3 87.9-48.3 94 0 111.3 61.9 111.3 142.3V448z"
                        /></svg
                    >
                </a>
                <a class="social" target="_blank" href="https://instagram.com/jeremtab">
                    <svg xmlns="http://www.w3.org/2000/svg" height="16" width="14" viewBox="0 0 448 512"
                        ><!--!Font Awesome Free 6.5.1 by @fontawesome - https://fontawesome.com License - https://fontawesome.com/license/free Copyright 2023 Fonticons, Inc.--><path
                            d="M224.1 141c-63.6 0-114.9 51.3-114.9 114.9s51.3 114.9 114.9 114.9S339 319.5 339 255.9 287.7 141 224.1 141zm0 189.6c-41.1 0-74.7-33.5-74.7-74.7s33.5-74.7 74.7-74.7 74.7 33.5 74.7 74.7-33.6 74.7-74.7 74.7zm146.4-194.3c0 14.9-12 26.8-26.8 26.8-14.9 0-26.8-12-26.8-26.8s12-26.8 26.8-26.8 26.8 12 26.8 26.8zm76.1 27.2c-1.7-35.9-9.9-67.7-36.2-93.9-26.2-26.2-58-34.4-93.9-36.2-37-2.1-147.9-2.1-184.9 0-35.8 1.7-67.6 9.9-93.9 36.1s-34.4 58-36.2 93.9c-2.1 37-2.1 147.9 0 184.9 1.7 35.9 9.9 67.7 36.2 93.9s58 34.4 93.9 36.2c37 2.1 147.9 2.1 184.9 0 35.9-1.7 67.7-9.9 93.9-36.2 26.2-26.2 34.4-58 36.2-93.9 2.1-37 2.1-147.8 0-184.8zM398.8 388c-7.8 19.6-22.9 34.7-42.6 42.6-29.5 11.7-99.5 9-132.1 9s-102.7 2.6-132.1-9c-19.6-7.8-34.7-22.9-42.6-42.6-11.7-29.5-9-99.5-9-132.1s-2.6-102.7 9-132.1c7.8-19.6 22.9-34.7 42.6-42.6 29.5-11.7 99.5-9 132.1-9s102.7-2.6 132.1 9c19.6 7.8 34.7 22.9 42.6 42.6 11.7 29.5 9 99.5 9 132.1s2.7 102.7-9 132.1z"
                        /></svg
                    >
                </a>
                <a class="social" target="_blank" href="https://github.com/jeremt">
                    <svg xmlns="http://www.w3.org/2000/svg" height="16" width="15.5" viewBox="0 0 496 512"
                        ><!--!Font Awesome Free 6.5.1 by @fontawesome - https://fontawesome.com License - https://fontawesome.com/license/free Copyright 2023 Fonticons, Inc.--><path
                            d="M165.9 397.4c0 2-2.3 3.6-5.2 3.6-3.3 .3-5.6-1.3-5.6-3.6 0-2 2.3-3.6 5.2-3.6 3-.3 5.6 1.3 5.6 3.6zm-31.1-4.5c-.7 2 1.3 4.3 4.3 4.9 2.6 1 5.6 0 6.2-2s-1.3-4.3-4.3-5.2c-2.6-.7-5.5 .3-6.2 2.3zm44.2-1.7c-2.9 .7-4.9 2.6-4.6 4.9 .3 2 2.9 3.3 5.9 2.6 2.9-.7 4.9-2.6 4.6-4.6-.3-1.9-3-3.2-5.9-2.9zM244.8 8C106.1 8 0 113.3 0 252c0 110.9 69.8 205.8 169.5 239.2 12.8 2.3 17.3-5.6 17.3-12.1 0-6.2-.3-40.4-.3-61.4 0 0-70 15-84.7-29.8 0 0-11.4-29.1-27.8-36.6 0 0-22.9-15.7 1.6-15.4 0 0 24.9 2 38.6 25.8 21.9 38.6 58.6 27.5 72.9 20.9 2.3-16 8.8-27.1 16-33.7-55.9-6.2-112.3-14.3-112.3-110.5 0-27.5 7.6-41.3 23.6-58.9-2.6-6.5-11.1-33.3 2.6-67.9 20.9-6.5 69 27 69 27 20-5.6 41.5-8.5 62.8-8.5s42.8 2.9 62.8 8.5c0 0 48.1-33.6 69-27 13.7 34.7 5.2 61.4 2.6 67.9 16 17.7 25.8 31.5 25.8 58.9 0 96.5-58.9 104.2-114.8 110.5 9.2 7.9 17 22.9 17 46.4 0 33.7-.3 75.4-.3 83.6 0 6.5 4.6 14.4 17.3 12.1C428.2 457.8 496 362.9 496 252 496 113.3 383.5 8 244.8 8zM97.2 352.9c-1.3 1-1 3.3 .7 5.2 1.6 1.6 3.9 2.3 5.2 1 1.3-1 1-3.3-.7-5.2-1.6-1.6-3.9-2.3-5.2-1zm-10.8-8.1c-.7 1.3 .3 2.9 2.3 3.9 1.6 1 3.6 .7 4.3-.7 .7-1.3-.3-2.9-2.3-3.9-2-.6-3.6-.3-4.3 .7zm32.4 35.6c-1.6 1.3-1 4.3 1.3 6.2 2.3 2.3 5.2 2.6 6.5 1 1.3-1.3 .7-4.3-1.3-6.2-2.2-2.3-5.2-2.6-6.5-1zm-11.4-14.7c-1.6 1-1.6 3.6 0 5.9 1.6 2.3 4.3 3.3 5.6 2.3 1.6-1.3 1.6-3.9 0-6.2-1.4-2.3-4-3.3-5.6-2z"
                        /></svg
                    >
                </a>
            </footer>
        </section>
    </div>
    <Canvas>
        <Scene {scroll} />
    </Canvas>
</Scroller>

<style>
    header,
    section {
        display: flex;
        flex-direction: column;
        align-items: center;
        justify-content: center;
        height: 100vh;
        padding-top: 25vh;
    }
    h1 {
        color: var(--color-fg);
        font-family: var(--font-title);
        margin: 0;
        font-size: clamp(1.6rem, 6vw, 4rem);
    }
    .subtitle {
        font-size: clamp(1.1rem, 2vw, 1.8rem);
        font-family: var(--font-title);
        font-weight: normal;
        max-width: 35rem;
        margin: 0;
    }
    p {
        color: var(--color-dimmed);
        font-family: var(--font-body);
        padding: 0 1rem;
        max-width: 35rem;
        line-height: 1.7;
        text-align: center;
        white-space: balance;
    }
    h2 {
        color: var(--color-fg);
        font-family: var(--font-title);
        font-size: clamp(1.4rem, 4vw, 3rem);
        margin: 0;
    }

    p > a {
        pointer-events: all;
        color: var(--color-accent);
    }

    a[role='button'] {
        --button-height: 3rem;

        height: var(--button-height); /* hardcoded size can be used in translate */
        pointer-events: all; /* necessary because of Scroller */

        display: flex;
        align-items: center;
        padding-inline: 1em;
        justify-content: center;
        transition: all 0.3s ease-in-out;

        position: relative; /* to absolute position before */
        transform-style: preserve-3d;

        color: var(--color-accent-fg);
        cursor: pointer;
        font-size: 1.1rem;
        font-family: var(--font-buttons);
        font-weight: bold;
        text-decoration: none;
        background-color: var(--color-accent);
    }
    a[role='button']:hover {
        transform: translateY(calc(var(--button-height) / -2)) rotateX(90deg);
    }
    a[role='button']::before {
        content: 'See project';

        position: absolute; /* stretch the connected element */

        opacity: 0;
        transform: rotateX(90deg) rotateY(180deg) rotateZ(180deg) translateY(var(--button-height));
        transition: all 0.5s ease-out;
        transform-origin: bottom center;

        /* not automatically inherited from element */
        height: var(--button-height);
        display: flex;
        align-items: center;
        padding-inline: 1em;
        justify-content: center;
        background-color: var(--color-accent);
    }
    a[role='button']:hover:before {
        transform: rotateX(90deg) rotateY(180deg) rotateZ(180deg) translateY(--button-height);
        opacity: 1;
    }

    footer {
        display: flex;
        padding: 3rem;
        gap: 4rem;
    }
    .social {
        pointer-events: all;
        fill: var(--color-accent);
        scale: 2.5;
        transition: scale 0.3s;
    }
    .social:hover {
        scale: 3;
    }
</style>
