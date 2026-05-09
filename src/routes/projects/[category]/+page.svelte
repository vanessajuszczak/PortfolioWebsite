<script>
    import {base} from '$app/paths';
    import ProjectCard from '$lib/components/ProjectCard.svelte';

    export let params;

    const category = params.category;

    const projectData = {
        games: [
            {title: 'Shopping Collection Game', description: 'The player must add items from their shopping list to the cart.', href: base + '/projects/games/project1', image: base + '/images/games/project1/main.png'},
            {title: 'Side Scrolling Shooter Game', description: 'The player must shoot enemies to reach a score of 50.', href: base + '/projects/games/project2', image: base + '/images/games/project2/main.png'},
            {title: 'The Descent', description: 'Advance through the floors, defeat the monster, and find a way to escape!', href: base + '/projects/games/project3', image: base + '/images/games/project3/main.png'},
            {title: 'Game 4', description: 'Desc', href: base + '/projects/games/project4', image: base + '/images/games/project4/main.jpg'},
            {title: 'Game 5', description: 'Desc', href: base + '/projects/games/project5', image: base + '/images/games/project5/main.jpg'}
        ],
        'digital-art': [
            {title: 'Basic Animations', description: 'Three basic beginner animations to showcase skills.', href: base + '/projects/digital-art/project1', image: base + '/images/digital-art/project1/gif1.gif'},
            {title: 'Fantasy Game Original Character', description: 'Concept art of an original character designed for a fantasy-style game.', href: base + '/projects/digital-art/project2', image: base + '/images/digital-art/project2/ss1.png'},
            {title: 'Walk Cycle Animation', description: 'An animation showcasing a walk cycle of an original character.', href: base + '/projects/digital-art/project3', image: base + '/images/digital-art/project3/main.png'},
            {title: 'Head-turn Animation', description: 'An animation showcasing a head-turn with expression change of an original character.', href: base + '/projects/digital-art/project4', image: base + '/images/digital-art/project4/gif3.gif'},
            {title: 'Illustration 2', description: 'Desc', href: base + '/projects/digital-art/project5', image: base + '/images/digital-art/project5/main.jpg'}
        ],
        '3d': [
            {title: '3D Game Asset', description: 'A 3D model of a tube slide used as a finish goal in a game.', href: base + '/projects/3d/project1', image: base + '/images/3d/project1/main.jpg'},
            {title: 'School Bus Model', description: 'A 3D model of a school bus with custom UV-mapping.', href: base + '/projects/3d/project2', image: base + '/images/3d/project2/main.jpg'},
            {title: 'Random Basic 3D Models', description: 'A compilation of random 3D models, including scaffolding, a castle, a mug, and hands.', href: base + '/projects/3d/project3', image: base + '/images/3d/project3/main.jpg'},
            {title: '3D Model 4', description: 'Desc', href: base + '/projects/3d/project4', image: base + '/images/3d/project4/main.jpg'},
            {title: '3D Model 5', description: 'Desc', href: base + '/projects/3d/project5', image: base + '/images/3d/project5/main.jpg'}
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
                image={project.image}
            />
        {/each}
    </div>

    <p class="mobile-scroll-hint">Scroll to View Projects ➜</p>
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

    .mobile-scroll-hint {
        display: none;
    }

    @media (max-width: 760px) {
        .grid {
            padding-bottom: var(--space-sm);
            scrollbar-width: thin;
            scrollbar-color: var(--color-accent) var(--color-purple-bottom);
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

        .mobile-scroll-hint {
            display: block;
            margin: var(--space-sm) auto var(--space-lg);
            margin-top: var(--space-lg);
            color: var(--text-secondary);
            font-size: var(--font-md);
            font-weight: 700;
            text-align: center;
            text-transform: uppercase;
        }
        .category-page {
            padding: 60px var(--space-lg) var(--space-md);
        }

        .category-page h1 {
            margin-bottom: var(--space-lg);
        }

        .grid {
            padding: 0 0 var(--space-lg);
            gap: var(--space-md);
        }
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