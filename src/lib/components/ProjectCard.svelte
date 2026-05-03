<script>
    export let title;
    export let description = '';
    export let href = '#';
    export let buttonLabel = 'View';
</script>

<article class="project-card">
    <div class="placeholder-art project-image" role="img" aria-label="Project image"></div>
    <h3>{title}</h3>
    {#if description}
        <p>{description}</p>
    {/if}
    <a class="featured-button" href={href}>{buttonLabel} ➜</a>
</article>

<style>
    .project-card {
        width: 300px;
        padding: var(--space-xs) var(--space-sm) var(--space-sm);
        border: 1.5px solid var(--color-accent);
        border-radius: var(--radius-md);
        background: linear-gradient(180deg, rgba(118, 61, 196, 0.42), rgba(13, 2, 28, 0.8));
        text-align: center;
    }

    .project-image {
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

    .featured-button {
        width: 100%;
        min-height: 28px;
        font-size: var(--font-sm);
    }

    @media (min-width: 1300px) {
        .project-card {
            width: 500px;
            margin-top: 20px;
        }

        .featured-button {
            min-height: 40px;
            font-size: var(--font-lg);
        }

        p {
            font-size: var(--font-md);
        }

        h3 {
            font-size: var(--font-lg);
        }
    }
</style>