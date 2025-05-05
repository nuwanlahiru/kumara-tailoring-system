<script>
    let email = '';
    let password = '';
    let error = '';
    let isLoading = false;

    async function handleLogin() {
        if (!email || !password) {
            error = 'Please enter both email and password';
            return;
        }
        
        isLoading = true;
        error = '';
        
        // TODO: Implement actual login with Supabase
        console.log('Login attempt with:', email);
        
        // Simulate API call
        try {
            await new Promise(resolve => setTimeout(resolve, 1000));
            // Redirect to dashboard on success
            window.location.href = '/dashboard';
        } catch (err) {
            error = 'Login failed. Please check your credentials.';
            console.error('Login error:', err);
        } finally {
            isLoading = false;
        }
    }
</script>

<div class="login-container">
    <div class="login-box">
        <h2>Login to Your Account</h2>
        
        {#if error}
            <div class="error-message">
                {error}
            </div>
        {/if}
        
        <form on:submit|preventDefault={handleLogin}>
            <div class="form-group">
                <label for="email">Email</label>
                <input
                    type="email"
                    id="email"
                    bind:value={email}
                    placeholder="Enter your email"
                    required
                />
            </div>
            
            <div class="form-group">
                <label for="password">Password</label>
                <input
                    type="password"
                    id="password"
                    bind:value={password}
                    placeholder="Enter your password"
                    required
                />
            </div>
            
            <button type="submit" disabled={isLoading} class="login-button">
                {isLoading ? 'Logging in...' : 'Login'}
            </button>
        </form>
        
        <div class="forgot-password">
            <a href="/forgot-password">Forgot your password?</a>
        </div>
    </div>
</div>

<style>
    .login-container {
        display: flex;
        justify-content: center;
        align-items: center;
        min-height: 60vh;
        padding: 2rem;
    }
    
    .login-box {
        background: white;
        padding: 2.5rem;
        border-radius: 8px;
        box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1);
        width: 100%;
        max-width: 400px;
    }
    
    h2 {
        margin-bottom: 1.5rem;
        color: var(--text);
        text-align: center;
    }
    
    .form-group {
        margin-bottom: 1.5rem;
    }
    
    label {
        display: block;
        margin-bottom: 0.5rem;
        color: var(--text);
        font-weight: 500;
    }
    
    input {
        width: 100%;
        padding: 0.75rem;
        border: 1px solid var(--gray);
        border-radius: 4px;
        font-size: 1rem;
    }
    
    input:focus {
        outline: none;
        border-color: var(--primary);
        box-shadow: 0 0 0 2px rgba(76, 175, 80, 0.2);
    }
    
    .login-button {
        width: 100%;
        padding: 0.75rem;
        background-color: var(--primary);
        color: white;
        border: none;
        border-radius: 4px;
        font-size: 1rem;
        font-weight: 600;
        cursor: pointer;
        transition: background-color 0.2s;
    }
    
    .login-button:hover {
        background-color: var(--primary-dark);
    }
    
    .login-button:disabled {
        background-color: var(--gray);
        cursor: not-allowed;
    }
    
    .forgot-password {
        margin-top: 1rem;
        text-align: center;
    }
    
    .forgot-password a {
        color: var(--primary);
        text-decoration: none;
    }
    
    .forgot-password a:hover {
        text-decoration: underline;
    }
    
    .error-message {
        background-color: #ffebee;
        color: var(--error);
        padding: 0.75rem;
        border-radius: 4px;
        margin-bottom: 1.5rem;
        font-size: 0.9rem;
    }
</style>
