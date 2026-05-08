<script>
    import ProjectCard from '$lib/components/ProjectCard.svelte';

    export let params;

    const category = params.category;

    const projectData = {
        games: [
            {title: 'Shopping Collection Game', description: 'The player must add items from their shopping list to the cart.', href: '/projects/games/project1'},
            {title: 'Side Scrolling Shooter Game', description: 'The player must shoot enemies to reach a score of 50.', href: '/projects/games/project2'},
            {title: 'Game 3', description: 'Desc', href: '/projects/games/project3'},
            {title: 'Game 4', description: 'Desc', href: '/projects/games/project4'},
            {title: 'Game 5', description: 'Desc', href: '/projects/games/project5'}
        ],
        'digital-art': [
            {title: 'Animation 1', description: 'Desc', href: '#'},
            {title: 'Illustration 1', description: 'Desc', href: '#'},
            {title: 'Game Asset 1', description: 'Desc', href: '#'},
            {title: 'Game Asset 2', description: 'Desc', href: '#'},
            {title: 'Illustration 2', description: 'Desc', href: '#'}
        ],
        '3d': [
            {title: '3D Model 1', description: 'Desc', href:'#'},
            {title: '3D Model 2', description: 'Desc', href:'#'},
            {title: '3D Model 3', description: 'Desc', href:'#'},
            {title: '3D Model 4', description: 'Desc', href:'#'},
            {title: '3D Model 5', description: 'Desc', href:'#'}
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