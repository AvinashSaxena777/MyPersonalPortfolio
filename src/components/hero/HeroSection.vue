<template>
  <section class="hero container has-ellipse-curve">
    <div class="hero-content">
      <h1 class="hero__headline">Hey, I'm Avinash 🖖</h1>
      <div class="hero__location">
        <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
          <path d="M21 10c0 7-9 13-9 13s-9-6-9-13a9 9 0 0 1 18 0z"></path>
          <circle cx="12" cy="10" r="3"></circle>
        </svg>
        San Jose, CA
      </div>
      <p class="hero__description">
        Software Engineer with 3+ years of experience building scalable backend systems and Salesforce integrations. M.S. in AI with expertise in GenAI and data-driven automation.
        <br>
        <span class="seeking-roles">🚀 Actively seeking full-time SWE / ML roles in the US (Available Immediately).</span>
      </p>
      <SocialMediaIcons />
    </div>
    <aside class="hero-aside">
      <ScrollIndicator class="is-mobile-only" />
      <h2 class="hero__subheadline">software engineer</h2>
      <HeroAvatar>
        <img
src="@/assets/img/profile.jpg" alt="me" class="hero-avatar__image" width="140" height="140"
          loading="lazy" />
      </HeroAvatar>
    </aside>
  </section>
</template>

<style scoped>
.hero {
  display: grid;
  grid-template-columns: minmax(50%, 700px) auto;
  align-items: center;
  padding: 3rem 0;
}

.hero__headline {
  font-size: var(--text-3xl);
  font-size: clamp(var(--text-xl), 1vw + var(--text-2xl), var(--text-3xl));
  font-weight: var(--fw-bold);
  margin-bottom: 0.5rem;
}

.hero__location {
  display: flex;
  align-items: center;
  gap: 0.5rem;
  color: var(--color-gray-400);
  font-family: var(--font-mono);
  font-size: var(--text-sm);
  margin-bottom: 1.5rem;
  
  svg {
    width: 16px;
    height: 16px;
    color: var(--color-accent);
  }
}

.hero__subheadline {
  display: grid;
  grid-template-columns: 1fr auto 1fr;
  gap: 1em;
  font-size: var(--text-sm);
  font-family: var(--font-mono);
  font-weight: var(--fw-normal);
  writing-mode: vertical-lr;
  text-transform: uppercase;
  letter-spacing: 2.5px;
  color: var(--color-gray-400);
  margin: 0 1rem;

  &::before,
  &::after {
    content: '';
    border-bottom: 1px solid var(--color-gray-400);
    align-self: center;
    justify-self: center;
    min-width: 24px;
    transform: rotate(90deg);
  }
}

.hero__description {
  font-size: clamp(var(--text-base), 1vw + var(--text-lg), var(--text-xl));
  margin-block-end: 1.5rem;
  color: var(--color-silver-600);
  line-height: 1.6;
}

.seeking-roles {
  display: inline-block;
  margin-top: 0.75rem;
  font-weight: var(--fw-bold);
  color: var(--color-accent);
  font-size: 0.9em;
}

.hero-aside {
  display: flex;
  justify-self: end;
  padding: 0 17px;
}

@media screen and (min-width: 64em) {
  .hero {
    &::after {
      content: '';
      background-color: var(--color-gray-600);
      opacity: 0.1;
      position: absolute;
      width: 100%;
      z-index: var(--z-hide);
      left: 0;
      top: 0;
    }

    &.has-ellipse-curve::after {
      content: '';
      clip-path: ellipse(100% 55% at 48% 44%);
      height: calc(500px + 2vw);
    }

    &.has-triangle-down::after {
      clip-path: polygon(50% 63%, 100% 38%, 100% 2%, 0% 1%, 0% 38%);
      height: calc(500px + 3vw);
    }
  }

  body[data-theme='light'] .hero::after {
    content: '';
    background-color: var(--color-gray-300);
  }
}

@media (--vw-lg) {
  .hero-avatar {
    display: none;
  }
}

@media (--vw-sm) {
  .hero {
    height: 100vh;
    height: 100dvh;
    grid-template-columns: 1fr;
  }

  .hero-content {
    text-align: center;
  }

  .hero__headline {
    font-size: calc(var(--text-xl) + 0.75rem);
    letter-spacing: 1.2px;
  }

  .social-media-icons a {
    padding: 8px;
  }

  .social-media-icons a svg {
    max-width: 35px;
  }
}
</style>
