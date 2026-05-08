<script>
    import {base} from '$app/paths';
    import {resolve} from '$app/paths';

    const categories = [
        {
            title: 'Games',
            description: 'Game development projects',
            href: base + '/projects/games'
        },
        {
            title: 'Digital Art',
            description: 'Animations, illustrations, and digital media projects',
            href: base + '/projects/digital-art'
        },
        {
            title: '3D Models',
            description: '3D assets, renders, and modelling projects',
            href: base + '/projects/3d'
        }
    ];
</script>

<section class="projects">
    <h1>Projects</h1>

    <div class="category-grid">
        {#each categories as category}
            <div class="category-card">
                <div class="placeholder-art image"></div>
                <h2>{category.title}</h2>
                <p>{category.description}</p>
                <a class="button"  href={resolve(category.href)}>Continue ➜</a>
            </div>
        {/each}
    </div>
</section>

<style>
    .projects {
        text-align: center;
        padding: var(--space-xl);
    }

    h1 {
        margin-bottom: var(--space-lg);
        font-size: var(--font-xxl);
    }

    .category-grid {
        display: flex;
        justify-content: center;
        gap: var(--space-lg);
        flex-wrap: wrap;
    }

    .category-card {
        display: flex;
        flex-direction: column;
        width: 300px;
        padding: var(--space-md);
        border: 2px solid var(--color-accent);
        border-radius: var(--radius-md);
        background: linear-gradient(180deg, var(--color-panel), var(--color-purple-bottom));
        text-align: center;
    }
    
    .category-card p {
        flex-grow: 1;
    }

    .button:hover {
        transform: translateY(-4px) scale(1.03);
        box-shadow: 0 0 10px var(--color-accent);
    }

    .image {
        width: 100%;
        aspect-ratio: 16/9;
        border-radius: var(--radius-md);
        margin-bottom: var(--space-sm);
    }

    .button {
        display: inline-block;
        margin-top: var(--space-sm);
        font-size: var(--font-md);
        border: 2px solid var(--color-accent);
        border-radius: var(--radius-md);
        padding: var(--space-xs);

        transition: transform var(--transition-fast), box-shadow var(--transition-fast);
    }

    @media (min-width: 1300px) {
        .category-card {
            width: 420px;
            min-height: 520px;
        }

        .category-card h2 {
            font-size: var(--font-xl);
        }

        .category-card p {
            font-size: var(--font-lg);
        }

        .button {
            font-size: var(--font-lg);
            min-height: 44px;
        }

        .image {
            height: 240px;
        }

        h1 {
            font-size: var(--font-xxxl);
        }
    }
</style>