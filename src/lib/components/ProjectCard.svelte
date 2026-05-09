<script>
    export let title;
    export let description = '';
    export let href = '#';
    export let image = '';
</script>

<a href={href} class="project-card">
    <img class="card-image" src={image} alt={title}>
    <h3>{title}</h3>
    {#if description}
        <p>{description}</p>
    {/if}
</a>

<style>
    .project-card {
        width: 300px;
        padding: var(--space-xs) var(--space-sm) var(--space-sm);
        border: 1.5px solid var(--color-accent);
        border-radius: var(--radius-md);
        background: linear-gradient(180deg, var(--color-panel), var(--color-purple-bottom));
        text-align: center;
        transition: transform var(--transition-fast), box-shadow var(--transition-fast);
    }

    .project-card:hover {
        transform: translateY(-6px) scale(1.02);
        box-shadow: 0 0 20px var(--color-accent);
    }

    .card-image {
        width: 100%;
        aspect-ratio: 16 / 9;
        border-radius: var(--radius-md);
        margin-bottom: var(--space-xs);
    }

    h3 {
        margin-bottom: var(--space-md);
        font-size: var(--font-md);
    }

    p {
        min-height: 32px;
        margin: 0 0 10px;
        font-size: var(--font-sm);
        line-height: 1.2;
    }

    @media (max-width: 760px) {
        .project-card {
            width: 300px;
        }

        h3 {
            font-size: (--font-base);
            margin-bottom: var(--space-sm);
        }

        p {
            font-size: var(--font-sm);
        }
    }

    @media (min-width: 1300px) {
        .project-card {
            width: 500px;
            margin-top: var(--space-md);
            border: 2px solid var(--color-accent);
        }

        p {
            font-size: var(--font-md);
        }

        h3 {
            font-size: var(--font-lg);
        }
    }
</style>