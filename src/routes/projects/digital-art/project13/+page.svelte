<script>
    import {base} from '$app/paths';
</script>

<section class="project-page">
    <div class="hero-image">
        <img src={base + '/images/digital-art/project13/figma.png'} alt="Figma Screenshot" />
    </div>

    <div class="project-info">
        <h1>Figma Assignment App Prototype</h1>

        <p class="project-desc">
            An interactive Figma prototype for a teacher-focused app designed to manage assignments and student submissions.
        </p>
        <p>
            <a class="link" href="https://www.figma.com/proto/RgvYMX66pJiJVAgiG59n3j/IxD-Prototype---Vanessa-Juszczak?node-id=14-348&t=idbFSIl37SGC3Y5P-1" target="_blank">Interactive Figma Prototype</a>
        </p>

        <div class="project-details">
            <p><strong>Software:</strong> Figma</p>
            <p><strong>Year:</strong> 2025</p>
        </div>
    </div>
</section>

<div class="gallery">
    <h2>Gallery</h2>

    <div class="gallery-grid">
        <img src={base + '/images/digital-art/project13/wireframes.png'} alt="Screenshot" />
        <img src={base + '/images/digital-art/project13/diagram.png'} alt="Screenshot" />
        <img src={base + '/images/digital-art/project13/figma.png'} alt="Screenshot" />
    </div>
</div>

<div class="button-wrapper">
 <a class="back-button" href={base +"/projects/digital-art"}>
        🡐 Back to Digital Art
    </a>
</div>

<style>
    .button-wrapper {
        display: flex;
        justify-content: center;
        margin-bottom: var(--space-xl);
    }

    .back-button {
        display: inline-flex;
        align-items: center;
        justify-content: center;
        padding: var(--space-xs) var(--space-sm);
        border: 2px solid var(--color-accent);
        border-radius: var(--radius-md);

        font-size: var(--font-md);
        background: linear-gradient(180deg, var(--color-accent-soft) 0%, var(--color-purple-top) 100%);
        color: var(--text-contrast);
        font-weight: 700;
        box-shadow: inset 0 1px 4px var(--color-purple-top);

        transition: transform var(--transition-fast), box-shadow var(--transition-fast);
    }

    .back-button:hover {
        transform: translateY(-2px);
        box-shadow: 0 0 10px var(--color-accent);
    }

    .project-page {
        display: grid;
        grid-template-columns: 1fr 1fr;
        gap: var(--space-xl);

        padding: var(--space-xl);
        align-items: center;
    }

    .hero-image img {
        width: 100%;
        border-radius: var(--radius-md);
        border: 2px solid var(--color-line);
    }
    
    .project-info h1 {
        margin-bottom: var(--space-md);
        font-size: var(--font-xxl);
    }

    .project-desc {
        margin-bottom: var(--space-lg);
        font-size: var(--font-lg);
    }

    .link {
        color: var(--color-accent);
        text-decoration: underline;
        text-underline-offset: 3px;
        font-weight: 600;
        transition: color var(--transition-fast);
    }

    .link:hover {
        color: var(--text-contrast);
    }

    .project-details {
        display: grid;
        gap: var(--space-sm);
    }

    .gallery {
        margin-top: var(--space-lg);
        text-align: center;
        margin-bottom: var(--space-xl);
    }

    .gallery h2 {
        margin-bottom: var(--space-md);
        font-size: var(--font-xxl);
    }

    .gallery-grid {
        display: flex;
        justify-content: center;
        gap: var(--space-md);
        flex-wrap: wrap;
    }

    .gallery-grid img {
        width: 350px;
        max-width: 100%;
        border-radius: var(--radius-md);
        border: 2px solid var(--color-line);
        object-fit: cover;
    }

    @media (max-width: 760px) {
        .project-page {
            display: flex;
            flex-direction: column;
            padding: var(--space-lg) var(--space-md);
            gap: var(--space-lg);
            text-align: center;
        }
    }

    @media (min-width: 1300px) {
        .gallery-grid img {
            width: 450px;
        }

        .gallery h2 {
            font-size: var(--font-xxxl);
        }

        .project-desc {
            font-size: var(--font-xl);
        }

        .project-details {
            font-size: var(--font-lg);
        }

        .back-button {
            font-size: var(--font-lg);
        }
    }
</style>