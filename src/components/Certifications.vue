<template>
  <section id="certifications" class="certifications-section container">
    <div class="header-group">
      <h3>Certifications</h3>
      <div class="connector-line"></div>
    </div>

    <div class="certs-grid">
      <div v-for="(cert, index) in certifications" :key="index" class="cert-ticket">
        <div class="ticket-stub">
          <div class="stub-icon">
            <img src="https://cdn-icons-png.flaticon.com/512/5968/5968914.png" alt="Salesforce" class="cert-icon" width="32" height="32" />
          </div>
          <div class="stub-decorative-circles">
            <span class="circle top"></span>
            <span class="circle bottom"></span>
          </div>
        </div>
        
        <div class="ticket-body">
          <div class="cert-info">
             <span class="cert-issuer">Salesforce Certified</span>
             <h4 class="cert-name">{{ cert.name }}</h4>
          </div>
          <a :href="cert.link" class="verify-btn" target="_blank" rel="noopener noreferrer">
            <span>Verify</span>
            <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
              <path d="M10 13a5 5 0 0 0 7.54.54l3-3a5 5 0 0 0-7.07-7.07l-1.72 1.71"></path>
              <path d="M14 11a5 5 0 0 0-7.54-.54l-3 3a5 5 0 0 0 7.07 7.07l1.71-1.71"></path>
            </svg>
          </a>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
const certifications = [
  { name: 'CPQ and Billing Consultant Accredited Professional', link: 'https://www.credly.com/go/0Ptn4HGj' },
  { name: 'Platform Developer II', link: 'https://sforce.co/verifycerts' },
  { name: 'CPQ Specialist', link: 'https://sforce.co/verifycerts' },
  { name: 'Sales Cloud Consultant', link: 'https://sforce.co/verifycerts' },  
  { name: 'Platform Developer I', link: 'https://sforce.co/verifycerts' },
  { name: 'Administrator', link: 'https://sforce.co/verifycerts' },
]
</script>

<style scoped>
.certifications-section {
  flex-direction: column;
  padding-block: 4rem;
  padding-block-start: 1rem;
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

.certs-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(320px, 1fr));
  gap: 2rem;
}

/* Ticket Design */
.cert-ticket {
  display: flex;
  min-height: 100px;
  filter: drop-shadow(var(--elevation-2));
  transition: transform 0.3s ease, filter 0.3s ease;
}

.cert-ticket:hover {
  transform: translateY(-4px);
  filter: drop-shadow(var(--elevation-3));
}

/* Stub (Left Side) */
.ticket-stub {
  width: 80px;
  background: var(--color-accent);
  border-top-left-radius: 12px;
  border-bottom-left-radius: 12px;
  display: flex;
  align-items: center;
  justify-content: center;
  position: relative;
  /* Dotted separator line on right */
  border-right: 2px dashed rgba(0,0,0,0.2);
}

.stub-icon {
  width: 48px;
  height: 48px;
  background: rgba(0,0,0,0.2);
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
}

.cert-icon {
  filter: brightness(0) invert(1);
}

.circle {
  position: absolute;
  width: 20px;
  height: 20px;
  background-color: var(--color-default-black); /* Matches background */
  border-radius: 50%;
  right: -10px;
  z-index: 2;
}

.top { top: -10px; }
.bottom { bottom: -10px; }

/* Body (Right Side) */
.ticket-body {
  flex: 1;
  background: var(--color-gray-800);
  border-top-right-radius: 12px;
  border-bottom-right-radius: 12px;
  padding: 1rem 1.5rem;
  display: flex;
  justify-content: space-between;
  align-items: center;
  gap: 1rem;
  position: relative;
  border: 1px solid var(--border-color);
  border-left: none;
}

.cert-info {
  display: flex;
  flex-direction: column;
  gap: 0.25rem;
  flex: 1;
}

.cert-issuer {
  font-family: var(--font-mono);
  font-size: var(--text-xs);
  text-transform: uppercase;
  color: var(--color-gray-400);
  letter-spacing: 1px;
}

.cert-name {
  font-size: var(--text-base);
  font-weight: var(--fw-bold);
  color: var(--color-default-white);
  line-height: 1.2;
  margin: 0;
}

/* Verify Button */
.verify-btn {
  display: flex;
  align-items: center;
  gap: 0.5rem;
  padding: 0.4rem 0.8rem;
  border: 1px solid var(--color-gray-600);
  border-radius: 99px;
  color: var(--color-gray-300);
  font-size: var(--text-xs);
  font-weight: var(--fw-bold);
  transition: all 0.2s ease;
  flex-shrink: 0;
  
  svg {
    width: 14px;
    height: 14px;
  }
}

.verify-btn:hover {
  border-color: var(--color-accent);
  color: var(--color-accent);
  background: rgba(255,255,255,0.05);
  text-decoration: none;
}

/* Light Theme */
body[data-theme='light'] {
  & .header-group h3 {
     color: var(--text-color-default);
  }

  & .connector-line {
    background: linear-gradient(90deg, var(--color-gray-300), transparent);
  }

  & .ticket-body {
    background: var(--color-default-white);
    border-color: var(--color-gray-300);
  }
  
  & .cert-name {
    color: var(--color-gray-800);
  }
  
  & .cert-issuer {
    color: var(--color-gray-500);
  }
  
   & .circle {
    background-color: var(--color-light); /* Matches background */
  }
  
  & .verify-btn {
    border-color: var(--color-gray-300);
    color: var(--color-gray-600);
  }
  
  & .verify-btn:hover {
    border-color: var(--color-accent);
    color: var(--color-accent);
    background: var(--color-gray-100);
  }
}

/* Responsive */
@media (--vw-sm) {
  .certs-grid {
    grid-template-columns: 1fr;
  }
  
  .cert-ticket {
    height: auto;
    flex-direction: column;
  }
  
  .ticket-stub {
    width: 100%;
    height: 60px;
    border-radius: 12px 12px 0 0;
    border-right: none;
    border-bottom: 2px dashed rgba(0,0,0,0.2);
  }
  
  .ticket-body {
    border-radius: 0 0 12px 12px;
    border-left: 1px solid var(--border-color);
    border-top: none;
    padding: 1.5rem;
    flex-direction: row;
  }
  
  .stub-decorative-circles {
    display: none;
  }
}
</style>
