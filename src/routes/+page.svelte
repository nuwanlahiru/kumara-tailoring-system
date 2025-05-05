<script>
    // This will be our main landing page
    import '../app.css';
</script>

<main>
    <h1>Welcome to Kumara Master Tailoring System</h1>
    <p>Your digital solution for managing tailoring operations</p>
    <div class="cta-buttons">
        <a href="/login" class="button">Login</a>
        <a href="/dashboard" class="button secondary">Dashboard</a>
    </div>
</main>

<style>
    main {
        text-align: center;
        padding: 2rem;
        max-width: 800px;
        margin: 0 auto;
    }

    h1 {
        color: #2c3e50;
        margin-bottom: 1rem;
    }

    .cta-buttons {
        margin-top: 2rem;
        display: flex;
        gap: 1rem;
        justify-content: center;
    }

    .button {
        padding: 0.75rem 1.5rem;
        border-radius: 4px;
        text-decoration: none;
        font-weight: 600;
        transition: all 0.2s;
    }

    .button {
        background-color: #4CAF50;
        color: white;
    }

    .button:hover {
        background-color: #45a049;
    }


    .button.secondary {
        background-color: #f0f0f0;
        color: #333;
    }


    .button.secondary:hover {
        background-color: #e0e0e0;
    }
</style>
