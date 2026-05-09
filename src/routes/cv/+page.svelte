<script>
    import {base} from '$app/paths';
</script>

<section class="cv-page">
    <h1>CV</h1>

    <a class="download-button" href={base + '/cv/vanessa-cv.pdf'} download >
        Download CV
    </a>

    <div class="cv-image">
        <img src={base + '/cv/cv-image.png'} alt="CV Preview" />
    </div>
</section>

<style>
    .cv-page {
        display: flex;
        flex-direction: column;
        align-items: center;
        padding: var(--space-xl);
    }

    .cv-page h1 {
        margin-bottom: var(--space-md);
        font-size: var(--font-xxxl);
        text-align: center;
    }

    .download-button {
        display: inline-block;
        margin-bottom: var(--space-xl);
        padding: var(--space-sm) var(--space-md);

        border: 2px solid var(--color-accent);
        border-radius: var(--radius-md);
        font-size: var(--font-md);

        transition: transform var(--transition-fast), box-shadow var(--transition-fast);
    }

    .download-button:hover {
        transform: translateY(-3px) scale(1.03);
        box-shadow: 0 0 12px var(--color-accent);
    }

    .cv-image {
        width: 100%;
        display: flex;
        justify-content: center;
    }

    .cv-image img {
        width: 100%;
        max-width: 900px;

        border-radius: var(--radius-md);
        border: 2px solid var(--color-line);
        box-shadow: var(--shadow-md);
    }

    @media (min-width: 1300px) {
        .cv-image img {
            max-width: 1100px;
        }

        .download-button {
            font-size: var(--font-lg);
        }
    }
</style>