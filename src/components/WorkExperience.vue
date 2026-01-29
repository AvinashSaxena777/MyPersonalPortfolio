<template>
  <section id="experience" class="work-experience container">
    <h3 class="section-title">Work Experience</h3>
    <div class="experience-list">
      <div v-for="(job, index) in experience" :key="index" class="experience-item">
        <div class="experience-left">
          <div class="logo-wrapper">
             <div class="company-logo-container">
               <img :src="job.logo" :alt="job.company" class="company-logo" />
             </div>
          </div>
          <div class="job-meta">
            <h4 class="job-title">{{ job.title }}</h4>
            <div class="company-name">{{ job.company }}</div>
            <div class="job-duration">{{ job.duration }}</div>
            <div class="tech-stack-container">
               <h5 class="tech-heading">Key Skills</h5>
               <div class="tech-stack">
                 <span v-for="tech in job.techStack" :key="tech" class="tech-tag">{{ tech }}</span>
               </div>
            </div>
          </div>
        </div>
        
        <div class="experience-right">
          <div class="responsibilities-card">
            <ul class="job-responsibilities">
              <li v-for="(item, i) in job.responsibilities" :key="i">{{ item }}</li>
            </ul>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import sjsuLogo from '@/assets/img/sjsu-logo.png'
import nttLogo from '@/assets/img/ntt-logo.png'
import deloitteLogo from '@/assets/img/deloitte-logo.png'

const experience = [
  {
    title: 'Research Assistant',
    company: 'San Jose State University',
    location: 'San Jose, CA',
    duration: 'Jan 2025 – Mar 2025',
    logo: sjsuLogo,
    responsibilities: [
      'Developed Agentic AI application using LLMs and GraphQL to automate student resource retrieval, improving accessibility by 30%.',
      'Engineered a full-stack solution with Node.js, React, and Kafka for real-time data streaming, reducing deployment errors by 40% via CI/CD.',
      'Optimized LLM accuracy by 25% through meta-prompting and chain-of-thought reasoning with iterative feedback loops.',
      'Implemented curriculum learning by training models on datasets of increasing complexity, boosting query generalization by 18%.',
    ],
    techStack: ['LLMs', 'GraphQL', 'Node.js', 'React', 'Kafka', 'CI/CD'],
  },
  {
    title: 'Software Engineer - Salesforce',
    company: "NTT Data (Client: Dave & Buster's)",
    location: 'Hyderabad, India',
    duration: 'Sep 2021 – Jan 2024',
    logo: nttLogo,
    responsibilities: [
      'Managed a three-member team to integrate web applications with Salesforce (Sales Cloud/CPQ) using Mulesoft, increasing data synchronization speed by 30%.',
      'Engineered custom LWC-based interfaces to streamline sales workflows, reducing development cycles by 25% and enhancing cross-functional collaboration.',
      'Led change management and impact assessment for critical system updates, ensuring stakeholder buy-in and 99.9% service uptime.',
      'Automated production rollouts using Dockerized microservices and CI/CD pipelines, reducing errors by 40% through robust monitoring.',
    ],
    techStack: ['Salesforce', 'Mulesoft', 'LWC', 'Docker', 'CI/CD', 'Microservices'],
  },
  {
    title: 'Software Engineer',
    company: 'Deloitte (Client: Broadcom)',
    location: 'Hyderabad, India',
    duration: 'Jan 2020 – Sep 2021',
    logo: deloitteLogo,
    responsibilities: [
      'Enhanced Spring Microservice API performance by implementing caching and asynchronous processing, reducing response times by 66%.',
      'Scaled ELK Stack from a single-server setup to a distributed architecture across 4 Google Cloud Platform (GCP) servers, significantly improving system reliability.',
      'Optimized SQL query performance via targeted tuning, improving database response time by 35%.',
      'Resolved 80+ backend issues and implemented 40+ feature enhancements, increasing customer satisfaction by 20%.',
      'Engineered an asynchronous web crawler using Scrapy and multi-threading to identify broken links across 4 million pages with 95% accuracy.',
    ],
    techStack: ['Spring Boot', 'Java', 'ELK Stack', 'GCP', 'SQL', 'Scrapy'],
  },
]
</script>

<style scoped>
.work-experience {
  display: flex;
  flex-direction: column;
  padding-block: 4rem;
}

.section-title {
  text-transform: uppercase;
  margin-block-end: 3rem;
  font-size: var(--text-2xl);
  border-bottom: 2px solid var(--color-gray-800);
  padding-bottom: 1rem;
}

.experience-list {
  display: flex;
  flex-direction: column;
  gap: 5rem;
}

