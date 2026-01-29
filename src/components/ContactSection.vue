<template>
  <section id="contact" class="contact-section container">
    <div class="header-group">
      <h3>Get In Touch</h3>
      <div class="connector-line"></div>
    </div>
    
    <!-- Notification Popup -->
    <transition name="fade">
      <div v-if="notification.show" class="notification-popup" :class="notification.type">
        <span>{{ notification.message }}</span>
        <button @click="closeNotification" class="close-btn">&times;</button>
      </div>
    </transition>
    
    <div class="contact-content">
      <div class="contact-text">
        <p>
          Whether it's a freelance gig, a collaboration, or a full-time opportunity, or want to say hi? 
          I'm always excited to connect with people who love building meaningful things. 
          Drop a message, and I'll get back to you as soon as I can!
        </p>
      </div>

      <div class="form-container">
        <form
          :action="formAction"
          method="POST"
          class="contact-form"
          @submit="handleSubmit"
        >
          <div class="form-group">
            <label for="name">Name</label>
            <input type="text" id="name" name="name" required placeholder="Your Name" />
          </div>

          <div class="form-group">
            <label for="email">Email</label>
            <input type="email" id="email" name="email" required placeholder="your.email@example.com" />
          </div>

          <div class="form-group">
            <label for="message">Message</label>
            <textarea id="message" name="message" rows="5" required placeholder="Hello! I'd like to discuss..."></textarea>
          </div>

          <button type="submit" class="submit-btn" :disabled="isSubmitting">
            <span v-if="!isSubmitting">Send Message</span>
            <span v-else>Sending...</span>
          </button>
        </form>
      </div>
    </div>
  </section>
</template>

<script setup>
import { ref, computed, reactive } from 'vue'

const isSubmitting = ref(false)
const formspreeKey = import.meta.env.VITE_FORMSPREE_KEY

const notification = reactive({
  show: false,
  message: '',
  type: 'success' // 'success' or 'error'
})

const formAction = computed(() => {
  return formspreeKey ? `https://formspree.io/f/${formspreeKey}` : '#'
})

const showNotification = (message, type = 'success') => {
  notification.message = message
  notification.type = type
  notification.show = true
  
  setTimeout(() => {
    closeNotification()
  }, 3000)
}

const closeNotification = () => {
  notification.show = false
}

const handleSubmit = async (e) => {
  e.preventDefault()

  if (!formspreeKey) {
    showNotification('Configuration missing. Restart dev server.', 'error')
    return
  }

  isSubmitting.value = true
  const formData = new FormData(e.target)

  try {
    const response = await fetch(formAction.value, {
      method: 'POST',
      body: formData,
      headers: {
        'Accept': 'application/json'
      }
    })

    if (response.ok) {
      showNotification("Thanks! I'll be in touch soon.", 'success')
      e.target.reset()
    } else {
      const data = await response.json().catch(() => ({}))
      if (data.errors) {
        showNotification(data.errors.map(err => err.message).join(', '), 'error')
      } else {
        showNotification("Problem submitting form.", 'error')
      }
    }
  } catch (error) {
    showNotification("Network error. Please try again.", 'error')
  } finally {
    isSubmitting.value = false
  }
}
</script>

<style scoped>
.contact-section {
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

.contact-content {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 4rem;
  align-items: start;
}

.contact-text p {
  font-size: var(--text-lg);
  color: var(--color-gray-400);
  line-height: 1.6;
}

.form-container {
  background: var(--color-gray-800);
  padding: 2rem;
  border-radius: 16px;
  border: 1px solid var(--border-color);
  box-shadow: var(--elevation-2);
}

.contact-form {
  display: flex;
  flex-direction: column;
  gap: 1.5rem;
}

.form-group {
  display: flex;
  flex-direction: column;
  gap: 0.5rem;
}

label {
  font-size: var(--text-sm);
  color: var(--color-gray-300);
  font-weight: var(--fw-bold);
  text-transform: uppercase;
}

input, textarea {
  background: var(--color-gray-900);
  border: 1px solid var(--color-gray-700);
  border-radius: 8px;
  padding: 0.8rem;
  color: var(--color-default-white);
  font-family: var(--font-body);
  transition: all 0.2s;
  
  &:focus {
    outline: none;
    border-color: var(--color-accent);
    box-shadow: 0 0 0 2px rgba(26, 188, 209, 0.2);
  }
}

.submit-btn {
  background: var(--color-accent);
  color: var(--color-default-black);
  border: none;
  padding: 1rem;
  border-radius: 8px;
  font-weight: var(--fw-bold);
  cursor: pointer;
  transition: transform 0.2s, opacity 0.2s;
  text-transform: uppercase;
  letter-spacing: 1px;
}

.submit-btn:hover {
  transform: translateY(-2px);
  opacity: 0.9;
}

.submit-btn:disabled {
  opacity: 0.5;
  cursor: not-allowed;
  transform: none;
}

/* Light Theme */
body[data-theme='light'] {
  & .header-group h3 { color: var(--text-color-default); }
  & .connector-line { background: linear-gradient(90deg, var(--color-gray-300), transparent); }
  
  & .contact-text p { color: var(--color-gray-600); }
  
  & .form-container {
    background: var(--color-default-white);
    border-color: var(--color-gray-200);
  }
  
  & label { color: var(--color-gray-600); }
  
  & input, & textarea {
    background: var(--color-gray-100);
    border-color: var(--color-gray-300);
    color: var(--color-gray-900);
  }
  
  & input:focus, & textarea:focus {
    background: var(--color-default-white);
  }
}

/* Responsive */
@media (--vw-md) {
  .contact-content {
    grid-template-columns: 1fr;
    gap: 2rem;
  }
}

/* Notification Styles */
.notification-popup {
  position: fixed;
  top: 80px; /* Below navbar */
  right: 20px;
  background: var(--color-gray-800);
  color: var(--color-default-white);
  padding: 1rem 1.5rem;
  border-radius: 8px;
  box-shadow: var(--elevation-3);
  z-index: 1000;
  display: flex;
  align-items: center;
  gap: 1rem;
  border-left: 4px solid var(--color-accent);
  max-width: 300px;
}

.notification-popup.error {
  border-left-color: #ef4444;
}

.close-btn {
  background: transparent;
  border: none;
  font-size: 1.25rem;
  color: var(--color-gray-400);
  cursor: pointer;
  padding: 0;
  line-height: 1;
}

.close-btn:hover {
  color: var(--color-default-white);
}

/* Transition */
.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.3s ease, transform 0.3s ease;
}

.fade-enter-from,
.fade-leave-to {
  opacity: 0;
  transform: translateY(-10px);
}

/* Light Theme Override */
body[data-theme='light'] .notification-popup {
  background: var(--color-default-white);
  color: var(--color-gray-900);
  border: 1px solid var(--color-gray-200);
  border-left: 4px solid var(--color-accent);
}

body[data-theme='light'] .notification-popup.error {
  border-left-color: #ef4444;
}
</style>
