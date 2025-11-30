<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Breadcrumb Navigation Implementation Guide</title>
    <style>
        :root {
            --primary: #1e40af;
            --primary-light: #3b82f6;
            --accent: #06b6d4;
            --text-dark: #0f172a;
            --text-gray: #64748b;
            --border: #e2e8f0;
        }

        body {
            font-family: 'Inter', -apple-system, BlinkMacSystemFont, sans-serif;
            color: var(--text-dark);
            margin: 0;
            padding: 2rem;
            background: #f8fafc;
            max-width: 900px;
            margin: 0 auto;
        }

        code {
            background: #f1f5f9;
            padding: 0.25rem 0.5rem;
            border-radius: 4px;
            font-family: 'JetBrains Mono', monospace;
            color: #d73a49;
        }

        pre {
            background: #1a202c;
            color: #fff;
            padding: 1rem;
            border-radius: 8px;
            overflow-x: auto;
        }

        h1, h2, h3 {
            color: var(--primary);
        }
    </style>
</head>
<body>
    <h1>Feature 4: Breadcrumb Navigation Component</h1>
    
    <h2>Breadcrumb HTML Snippet</h2>
    <p>Add this right after the opening <code>&lt;main&gt;</code> tag or after your header in target pages:</p>
    
    <pre>&lt;nav class="breadcrumb" aria-label="Breadcrumb"&gt;
    &lt;ol class="breadcrumb-list"&gt;
        &lt;li class="breadcrumb-item"&gt;
            &lt;a href="/cloud-native-blogs/index.html"&gt;
                &lt;i class="fas fa-home"&gt;&lt;/i&gt; Home
            &lt;/a&gt;
        &lt;/li&gt;
        &lt;li class="breadcrumb-item"&gt;
            &lt;a href="/cloud-native-blogs/sitemap.html"&gt;Security&lt;/a&gt;
        &lt;/li&gt;
        &lt;li class="breadcrumb-item active" aria-current="page"&gt;
            RBAC Setup
        &lt;/li&gt;
    &lt;/ol&gt;
&lt;/nav&gt;</pre>

    <h2>Breadcrumb CSS</h2>
    <p>Add this to your page's <code>&lt;style&gt;</code> section:</p>

    <pre>/* Breadcrumb Navigation */
.breadcrumb {
    background: var(--bg-light);
    padding: 1rem 2rem;
    border-bottom: 1px solid var(--border);
    margin-bottom: 2rem;
}

.breadcrumb-list {
    list-style: none;
    display: flex;
    flex-wrap: wrap;
    gap: 0.5rem;
    align-items: center;
    max-width: 1200px;
    margin: 0 auto;
}

.breadcrumb-item {
    display: flex;
    align-items: center;
    gap: 0.5rem;
}

.breadcrumb-item a {
    color: var(--primary);
    text-decoration: none;
    font-weight: 500;
    transition: all 0.3s;
    display: flex;
    align-items: center;
    gap: 0.25rem;
}

.breadcrumb-item a:hover {
    color: var(--accent);
    text-decoration: underline;
}

.breadcrumb-item a i {
    font-size: 0.85rem;
}

.breadcrumb-item::after {
    content: "/";
    color: var(--text-gray);
    margin-left: 0.5rem;
    font-weight: 300;
}

.breadcrumb-item:last-child::after {
    content: "";
    margin: 0;
}

.breadcrumb-item.active {
    color: var(--text-gray);
    font-weight: 500;
}

/* Responsive */
@media (max-width: 768px) {
    .breadcrumb {
        padding: 0.75rem 1rem;
    }

    .breadcrumb-list {
        gap: 0.25rem;
    }

    .breadcrumb-item {
        font-size: 0.9rem;
    }
}</pre>

    <h2>Pages to Update with Breadcrumbs</h2>
    
    <h3>Priority 1 (Core Security Pages)</h3>
    <ul>
        <li><code>kubernetes/rbac_setup.html</code> - Breadcrumb: Home > Security > RBAC Setup</li>
        <li><code>kubernetes/k8s_security_index.html</code> - Breadcrumb: Home > Security > Security Index</li>
        <li><code>kubernetes/certificate_management.html</code> - Breadcrumb: Home > Security > Certificate Management</li>
        <li><code>kubernetes/secrets_management.html</code> - Breadcrumb: Home > Security > Secrets Management</li>
        <li><code>kubernetes/network_policies.html</code> - Breadcrumb: Home > Security > Network Policies</li>
    </ul>

    <h3>Priority 2 (Learning Paths)</h3>
    <ul>
        <li><code>learning-paths/advanced_topics.html</code> - Breadcrumb: Home > Learning > Advanced Topics</li>
        <li><code>learning-paths/interview_prep.html</code> - Breadcrumb: Home > Learning > Interview Prep</li>
        <li><code>learning-paths/resources_library.html</code> - Breadcrumb: Home > Learning > Resources</li>
    </ul>

    <h3>Priority 3 (CNCF & Architecture)</h3>
    <ul>
        <li><code>cncf-ecosystem/cncfscope.html</code> - Breadcrumb: Home > CNCF > Tools Overview</li>
        <li><code>architecture/cloud_native_architecture_flowchart.html</code> - Breadcrumb: Home > Architecture > Flowchart</li>
        <li><code>kubernetes/glossary.html</code> - Breadcrumb: Home > Resources > Glossary</li>
        <li><code>sitemap.html</code> - Breadcrumb: Home > Resources > Site Map</li>
    </ul>

    <h2>Implementation Template</h2>
    <p>For each page, customize the breadcrumb content and href paths:</p>

    <pre>&lt;!-- Example for kubernetes/rbac_setup.html --&gt;
&lt;nav class="breadcrumb" aria-label="Breadcrumb"&gt;
    &lt;ol class="breadcrumb-list"&gt;
        &lt;li class="breadcrumb-item"&gt;
            &lt;a href="/cloud-native-blogs/index.html"&gt;
                &lt;i class="fas fa-home"&gt;&lt;/i&gt; Home
            &lt;/a&gt;
        &lt;/li&gt;
        &lt;li class="breadcrumb-item"&gt;
            &lt;a href="/cloud-native-blogs/sitemap.html"&gt;Security&lt;/a&gt;
        &lt;/li&gt;
        &lt;li class="breadcrumb-item active" aria-current="page"&gt;
            RBAC Setup
        &lt;/li&gt;
    &lt;/ol&gt;
&lt;/nav&gt;</pre>

    <h2>Summary</h2>
    <p>This breadcrumb component:</p>
    <ul>
        <li>✅ Semantic HTML with aria-label and aria-current</li>
        <li>✅ Responsive design adapting to mobile (font-size: 0.9rem)</li>
        <li>✅ Consistent styling with design system colors</li>
        <li>✅ Hover effects on links (color + underline)</li>
        <li>✅ "/" separators that hide on last item</li>
        <li>✅ Home icon for visual clarity</li>
        <li>✅ Active state styling for current page</li>
    </ul>

</body>
</html>
