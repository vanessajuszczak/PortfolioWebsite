<script>
    import {base} from '$app/paths';
</script>

<section class="project-page">
    <div class="hero-image">
        <img src={base + '/images/digital-art/project10/thumbnail.gif'} alt="Thumbnail of pixel art assets preview" />
    </div>

    <div class="project-info">
        <h1>Pixel Art Game Assets Project</h1>

        <p class="project-desc">
            A collection of original pixel art assets created for a 2D adventure game as part of my Concept Art for Games module, including characters, environments and game elements.
        </p>

        <div class="project-details">
            <p><strong>Software:</strong> Aseprite</p>
            <p><strong>Year:</strong> 2025</p>
        </div>
    </div>
</section>

<div class="gallery">
    <h2>Gallery</h2>

    <div class="gallery-grid">
        <img src={base + '/images/digital-art/project10/1.png'} alt="Screenshot" />
        <img src={base + '/images/digital-art/project10/2.gif'} alt="Gif" />
        <img src={base + '/images/digital-art/project10/3.gif'} alt="Gif" />
        <img src={base + '/images/digital-art/project10/4.gif'} alt="Gif" />
        <img src={base + '/images/digital-art/project10/5.gif'} alt="Gif" />
        <img src={base + '/images/digital-art/project10/6.gif'} alt="Gif" />
        <img src={base + '/images/digital-art/project10/7.gif'} alt="Gif" />
        <img src={base + '/images/digital-art/project10/8.gif'} alt="Gif" />
        <img src={base + '/images/digital-art/project10/9.gif'} alt="Gif" />
        <img src={base + '/images/digital-art/project10/10.gif'} alt="Gif" />
        <img src={base + '/images/digital-art/project10/11.gif'} alt="Gif" />
        <img src={base + '/images/digital-art/project10/12.gif'} alt="Gif" />
        <img src={base + '/images/digital-art/project10/13.png'} alt="Screenshot" />
        <img src={base + '/images/digital-art/project10/14.png'} alt="Screenshot" />
        <img src={base + '/images/digital-art/project10/15.png'} alt="Screenshot" />
        <img src={base + '/images/digital-art/project10/16.gif'} alt="Gif" />
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