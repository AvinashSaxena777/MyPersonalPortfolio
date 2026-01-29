<template>
  <section id="education" class="education-section container">
    <div class="header-group">
      <h3>Education</h3>
      <div class="connector-line"></div>
    </div>

    <div class="education-grid">
      <div v-for="(edu, index) in education" :key="index" class="edu-card">
        <div class="edu-icon-wrapper">
          <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round">
            <path d="M22 10v6M2 10l10-5 10 5-10 5z"/>
            <path d="M6 12v5c3 3 9 3 12 0v-5"/>
          </svg>
        </div>
        
        <div class="edu-content">
          <span class="edu-period">{{ edu.period }}</span>
          <h4 class="edu-degree">{{ edu.degree }}</h4>
          <div class="edu-school-group">
            <span class="edu-school">{{ edu.school }}</span>
            <span class="edu-location">{{ edu.location }}</span>
          </div>
          
          <div class="edu-stats">
            <div class="gpa-badge">
              <span class="label">GPA</span>
              <span class="value">{{ edu.gpa }}</span>
            </div>
          </div>

          <div class="coursework">
            <h5 class="coursework-label">Relevant Coursework:</h5>
            <p>{{ edu.coursework }}</p>
          </div>
        </div>
        
        <!-- Decorative background element -->
        <div class="bg-decoration"></div>
      </div>
    </div>
  </section>
</template>

<script setup>
const education = [
  {
    degree: 'Master of Science, Artificial Intelligence',
    school: 'San Jose State University',
    location: 'San Jose, CA, USA',
    period: 'Jan 2024 - Dec 2025',
    gpa: '3.9 / 4.0',
    coursework: 'Recommender Systems, Deep Learning, Natural Language Processing'
  },
  {
    degree: 'Bachelor of Engineering, Information Technology',
    school: 'SGSITS Indore',
    location: 'Madhya Pradesh, India',
    period: 'Jul 2015 - May 2019',
    gpa: '3.8 / 4.0',
    coursework: 'Data Structures and Algorithms, Operating Systems, Cloud Computing'
  }
]
</script>

<style scoped>
.education-section {
  flex-direction: column;
  padding-block: 2rem 4rem;
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

.education-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(350px, 1fr));
  gap: 2rem;
}

.edu-card {
  position: relative;
  background: var(--color-gray-800);
  background: color-mix(in srgb, var(--color-gray-800) 40%, transparent);
  backdrop-filter: blur(10px);
  border: 1px solid var(--border-color);
  border-radius: 16px;
  padding: 2.5rem 2rem;
  display: flex;
  flex-direction: column;
  gap: 1.5rem;
  overflow: hidden;
  transition: all 0.3s ease;
}

.edu-card:hover {
  transform: translateY(-5px);
  border-color: var(--color-accent);
  background: color-mix(in srgb, var(--color-gray-800) 60%, transparent);
  box-shadow: var(--elevation-3);
}

.edu-icon-wrapper {
  width: 50px;
  height: 50px;
  background: var(--color-default-black);
  border: 1px solid var(--color-gray-700);
  border-radius: 12px;
  display: flex;
  align-items: center;
  justify-content: center;
  color: var(--color-accent);
  z-index: 2;
  
  svg {
    width: 28px;
    height: 28px;
  }
}

.edu-content {
  z-index: 2;
  display: flex;
  flex-direction: column;
}

.edu-period {
  font-family: var(--font-mono);
  font-size: var(--text-xs);
  color: var(--color-gray-400);
  margin-bottom: 0.5rem;
  letter-spacing: 1px;
}

.edu-degree {
  font-size: var(--text-xl);
  font-weight: var(--fw-bold);
  line-height: 1.2;
  margin-bottom: 0.75rem;
  color: var(--color-default-white);
}

.edu-school-group {
  display: flex;
  flex-direction: column;
  gap: 0.2rem;
  margin-bottom: 1.5rem;
  font-size: var(--text-base);
  color: var(--color-silver-600);
}

.edu-school {
  font-weight: var(--fw-bold);
  color: var(--color-primary);
}

.edu-stats {
  margin-bottom: 1.5rem;
}

.gpa-badge {
  display: inline-flex;
  align-items: center;
  gap: 0.5rem;
  background: rgba(255,255,255,0.05);
  border: 1px solid var(--color-gray-700);
  padding: 0.3rem 0.8rem;
  border-radius: 99px;
  font-family: var(--font-mono);
  font-size: var(--text-sm);
}

.gpa-badge .label {
  color: var(--color-gray-400);
  font-weight: var(--fw-bold);
}

.gpa-badge .value {
  color: var(--color-accent);
}

.coursework {
  border-top: 1px dashed var(--color-gray-700);
  padding-top: 1rem;
}

.coursework-label {
  font-size: var(--text-xs);
  text-transform: uppercase;
  color: var(--color-gray-400);
  margin-bottom: 0.5rem;
  letter-spacing: 0.5px;
}

.coursework p {
  font-size: var(--text-sm);
  line-height: 1.6;
  color: var(--paragraph-color);
}

.bg-decoration {
  position: absolute;
  top: -20px;
  right: -20px;
  width: 150px;
  height: 150px;
  background: radial-gradient(circle, var(--color-accent) 0%, transparent 70%);
  opacity: 0.05;
  border-radius: 50%;
  pointer-events: none;
  z-index: 1;
}

.edu-card:hover .bg-decoration {
  opacity: 0.1;
  transform: scale(1.2);
  transition: transform 0.5s ease;
}

/* Light Theme Overrides */
body[data-theme='light'] {
  & .header-group h3 { color: var(--text-color-default); }
  & .connector-line { background: linear-gradient(90deg, var(--color-gray-300), transparent); }

  & .edu-card {
    background: rgba(255, 255, 255, 0.7);
    border-color: var(--color-gray-300);
    box-shadow: var(--elevation-2);
  }

  & .edu-card:hover {
    background: rgba(255, 255, 255, 0.95);
    border-color: var(--color-accent);
  }

  & .edu-icon-wrapper {
    background: var(--color-gray-100);
    border-color: var(--color-gray-300);
  }

  & .edu-degree { color: var(--color-gray-800); }
  & .edu-school-group { color: var(--color-gray-600); }
  & .edu-school { color: var(--color-primary); } /* Keep primary color */
  
  & .gpa-badge {
    background: var(--color-gray-100);
    border-color: var(--color-gray-300);
  }
  
  & .gpa-badge .label { color: var(--color-gray-600); }
  & .coursework { border-top-color: var(--color-gray-300); }
  & .coursework p { color: var(--color-gray-700); }
}

@media (--vw-sm) {
  .education-grid {
    grid-template-columns: 1fr;
  }
}
</style>
