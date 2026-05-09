<script>
    let submitted = false;

    function handleSubmit(event) {
        event.preventDefault();
        submitted = true;
    }
</script>

<section class="contact-page">
    <h1>Want to get in Touch?</h1>
    <p class="contact-intro">
        Send me a quick message to get in touch regarding projects, 
        collaborations, or general enquiries.
        
        I'll respond as soon as possible.
    </p>

    <form class="contact-form" on:submit={handleSubmit}>
        <div class="input-group">
            <label for="name">Name</label>
            <input type="text" id="name" placeholder="Enter your name" required />
        </div>

        <div class="input-group">
            <label for="email">Email</label>
            <input type="email" id="email" placeholder="Enter your email" required />
        </div>

        <div class="input-group">
            <label for="message">Message</label>
            <textarea id="message" rows="8" placeholder="Enter your message" required ></textarea>
        </div>

        <button type="submit">
            Send Message
        </button>

        {#if submitted}
            <p class="success-message">
                Message sent successfully.
            </p>
        {/if}
    </form>
</section>

<style>
    .contact-page {
        padding: var(--space-xl);
        text-align: center;
    }

    .contact-page h1 {
        margin-bottom: var(--space-xl);
        font-size: var(--font-xxxl);
    }

    .contact-intro {
        max-width: 500px;
        margin: 0 auto var(--space-lg);
        text-align: center;
        font-size: var(--font-md);
        color: var(--text-contrast);
        line-height: 1.8;
    }

    .contact-form {
        display: flex;
        flex-direction: column;
        gap: var(--space-lg);

        max-width: 800px;
        margin: 0 auto;
        padding: var(--space-xl);
        
        border: 2px solid var(--color-line);
        border-radius: var(--radius-md);
        background: linear-gradient(180deg, var(--color-panel), var(--color-purple-bottom));
    }

    .input-group {
        display: flex;
        flex-direction: column;
        text-align: left;
    }

    .input-group label {
        margin-bottom: var(--space-xs);
        font-size: var(--font-md);
    }

    .input-group input,
    .input-group textarea {
        padding: var(--space-sm);
        border: 2px solid var(--color-line);
        border-radius: var(--radius-md);
        background: var(--color-panel-soft);
        color: var(--text-primary);
        font-size: var(--font-md);

        resize: vertical;
    }

    .input-group input:focus,
    .input-group textarea:focus {
        outline: none;
        border-color: var(--color-accent);
        box-shadow: 0 0 10px var(--color-accent);
    }

    button {
        align-self: center;
        padding: var(--space-sm) var(--space-lg);

        border: 2px solid var(--color-accent);
        border-radius: var(--radius-md);
        font-size: var(--font-md);
        background: linear-gradient(180deg, var(--color-accent-soft) 0%, var(--color-purple-top) 100%);
        color: var(--text-contrast);
        font-weight: 700;
        box-shadow: inset 0 1px 4px var(--color-purple-top);

        transition: transform var(--transition-fast), box-shadow var(--transition-fast);
    }

    button:hover {
        transform: translateY(-3px) scale(1.03);
        box-shadow: 0 0 12px var(--color-accent);
    }

    .success-message {
        margin-top: var(--space-sm);
        font-size: var(--font-lg);
        color: var(--color-accent);
    }

    @media (max-width: 760px) {
        .contact-page {
            padding: var(--space-lg) var(--space-md);
        }
        
        .contact-page h1 {
            margin-bottom: var(--space-md);
            font-size: var(--font-xxl);
        }
        
        .contact-form {
            max-width: 500px;
            gap: var(--space-md);
        }

        .input-group input,
        .input-group textarea {
            font-size: var(--font-sm);
        }
    }

    @media (min-width: 1300px) {
        .contact-form {
            max-width: 1000px;
        }

        .input-group input,
        .input-group textarea {
            font-size: var(--font-lg);
        }

        button {
            font-size: var(--font-xl);
        }

        .input-group label {
            font-size: var(--font-lg);
        }

        .success-message {
            font-size: var(--font-xl);
        }

        .contact-intro {
            max-width: 800px;
            font-size: var(--font-lg);
        }
    }
</style>