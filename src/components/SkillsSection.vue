<template>
  <section id="skills" class="skills-section container">
    <div class="skills-header">
      <h3>Skills & Expertise</h3>
      <p class="skills-subtitle">My technical toolbox and areas of specialization.</p>
    </div>
    
    <div class="bento-grid">
      <!-- Software Engineering -->
      <div class="bento-card software">
        <div class="card-bg-icon">
          <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1">
            <polyline points="16 18 22 12 16 6"></polyline>
            <polyline points="8 6 2 12 8 18"></polyline>
          </svg>
        </div>
        <div class="card-header">
          <div class="icon-box">
            <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
              <polyline points="16 18 22 12 16 6"></polyline>
              <polyline points="8 6 2 12 8 18"></polyline>
            </svg>
          </div>
          <h4>Software Engineering</h4>
        </div>
        <div class="skills-grid">
          <div v-for="skill in skills.software" :key="skill.name" class="skill-item">
            <img :src="skill.image || `https://cdn.simpleicons.org/${skill.slug}`" :alt="skill.name" class="skill-icon" width="40" height="40" loading="lazy" />
            <span class="skill-name">{{ skill.name }}</span>
          </div>
        </div>
      </div>

      <!-- AI & Machine Learning -->
      <div class="bento-card ai">
         <div class="card-bg-icon">
          <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1">
             <path d="M12 2a10 10 0 1 0 10 10A10 10 0 0 0 12 2Zm0 18a8 8 0 1 1 8-8 8 8 0 0 1-8 8Z"/>
             <path d="M12 12v.01"/>
             <path d="M12 6a6 6 0 0 0-6 6v.01"/>
          </svg>
        </div>
        <div class="card-header">
          <div class="icon-box">
            <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
              <path d="M21 16V8a2 2 0 0 0-1-1.73l-7-4a2 2 0 0 0-2 0l-7 4A2 2 0 0 0 3 8v8a2 2 0 0 0 1 1.73l7 4a2 2 0 0 0 2 0l7-4A2 2 0 0 0 21 16z"></path>
              <polyline points="3.27 6.96 12 12.01 20.73 6.96"></polyline>
              <line x1="12" y1="22.08" x2="12" y2="12"></line>
            </svg>
          </div>
          <h4>AI & Machine Learning</h4>
        </div>
         <div class="skills-grid">
          <div v-for="skill in skills.ai" :key="skill.name" class="skill-item">
             <img :src="skill.image || `https://cdn.simpleicons.org/${skill.slug}`" :alt="skill.name" class="skill-icon" width="40" height="40" loading="lazy" />
            <span class="skill-name">{{ skill.name }}</span>
          </div>
        </div>
      </div>

      <!-- Salesforce -->
      <div class="bento-card salesforce">
         <div class="card-bg-icon">
          <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1">
             <path d="M18 10h-1.26A8 8 0 1 0 9 20h9a5 5 0 0 0 0-10z"></path>
          </svg>
        </div>
        <div class="card-header">
           <div class="icon-box">
             <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
               <path d="M18 10h-1.26A8 8 0 1 0 9 20h9a5 5 0 0 0 0-10z"></path>
             </svg>
           </div>
           <h4>Salesforce</h4>
        </div>
         <div class="skills-grid">
          <div v-for="skill in skills.salesforce" :key="skill.name" class="skill-item">
             <img :src="skill.image || `https://cdn.simpleicons.org/${skill.slug}`" :alt="skill.name" class="skill-icon" width="40" height="40" loading="lazy" />
            <span class="skill-name">{{ skill.name }}</span>
          </div>
        </div>
      </div>

      <!-- Cloud & DevOps -->
      <div class="bento-card cloud">
         <div class="card-bg-icon">
          <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1">
             <rect x="2" y="2" width="20" height="8" rx="2" ry="2"></rect>
             <rect x="2" y="14" width="20" height="8" rx="2" ry="2"></rect>
             <line x1="6" y1="6" x2="6.01" y2="6"></line>
             <line x1="6" y1="18" x2="6.01" y2="18"></line>
          </svg>
        </div>
        <div class="card-header">
          <div class="icon-box">
            <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
               <path d="M22 6a2 2 0 0 1-2 2H4a2 2 0 0 1-2-2V5a2 2 0 0 1 2-2h16a2 2 0 0 1 2 2v1Z"/>
               <path d="M22 13a2 2 0 0 1-2 2H4a2 2 0 0 1-2-2v-1a2 2 0 0 1 2-2h16a2 2 0 0 1 2 2v1Z"/>
               <path d="M22 20a2 2 0 0 1-2 2H4a2 2 0 0 1-2-2v-1a2 2 0 0 1 2-2h16a2 2 0 0 1 2 2v1Z"/>
            </svg>
          </div>
          <h4>Cloud & DevOps</h4>
        </div>
         <div class="skills-grid">
          <div v-for="skill in skills.cloud" :key="skill.name" class="skill-item">
             <img :src="skill.image || `https://cdn.simpleicons.org/${skill.slug}`" :alt="skill.name" class="skill-icon" width="40" height="40" loading="lazy" />
            <span class="skill-name">{{ skill.name }}</span>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import javaImg from '@/assets/img/java.png'
