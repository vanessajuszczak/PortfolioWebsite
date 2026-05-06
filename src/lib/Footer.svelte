<footer class="footer">
    <div class="socials">
        <a href="https://www.youtube.com/@xnesswag" target="_blank" aria-label="Youtube">
            <img src="/images/footer/youtube.png" alt="Youtube" />
        </a>
        <a href="https://www.tiktok.com/@popscicle03" target="_blank" aria-label="Tiktok">
            <img src="/images/footer/tiktok.png" alt="Tiktok" />
        </a>
        <a href="https://www.twitch.tv/xnesswag" target="_blank" aria-label="Twitch">
            <img src="/images/footer/twitch.png" alt="Twitch" />
        </a>
    </div>
    <p>© Vanessa Juszczak</p>
</footer>


<style>
    .socials {
        display: flex;
        justify-content: center;
        gap: var(--space-md);
        margin-bottom: var(--space-sm);
        margin-top: var(--space-xs);
    }

    .socials a {
        width: 50px;
        height: 50px;
        border-radius: var(--radius-sm);
        background: var(--color-panel-soft);
        display: flex;
        align-items: center;
        justify-content: center;
        border: 2px solid var(--color-line);

        transition: transform var(--transition-fast), box-shadow var(--transition-fast);
    }

    .socials img {
        width: 40px;
        height: 40px;
        object-fit: contain;
    }

    .socials a:hover {
        transform: translateY(-3px) scale(1.08);
        box-shadow: 0 0 12px var(--color-accent);
    }

    p {
        color: var(--text-contrast);
        margin-top: var(--space-md);
    }

    .footer {
        width: 100%;
        padding: var(--space-md);
        text-align: center;
        font-family: var(--font-body);
        font-size: var(--font-sm);
        color: var(--text-contrast);
        border-top: 1px solid var(--color-line);
        box-shadow: var(--shadow-sm);
        position: relative;
        z-index: 10;
    }

    .footer::before {
        content: '';
        position: absolute;
        top: 0;
        left: 0;
        height: 3px;
        width: 100%;
        background: var(--color-primary);
        animation: gradientScroll 6s linear infinite;
    }

    @keyframes fadeInFooter {
        from { opacity: 0; transform: translateY(10px); }
        to { opacity: 1; transform: translateY(0); }
    }

    @keyframes gradientScroll {
        0% { background-position: 0% 50%; }
        100% { background-position: 100% 50%; }
    }

    @media (max-width: 768px) {
        .footer {
            padding: var(--space-sm);
            font-size: var(--font-xs);
        }
    }
</style>
