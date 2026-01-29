<template>
  <section id="publications" class="publications-section container">
    <div class="header-group">
      <h3>Publications</h3>
      <div class="connector-line"></div>
    </div>

    <div class="pub-card-wrapper">
      <div class="pub-card">
        <div class="pub-type-badge">Master's Thesis</div>
        
        <div class="pub-content">
          <div class="pub-icon">
            <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5">
              <path d="M4 19.5A2.5 2.5 0 0 1 6.5 17H20"></path>
              <path d="M6.5 2H20v20H6.5A2.5 2.5 0 0 1 4 19.5v-15A2.5 2.5 0 0 1 6.5 2z"></path>
            </svg>
          </div>
          
          <div class="pub-details">
            <h4 class="pub-title">
              Retrieval Augmented Framework for Deepfake Audio Detection
            </h4>
            
            <div class="pub-meta">
              <span class="pub-year">
                <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
                  <rect x="3" y="4" width="18" height="18" rx="2" ry="2"></rect>
                  <line x1="16" y1="2" x2="16" y2="6"></line>
                  <line x1="8" y1="2" x2="8" y2="6"></line>
                  <line x1="3" y1="10" x2="21" y2="10"></line>
                </svg>
                Jan 2026
              </span>
              <span class="pub-status status-pending">
                <span class="status-dot"></span>
                Yet to be published
              </span>
            </div>
          </div>
          
          <div class="pub-action">
             <a href="#" class="read-btn disabled" aria-disabled="true">
               <span>Read Paper</span>
               <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
                 <line x1="5" y1="12" x2="19" y2="12"></line>
                 <polyline points="12 5 19 12 12 19"></polyline>
               </svg>
             </a>
          </div>
        </div>
        
        <!-- Background Pattern -->
        <div class="bg-pattern">
           <svg width="100%" height="100%" fill="none">
             <defs>
               <pattern id="dot-pattern" x="0" y="0" width="20" height="20" patternUnits="userSpaceOnUse">
                 <circle cx="2" cy="2" r="1" class="pattern-dot" />
               </pattern>
             </defs>
             <rect width="100%" height="100%" fill="url(#dot-pattern)" />
           </svg>
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped>
.publications-section {
  flex-direction: column;
  padding-block: 4rem;
}

.header-group {
  display: flex;
  align-items: center;
  gap: 2rem;
  margin-bottom: 3rem;
  
  h3 {
    text-transform: uppercase;
    font-size: var(--text-2xl);
    margin: 0;
    white-space: nowrap;
  }
}

.connector-line {
  height: 2px;
  background: linear-gradient(90deg, var(--color-gray-800), transparent);
  width: 100%;
  border-radius: 99px;
}

.pub-card-wrapper {
  display: flex;
  flex-direction: column;
  gap: 2rem;
}

.pub-card {
  position: relative;
  background: var(--color-gray-800);
  border: 1px solid var(--border-color);
  border-radius: 16px;
  padding: 3rem 2rem;
  overflow: hidden;
  transition: all 0.3s ease;
  display: flex;
  flex-direction: column;
}

.pub-card:hover {
  transform: translateY(-5px);
  border-color: var(--color-accent);
  box-shadow: var(--elevation-3);
}

.pub-type-badge {
  position: absolute;
  top: 0;
  right: 0;
  background: var(--color-accent);
  color: var(--color-default-black);
  padding: 0.4rem 1.2rem;
  border-bottom-left-radius: 16px;
  font-family: var(--font-mono);
  font-size: var(--text-xs);
  font-weight: var(--fw-bold);
  text-transform: uppercase;
  z-index: 2;
}

.pub-content {
  display: flex;
  align-items: center;
  gap: 2rem;
  z-index: 2;
}

.pub-icon {
  width: 64px;
  height: 64px;
  background: rgba(255,255,255,0.05);
  border-radius: 12px;
  display: flex;
  align-items: center;
  justify-content: center;
  flex-shrink: 0;
  color: var(--color-accent);
  border: 1px solid var(--color-gray-700);
  
  svg { width: 32px; height: 32px; }
}

.pub-details {
  flex: 1;
}

.pub-title {
  font-family: var(--font-title);
  font-size: var(--text-xl);
  font-weight: var(--fw-bold);
  color: var(--color-default-white);
  margin-bottom: 1rem;
  line-height: 1.3;
}

.pub-meta {
  display: flex;
  gap: 1.5rem;
  align-items: center;
  font-family: var(--font-mono);
  font-size: var(--text-sm);
}

.pub-year {
  display: flex;
  align-items: center;
  gap: 0.5rem;
  color: var(--color-silver-600);
  
  svg { width: 16px; height: 16px; }
}

.pub-status {
  display: inline-flex;
  align-items: center;
  gap: 0.5rem;
  padding: 0.2rem 0.8rem;
  border-radius: 99px;
  font-size: var(--text-xs);
  border: 1px solid currentColor;
}

.status-pending {
  color: #fbbf24; /* Amber for pending */
  background: rgba(251, 191, 36, 0.1);
  border-color: rgba(251, 191, 36, 0.3);
}

.status-dot {
  width: 6px;
  height: 6px;
  border-radius: 50%;
  background: currentColor;
  animation: pulse 2s infinite;
}

.pub-action {
  margin-left: auto;
}

.read-btn {
  display: flex;
  align-items: center;
  gap: 0.5rem;
  color: var(--color-default-white);
  padding: 0.6rem 1.2rem;
  border-radius: 8px;
  background: var(--color-primary);
  font-weight: var(--fw-bold);
  font-size: var(--text-sm);
  transition: all 0.2s;
  
  svg { width: 18px; height: 18px; }
}

.read-btn:hover:not(.disabled) {
  opacity: 0.9;
  transform: translateX(5px);
  text-decoration: none;
}

.read-btn.disabled {
  background: var(--color-gray-700);
  color: var(--color-gray-400);
  cursor: not-allowed;
  opacity: 0.7;
}

/* Background Pattern */
.bg-pattern {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  z-index: 1;
  opacity: 0.3;
  pointer-events: none;
}

.pattern-dot {
  fill: var(--color-gray-700);
}

@keyframes pulse {
  0% { opacity: 1; }
  50% { opacity: 0.4; }
  100% { opacity: 1; }
}

/* Light Theme Overrides */
body[data-theme='light'] {
  & .header-group h3 { color: var(--text-color-default); }
  & .connector-line { background: linear-gradient(90deg, var(--color-gray-300), transparent); }

  & .pub-card {
    background: var(--color-default-white);
    border-color: var(--color-gray-300);
    box-shadow: var(--elevation-2);
  }

  & .pub-card:hover { border-color: var(--color-accent); }
  
  & .pub-icon {
    background: var(--color-gray-100);
    border-color: var(--color-gray-200);
  }
  
  & .pub-title { color: var(--color-gray-800); }
  & .pub-year { color: var(--color-gray-600); }
  
  & .pattern-dot { fill: var(--color-gray-200); }
  
  & .read-btn.disabled {
    background: var(--color-gray-200);
    color: var(--color-gray-400);
  }
}

@media (--vw-md) {
  .pub-content {
    flex-direction: column;
    align-items: flex-start;
    gap: 1.5rem;
  }
  
  .pub-action {
    margin-left: 0;
    width: 100%;
  }
  
  .read-btn {
    justify-content: center;
    width: 100%;
  }
}
</style>
