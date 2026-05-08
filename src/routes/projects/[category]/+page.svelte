<script>
    import {page} from '$app/state';
    import ProjectCard from '$lib/components/ProjectCard.svelte';

    const category = page.url.pathname.split('/').pop();

    const projectData = {
        games: [
            {title: 'Game 1', description: 'Desc', href: '#'},
            {title: 'Game 2', description: 'Desc', href: '#'},
            {title: 'Game 3', description: 'Desc', href: '#'}
        ],
        digitalArt: [
            {title: 'Animation 1', description: 'Desc', href: '#'},
            {title: 'Illustration 1', description: 'Desc', href: '#'},
            {title: 'Game Asset 1', description: 'Desc', href: '#'}
        ],
        models: [
            {title: '3D Model 1', description: 'Desc', href:'#'},
            {title: '3D Model 2', description: 'Desc', href:'#'},
            {title: '3D Model 3', description: 'Desc', href:'#'}
        ]
    };

    const projects = projectData[category] || [];
</script>

<section class="category-page">
    <h1>{category.toUpperCase()}</h1>

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
        justify-content: center;
        gap: var(--space-lg);
        flex-wrap: wrap;
    }
</style>