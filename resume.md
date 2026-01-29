---
layout: default
title: Resume
permalink: /resume/
---

<div class="resume-page">
    <div class="container">
        <h1>Resume</h1>
        <p class="resume-description">View or download my CV below.</p>
        <div class="resume-viewer">
            <iframe
                src="{{ '/Daniel Adejumo_CV.pdf' | relative_url }}"
                title="Daniel Adejumo CV"
                loading="lazy"
            ></iframe>
        </div>
        <p class="resume-fallback">
            If the PDF does not render, <a href="{{ '/Daniel Adejumo_CV.pdf' | relative_url }}" target="_blank" rel="noopener">open it in a new tab</a>.
        </p>
    </div>
</div>

<style>
.resume-page {
    padding: var(--spacing-xl) 0;
}

.resume-page h1 {
    text-align: center;
    color: var(--text-primary);
    margin-bottom: var(--spacing-md);
}

.resume-description {
    text-align: center;
    color: var(--text-secondary);
    margin-bottom: var(--spacing-xl);
}

.resume-viewer {
    border: 1px solid var(--border-color);
    border-radius: var(--radius-md);
    overflow: hidden;
    background: var(--surface-color);
    box-shadow: 0 8px 24px var(--shadow-color);
}

.resume-viewer iframe {
    width: 100%;
    height: 80vh;
    border: 0;
}

.resume-fallback {
    text-align: center;
    margin-top: var(--spacing-lg);
}
</style>
