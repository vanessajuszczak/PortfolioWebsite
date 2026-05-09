<svelte:head>
    <title>Vanessa</title>
</svelte:head>

<script>
    import {base} from '$app/paths';
    import { resolve, asset } from '$app/paths';
	import ProjectCard from '$lib/components/ProjectCard.svelte';
   const featuredProjects = [
    {
        title: 'The Descent',
        description: 'Advance through the floors, defeat the monster, and find a way to escape!',
        href: base + '/projects/games/project3',
        image: base + '/images/games/project3/main.png'
    },
    {
        title: 'Fantasy Game Original Character',
        description: 'Concept art of an original character designed for a fantasy-style game.',
        href: base + '/projects/digital-art/project2',
        image: base + '/images/digital-art/project2/ss1.png'
    },
    {
        title: '3D Game Asset',
        description: 'A 3D model of a tube slide used as a finish goal in a game.',
        href: base + '/projects/3d/project1',
        image: base + '/images/3d/project1/main.jpg'
    }
   ];

   let arrowClicked = false;

   function handleArrowClick() {
    arrowClicked = true;
   }

</script>

<!-- Page Container -->
    <!-- Hero Section -->
    <section class="hero" aria-labelledby="home-title">
        <div class="hero-content">
            <p class="intro-line">
                Hi, I'm
            </p>
            <h1 id="home-title">Vanessa</h1>
            <p class="desc-line">Interactive Digital Art and Design student exploring web design, games, animation, and digital media.</p>
            <a class="down-arrow"
                class:active={arrowClicked}
                href="#featured"
                on:click={handleArrowClick}
                aria-label="Skip to featured projects"
            >
                ↡
            </a>
        </div>
    </section>

    
    <!-- Featured Section -->
     <section class="featured-section" id="featured" aria-labelledby="featured-title">
        <h2 id="featured-title">Featured Projects</h2>

        <div class="featured-grid">
            {#each featuredProjects as project}
                <ProjectCard
                    title={project.title}
                    description={project.description}
                    href={project.href}
                    image={project.image}
                />
            {/each}
        </div>

        <a class="featured-button" href={resolve('/projects/')}>View All Projects ➜</a>
     </section>


<style>
    /* Hero Section */
    .hero {
        text-align: center;
        min-height: 85vh;
        display: grid;
        flex-direction: column;
        justify-items: center;
        align-items: center;
        padding: 28px var(--space-md) 0;
    }

    .intro-line {
        display: flex;
        align-items: center;
        justify-content: center;
        gap: var(--space-xs);
        margin: 0;
        color: var(--text-primary);
        font-size: var(--font-lg);
        font-weight: 700;
        text-transform: uppercase;
        width: 100%;
        max-width: 555px;
    }

    .intro-line::after {
        content: "";
        width: 340px;
        height: 1px;
        background: var(--color-accent);
        margin-left: var(--space-sm);
    }

    h1 {
        margin: var(--space-xs) 0;
        font-size: var(--font-hero);
        letter-spacing: 0;
    }

    .desc-line {
        text-align: center;
        max-width: 700px;
        margin: 0 auto;
        margin-bottom: var(--space-sm);
        font-size: var(--font-sm);
        font-weight: 700;
    }

    .down-arrow {
        position: relative;
        display: inline-block;
        color: var(--color-accent);
        font-size: var(--space-xl);
        line-height: 1;
        margin-top: var(--space-md);

        transition: margin-top 0.4s ease;
        animation: pulseGlow 2s ease-in-out infinite;
    }

    .down-arrow::before {
        content: "";
        position: absolute;
        bottom: 40%;
        left: 50%;
        transform: translateX(-50%);
        width: 4px;
        height: 30px;
        background: var(--color-accent);
        transition: height 0.4s ease;
    }

    .down-arrow.active {
        animation: none;
    }
    

    /* Featured Section */
    .featured-section {
        display: grid;
        justify-items: center;
        padding: 0 var(--space-md) var(--space-md);
        text-align: center;
    }

    h2 {
        margin-bottom: var(--space-sm);
        font-size: var(--font-lg);
    }

    .featured-grid {
        display: flex;
        justify-content: center;
        gap: var(--space-lg);
        flex-wrap: wrap;
    }

    .featured-button {
        margin-top: var(--space-lg);
        font-size: var(--font-md);
    }

    #featured-title {
        min-height: 10vh;
        font-size: var(--font-xl);
    }

    :global(html) {
        scroll-behavior: smooth;
    }

    @keyframes pulseGlow {
        0% {
            transform: scale(1);
            text-shadow: 0 0 5px var(--color-accent);
        }

        50% {
            transform: scale(1.1);
            text-shadow: 0 0 15px var(--color-accent);
        }

        100% {
            transform: scale(1);
            text-shadow: 0 0 5px var(--color-accent);
        }
    }

    @media (min-width: 1300px) {
        .hero {
            min-height: 100vh;
        }

        h1 {
            font-size: 200px;
        }

        .intro-line {
            font-size: var(--font-xl);
            max-width: 670px;
        }

        .intro-line::after {
            flex: 1;
            width: 560px;
            height: 2px;
        }

        .desc-line {
            font-size: var(--font-md);
            max-width: 500px;
        }

        #featured-title {
            font-size: var(--font-xxl);
        }

        .featured-button {
            font-size: var(--font-lg);
        }

        .down-arrow.active {
            margin-top: 40vh;
        }

        .down-arrow.active::before {
            height: 350px;
        }

    }
</style>