import genAiImg from '@/assets/img/ai.png'
import awsImg from '@/assets/img/aws.png'

const skills = {
  software: [
    { name: 'Java', image: javaImg },
    { name: 'Python', slug: 'python' },
    { name: 'Node.js', slug: 'nodedotjs' },
    { name: 'Spring Boot', slug: 'springboot' },
    { name: 'GraphQL', slug: 'graphql' },
    { name: 'React', slug: 'react' },
    { name: 'Kafka', slug: 'apachekafka' },
    { name: 'Hibernate', slug: 'hibernate' },
    { name: 'Django', slug: 'django' },
    { name: 'Agile', slug: 'jirasoftware' }
  ],
  ai: [
    { name: 'GenAI', image: genAiImg },
    { name: 'LangChain', slug: 'langchain' },
    { name: 'TensorFlow', slug: 'tensorflow' },
    { name: 'PyTorch', slug: 'pytorch' },
    { name: 'Scikit-learn', slug: 'scikitlearn' },
    { name: 'NLP', slug: 'huggingface' },
    { name: 'Recommender', slug: 'pandas' },
    { name: 'SageMaker', slug: 'amazon' }
  ],
  salesforce: [
    { name: 'Apex', slug: 'salesforce' },
    { name: 'LWC', slug: 'javascript' },
    { name: 'SOQL', slug: 'databricks' },
    { name: 'Async Apex', slug: 'salesforce' }
  ],
  cloud: [
    { name: 'AWS', image: awsImg },
    { name: 'GCP', slug: 'googlecloud' },
    { name: 'Docker', slug: 'docker' },
    { name: 'Kubernetes', slug: 'kubernetes' },
    { name: 'Jenkins', slug: 'jenkins' },
    { name: 'Git', slug: 'git' },
    { name: 'Elastic Stack', slug: 'elasticsearch' },
    { name: 'Shell', slug: 'gnubash' },
    { name: 'SQL Tuning', slug: 'mysql' }
  ]
}
</script>

<style scoped>
.skills-section {
  flex-direction: column;
  padding-block: 4rem;
  overflow: visible;
}

.skills-header {
  margin-bottom: 3rem;
  
  h3 {
    text-transform: uppercase;
    font-size: var(--text-2xl);
    border-bottom: 2px solid var(--color-gray-800);
    padding-bottom: 1rem;
    margin-bottom: 0.5rem;
  }
}

.skills-subtitle {
  color: var(--color-gray-400);
  font-size: var(--text-lg);
}

.bento-grid {
  display: grid;
  grid-template-columns: repeat(12, 1fr);
  gap: 1.5rem;
  width: 100%;
}

