<svelte:head>
    <title>Vanessa</title>
</svelte:head>

<script>
    import { resolve, asset } from '$app/paths';
	import ProjectCard from '$lib/components/ProjectCard.svelte';
   const featuredProjects = [
    {
        title: 'Project 1 Title',
        description: 'Short desc of project 1'
    },
    {
        title: 'Project 2 Title',
        description: 'Short desc of project 2'
    },
    {
        title: 'Project 3 Title',
        description: 'Short desc of project 3'
    }
   ];
</script>

<!-- Page Container -->
    <!-- Hero Section -->
    <section class="hero" aria-labelledby="home-title">
        <div class="hero-content">
            <p class="intro-line">
                Hi, I'm
            </p>
            <h1 id="home-title">Vanessa</h1>
            <p class="desc-line">Short description</p>
            <a class="down-arrow" href="#featured" aria-label="Skip to featured projects">↡</a>
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
                    buttonLabel="View" 
                />
            {/each}
        </div>

        <a class="featured-button" href={resolve('/projects/')}>View All Projects -></a>
     </section>


<style>
    /* Hero Section */
    .hero {
        text-align: center;
        min-height: 85vh;
        display: grid;
        justify-items: center;
        align-items: center;
        padding: 28px var(--space-md) 0;
    }

    .intro-line {
        display: flex;
        align-items: center;
        gap: var(--space-xs);
        margin: 0;
        color: var(--text-primary);
        font-size: var(--font-lg);
        font-weight: 700;
        text-transform: uppercase;
    }

    .intro-line::after {
        content: "";
        width: 340px;
        height: 1px;
        background: var(--color-accent);
        margin-left: 10px;
    }

    h1 {
        margin: var(--space-xs) 0;
        font-size: var(--font-hero);
        letter-spacing: 0;
    }

    .desc-line {
        margin-bottom: var(--space-sm);
        font-size: var(--font-md);
        font-weight: 700;
    }

    .down-arrow {
        color: var(--color-accent);
        font-size: var(--space-xl);
        line-height: 1.5;
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
    }

    #featured-title {
        min-height: 12vh;
        font-size: var(--font-xl);
    }
</style>
