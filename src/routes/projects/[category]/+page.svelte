<script>
    import {base} from '$app/paths';
    import ProjectCard from '$lib/components/ProjectCard.svelte';

    export let params;

    const category = params.category;

    const projectData = {
        games: [
            {title: 'Shopping Collection Game', description: 'The player must add items from their shopping list to the cart.', href: base + '/projects/games/project1'},
            {title: 'Side Scrolling Shooter Game', description: 'The player must shoot enemies to reach a score of 50.', href: base + '/projects/games/project2'},
            {title: 'The Descent', description: 'Advance through the floors, defeat the monster, and find a way to escape!', href: base + '/projects/games/project3'},
            {title: 'Game 4', description: 'Desc', href: base + '/projects/games/project4'},
            {title: 'Game 5', description: 'Desc', href: base + '/projects/games/project5'}
        ],
        'digital-art': [
            {title: 'Basic Animations', description: 'Three basic beginner animations to showcase skills.', href: base + '/projects/digital-art/project1'},
            {title: 'Fantasy Game Original Character', description: 'Concept art of an original character designed for a fantasy-style game.', href: base + '/projects/digital-art/project2'},
            {title: 'Walk Cycle Animation', description: 'An animation showcasing a walk cycle of an original character.', href: base + '/projects/digital-art/project3'},
            {title: 'Head-turn Animation', description: 'An animation showcasing a head-turn with expression change of an original character.', href: base + '/projects/digital-art/project4'},
            {title: 'Illustration 2', description: 'Desc', href: base + '/projects/digital-art/project5'}
        ],
        '3d': [
            {title: '3D Game Asset', description: 'A 3D model of a tube slide used as a finish goal in a game.', href: base + '/projects/3d/project1'},
            {title: 'School Bus Model', description: 'A 3D model of a school bus with custom UV-mapping.', href: base + '/projects/3d/project2'},
            {title: 'Random Basic 3D Models', description: 'A compilation of random 3D models, including scaffolding, a castle, a mug, and hands.', href: base + '/projects/3d/project3'},
            {title: '3D Model 4', description: 'Desc', href: base + '/projects/3d/project4'},
            {title: '3D Model 5', description: 'Desc', href: base + '/projects/3d/project5'}
        ]
    };

    const categoryTitles = {
        games: 'Games',
        'digital-art': 'Digital Art',
        '3d': '3D Models'
    };

    const projects = projectData[category] || [];
</script>

<section class="category-page">
    <h1>{categoryTitles[category]}</h1>

    <div class="grid">
        {#each projects as project}
            <ProjectCard
                title={project.title}
                description={project.description}
                href={project.href}
            />
        {/each}
    </div>
</section>

<style>
    .category-page {
        text-align: center;
        padding: var(--space-xl);
    }

    .grid {
        display: flex;
        justify-content: flex-start;
        gap: var(--space-lg);
        
        overflow-x: auto;
        overflow-y: hidden;
        width: 100%;

        padding: var(--space-md);
        scroll-snap-type: x mandatory;
    }

    .grid::-webkit-scrollbar {
        height: 10px;
    }

    .grid::-webkit-scrollbar-track {
        background: var(--color-purple-bottom);
        border-radius: var(--radius-md);
    }

    .grid::-webkit-scrollbar-thumb {
        background: var(--color-accent);
        border-radius: var(--radius-md);
    }

    :global(.project-card) {
        flex: 0 0 31%;

        max-width: 360px;
        min-width: 300px;
        scroll-snap-align: center;
    }
    
    .category-page h1 {
        font-size: var(--font-xxl);
        margin-bottom: 0;
    }

    @media (min-width: 1300px) {
        :global(.project-card) {
            max-width: 620px;
        }
        .category-page h1 {
        font-size: var(--font-xxxl);
    }
    }
</style>