.experience-item {
  display: grid;
  grid-template-columns: 1fr 1.5fr;
  gap: 3rem;
  align-items: start;
}

/* Left Column Styling */
.experience-left {
  display: flex;
  flex-direction: column;
  gap: 1.5rem;
}

.logo-wrapper {
  margin-bottom: 0.5rem;
}

.company-logo-container {
  width: 80px;
  height: 80px;
  border-radius: 12px;
  background-color: var(--color-default-white); /* Logos usually standout better on white */
  border: 1px solid var(--color-gray-700);
  display: flex;
  align-items: center;
  justify-content: center;
  overflow: hidden;
  box-shadow: var(--elevation-2);
  padding: 0.5rem;
}

.company-logo {
  width: 100%;
  height: 100%;
  object-fit: contain;
}

.job-meta {
  display: flex;
  flex-direction: column;
  gap: 0.5rem;
}

.job-title {
  font-family: var(--font-title);
  font-size: calc(var(--text-xl) + 0.25rem);
  font-weight: var(--fw-bold);
  color: var(--color-accent);
  line-height: 1.2;
}

.company-name {
  font-size: var(--text-lg);
  font-weight: var(--fw-bold);
  color: var(--text-color-default);
}

.job-duration {
  font-family: var(--font-mono);
  font-size: var(--text-sm);
  color: var(--color-silver-600);
  text-transform: uppercase;
  letter-spacing: 1px;
  margin-top: 0.25rem;
}

.tech-stack-container {
  margin-top: 1.5rem;
}

.tech-heading {
  font-size: var(--text-xsm);
  text-transform: uppercase;
  color: var(--color-gray-400);
  margin-bottom: 0.75rem;
  letter-spacing: 1.5px;
}

.tech-stack {
  display: flex;
  flex-wrap: wrap;
  gap: 0.6rem;
}

.tech-tag {
  font-size: var(--text-xsm);
  font-family: var(--font-mono);
  color: var(--color-primary);
  background: color-mix(in srgb, var(--color-primary) 10%, transparent);
  padding: 0.3rem 0.8rem;
  border-radius: 4px;
  border: 1px solid color-mix(in srgb, var(--color-primary) 20%, transparent);
}

/* Right Column Styling */
.experience-right {
  position: relative;
}

.responsibilities-card {
  background: var(--color-gray-800);
  /* Use a lighter background for light mode via global theme vars if possible, 
     or rely on transparency/variables */
  background: color-mix(in srgb, var(--color-gray-800) 50%, transparent);
  backdrop-filter: blur(10px);
  padding: 2.5rem;
  border-radius: var(--radius-default);
  border: 1px solid var(--border-color);
  box-shadow: var(--elevation-3);
  position: relative;
  overflow: hidden;
  transition: transform 0.3s ease, box-shadow 0.3s ease;
}

.responsibilities-card::before {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  width: 4px;
  height: 100%;
  background: var(--color-accent);
  opacity: 0.8;
}

.responsibilities-card:hover {
  transform: translateY(-2px);
  box-shadow: var(--elevation-4);
}

.job-responsibilities {
  list-style: none;
  padding: 0;
  margin: 0;
}

.job-responsibilities li {
  position: relative;
  padding-left: 1.5rem;
  margin-bottom: 1rem;
  line-height: 1.6;
  color: var(--paragraph-color);
}

.job-responsibilities li::before {
  content: '▹';
  position: absolute;
  left: 0;
  color: var(--color-accent);
  font-size: 1.2rem;
  line-height: 1.4;
}

.job-responsibilities li:last-child {
  margin-bottom: 0;
}

/* Light Theme Overrides */
body[data-theme='light'] {
  & .responsibilities-card {
    background: color-mix(in srgb, var(--color-gray-100) 80%, transparent);
    border-color: var(--color-gray-300);
    box-shadow: var(--elevation-2);
  }
  
  & .job-responsibilities li {
    color: var(--text-color-default);
  }

  & .company-logo-container {
     background-color: var(--color-default-white);
     border-color: var(--color-gray-300);
  }
}

/* Responsive */
@media (--vw-md) {
  .experience-item {
    grid-template-columns: 1fr;
    gap: 2rem;
  }
  
  .experience-left {
    flex-direction: row;
    flex-wrap: wrap;
    align-items: center;
    gap: 1.5rem;
  }

  .logo-wrapper {
    margin-bottom: 0;
  }
  
  .job-meta {
    flex: 1;
  }

  .tech-stack-container {
      width: 100%;
  }

  .responsibilities-card {
    padding: 1.5rem;
  }
}

@media (--vw-sm) {
  .experience-left {
    flex-direction: column;
    align-items: flex-start;
  }
}
</style>