.bento-card {
  background: color-mix(in srgb, var(--color-gray-800) 40%, transparent);
  backdrop-filter: blur(12px);
  border: 1px solid var(--border-color);
  border-radius: 16px;
  padding: 2rem;
  position: relative;
  overflow: hidden;
  display: flex;
  flex-direction: column;
  gap: 1.5rem;
  transition: all 0.4s ease;
}

.bento-card:hover {
  border-color: var(--color-accent);
  box-shadow: var(--elevation-3);
  background: color-mix(in srgb, var(--color-gray-800) 60%, transparent);
}

.software { grid-column: span 7; }
.ai { grid-column: span 5; }
.salesforce { grid-column: span 5; }
.cloud { grid-column: span 7; }

/* Header */
.card-header {
  display: flex;
  align-items: center;
  gap: 1rem;
  z-index: 2;
  margin-bottom: 0.5rem;
}

.icon-box {
  width: 48px;
  height: 48px;
  background: var(--color-default-black);
  border-radius: 12px;
  display: flex;
  align-items: center;
  justify-content: center;
  flex-shrink: 0;
  border: 1px solid var(--color-gray-700);
  color: var(--color-accent);
  
  svg {
    width: 24px;
    height: 24px;
  }
}

h4 {
  font-size: var(--text-xl);
  font-weight: var(--fw-bold);
  margin: 0;
  color: var(--color-default-white);
}

/* Skills Grid */
.skills-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(80px, 1fr));
  gap: 1.5rem 1rem;
  z-index: 2;
}

.skill-item {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center; /* Important for alignment */
  text-align: center;
  gap: 0.75rem;
  transition: transform 0.2s ease;
  min-height: 80px; /* Ensure uniform height for easier clicking/hovering */
}

.skill-item:hover {
  transform: translateY(-5px);
}

.skill-icon {
  width: 40px;
  height: 40px;
  object-fit: contain;
  filter: grayscale(0.4);
  transition: filter 0.2s ease, transform 0.2s ease;
}

.skill-item:hover .skill-icon {
  filter: grayscale(0);
  transform: scale(1.1);
}

.skill-name {
  font-family: var(--font-mono);
  font-size: var(--text-xs);
  color: var(--color-gray-300);
  line-height: 1.2;
}

.skill-item:hover .skill-name {
  color: var(--color-accent);
  font-weight: var(--fw-bold);
}

/* Background Icons */
.card-bg-icon {
  position: absolute;
  right: -20px;
  bottom: -20px;
  width: 180px;
  height: 180px;
  opacity: 0.05;
  transform: rotate(-15deg);
  pointer-events: none;
  z-index: 1;
  
  svg {
    width: 100%;
    height: 100%;
  }
}

/* Light Mode Overrides */
body[data-theme='light'] {
  & .bento-card {
    background: rgba(255, 255, 255, 0.65);
    border-color: var(--color-gray-300);
    box-shadow: var(--elevation-2);
  }
  
  & .bento-card:hover {
    background: rgba(255, 255, 255, 0.9);
  }

  & h4 {
    color: var(--color-gray-800);
  }
  
  & .skill-name {
    color: var(--color-gray-600);
  }
  
  & .skill-item:hover .skill-name {
    color: var(--color-primary);
  }
  
  & .icon-box {
    background: var(--color-gray-100);
    border-color: var(--color-gray-200);
    color: var(--color-primary);
  }
  
  & .skills-subtitle {
    color: var(--color-gray-600);
  }
}

/* Responsive */
@media (--vw-md) {
  .bento-grid {
    grid-template-columns: 1fr;
  }
  
  .bento-card {
    grid-column: span 1 !important;
  }
  
  .skills-grid {
    grid-template-columns: repeat(auto-fill, minmax(70px, 1fr));
  }
  
  .skill-icon {
    width: 32px;
    height: 32px;
  }
}
</style>
