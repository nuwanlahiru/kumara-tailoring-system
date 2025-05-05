<script>
    import '../app.css';
</script>

<main class="container">
    <nav>
        <a href="/" class="logo">Kumara Tailoring</a>
        <div class="nav-links">
            <a href="/customers">Customers</a>
            <a href="/orders">Orders</a>
            <a href="/inventory">Inventory</a>
            <a href="/login" class="button">Login</a>
        </div>
    </nav>
    
    <slot /> <!-- This is where page content will be injected -->
    
    <footer>
        <p>© 2025 Kumara Master Tailoring System. All rights reserved.</p>
    </footer>
</main>

<style>
    nav {
        display: flex;
        justify-content: space-between;
        align-items: center;
        padding: 1rem 0;
        border-bottom: 1px solid var(--gray);
        margin-bottom: 2rem;
    }

    .logo {
        font-size: 1.5rem;
        font-weight: bold;
        color: var(--primary);
        text-decoration: none;
    }

    .nav-links {
        display: flex;
        gap: 2rem;
        align-items: center;
    }

    .nav-links a {
        color: var(--text);
        text-decoration: none;
        padding: 0.5rem 0;
        position: relative;
    }

    .nav-links a:hover {
        color: var(--primary);
    }

    .nav-links a::after {
        content: '';
        position: absolute;
        width: 0;
        height: 2px;
        bottom: 0;
        left: 0;
        background-color: var(--primary);
        transition: width 0.3s;
    }

    .nav-links a:hover::after {
        width: 100%;
    }

    .button {
        background-color: var(--primary);
        color: white;
        padding: 0.5rem 1rem;
        border-radius: 4px;
        text-decoration: none;
        transition: background-color 0.2s;
    }

    .button:hover {
        background-color: var(--primary-dark);
        text-decoration: none;
    }

    footer {
        margin-top: 4rem;
        padding: 2rem 0;
        border-top: 1px solid var(--gray);
        text-align: center;
        color: var(--text-light);
        font-size: 0.9rem;
    }
</style>
