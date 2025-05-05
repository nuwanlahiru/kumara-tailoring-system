<script>
    // Sample data - will be replaced with real data from Supabase
    const stats = [
        { name: 'Active Orders', value: '24', change: '+4.75%', changeType: 'positive' },
        { name: 'Total Customers', value: '156', change: '+12.3%', changeType: 'positive' },
        { name: 'Revenue (Monthly)', value: 'Rs. 245,000', change: '+8.2%', changeType: 'positive' },
        { name: 'Pending Tasks', value: '8', change: '-2', changeType: 'negative' }
    ];

    const recentOrders = [
        { id: '#ORD-001', customer: 'John Doe', type: 'Shirt', status: 'In Progress', dueDate: '2025-05-10' },
        { id: '#ORD-002', customer: 'Jane Smith', type: 'Trousers', status: 'Measuring', dueDate: '2025-05-12' },
        { id: '#ORD-003', customer: 'Robert Johnson', type: 'Blazer', status: 'Ready', dueDate: '2025-05-08', isUrgent: true },
    ];
</script>

<div class="dashboard">
    <h1>Dashboard</h1>
    
    <!-- Stats Cards -->
    <div class="stats-grid">
        {#each stats as stat}
            <div class="stat-card">
                <div class="stat-value">{stat.value}</div>
                <div class="stat-name">{stat.name}</div>
                <div class="stat-change {stat.changeType}">
                    {stat.changeType === 'positive' ? '↑' : '↓'} {stat.change}
                </div>
            </div>
        {/each}
    </div>

    <!-- Recent Orders -->
    <div class="section">
        <div class="section-header">
            <h2>Recent Orders</h2>
            <a href="/orders" class="view-all">View All</a>
        </div>
        
        <div class="table-container">
            <table>
                <thead>
                    <tr>
                        <th>Order ID</th>
                        <th>Customer</th>
                        <th>Type</th>
                        <th>Status</th>
                        <th>Due Date</th>
                        <th>Actions</th>
                    </tr>
                </thead>
                <tbody>
                    {#each recentOrders as order}
                        <tr class={order.isUrgent ? 'urgent' : ''}>
                            <td>{order.id}</td>
                            <td>{order.customer}</td>
                            <td>{order.type}</td>
                            <td>
                                <span class="status-badge {order.status.toLowerCase().replace(' ', '-')}">
                                    {order.status}
                                </span>
                            </td>
                            <td>{order.dueDate}</td>
                            <td>
                                <a href={`/orders/${order.id}`} class="action-link">View</a>
                            </td>
                        </tr>
                    {/each}
                </tbody>
            </table>
        </div>
    </div>

    <!-- Quick Actions -->
    <div class="quick-actions">
        <h2>Quick Actions</h2>
        <div class="action-buttons">
            <a href="/orders/new" class="action-button">
                <span class="icon">+</span>
                <span>New Order</span>
            </a>
            <a href="/customers/new" class="action-button">
                <span class="icon">+</span>
                <span>Add Customer</span>
            </a>
            <a href="/inventory/add" class="action-button">
                <span class="icon">+</span>
                <span>Add Inventory</span>
            </a>
        </div>
    </div>
</div>

<style>
    .dashboard {
        max-width: 1200px;
        margin: 0 auto;
        padding: 1rem;
    }

    h1 {
        color: var(--text);
        margin-bottom: 2rem;
    }

    /* Stats Grid */
    .stats-grid {
        display: grid;
        grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
        gap: 1.5rem;
        margin-bottom: 2.5rem;
    }

    .stat-card {
        background: white;
        border-radius: 8px;
        padding: 1.5rem;
        box-shadow: 0 2px 4px rgba(0, 0, 0, 0.05);
    }


    .stat-value {
        font-size: 2rem;
        font-weight: 700;
        color: var(--text);
        margin-bottom: 0.5rem;
    }

    .stat-name {
        color: var(--text-light);
        font-size: 0.9rem;
        margin-bottom: 0.5rem;
    }

    .stat-change {
        font-size: 0.85rem;
        font-weight: 500;
    }
    .stat-change.positive {
        color: var(--success);
    }
    .stat-change.negative {
        color: var(--error);
    }

    /* Section Styling */
    .section {
        background: white;
        border-radius: 8px;
        padding: 1.5rem;
        margin-bottom: 2rem;
        box-shadow: 0 2px 4px rgba(0, 0, 0, 0.05);
    }

    .section-header {
        display: flex;
        justify-content: space-between;
        align-items: center;
        margin-bottom: 1.5rem;
    }

    .section-header h2 {
        margin: 0;
        font-size: 1.25rem;
    }

    .view-all {
        color: var(--primary);
        text-decoration: none;
        font-size: 0.9rem;
    }

    .view-all:hover {
        text-decoration: underline;
    }

    /* Table Styling */
    .table-container {
        overflow-x: auto;
    }

    table {
        width: 100%;
        border-collapse: collapse;
    }

    th, td {
        padding: 1rem;
        text-align: left;
        border-bottom: 1px solid var(--gray-light);
    }

    th {
        font-weight: 600;
        color: var(--text-light);
        font-size: 0.85rem;
        text-transform: uppercase;
        letter-spacing: 0.05em;
    }


    tr:hover {
        background-color: #f9f9f9;
    }

    tr.urgent {
        border-left: 3px solid var(--error);
    }

    .status-badge {
        display: inline-block;
        padding: 0.25rem 0.75rem;
        border-radius: 9999px;
        font-size: 0.8rem;
        font-weight: 500;
    }

    .status-badge.in-progress {
        background-color: #e3f2fd;
        color: #1976d2;
    }

    .status-badge.measuring {
        background-color: #fff3e0;
        color: #ef6c00;
    }

    .status-badge.ready {
        background-color: #e8f5e9;
        color: #2e7d32;
    }

    .action-link {
        color: var(--primary);
        text-decoration: none;
    }

    .action-link:hover {
        text-decoration: underline;
    }

    /* Quick Actions */
    .quick-actions {
        background: white;
        border-radius: 8px;
        padding: 1.5rem;
        margin-bottom: 2rem;
        box-shadow: 0 2px 4px rgba(0, 0, 0, 0.05);
    }


    .action-buttons {
        display: grid;
        grid-template-columns: repeat(auto-fill, minmax(200px, 1fr));
        gap: 1rem;
        margin-top: 1rem;
    }

    .action-button {
        display: flex;
        flex-direction: column;
        align-items: center;
        justify-content: center;
        background: #f5f5f5;
        border: 1px dashed #ccc;
        border-radius: 8px;
        padding: 1.5rem 1rem;
        text-decoration: none;
        color: var(--text);
        transition: all 0.2s;
    }

    .action-button:hover {
        background: #e8f5e9;
        border-color: var(--primary);
    }

    .action-button .icon {
        font-size: 1.5rem;
        margin-bottom: 0.5rem;
        color: var(--primary);
    }
</style>
