<template>
  <section id="contact" class="contact">
    <div class="container">
      <h2 class="section-title reveal-up" ref="titleRef" :class="{ visible: titleVisible }">Get In Touch</h2>
      <p class="contact-intro reveal-up" ref="introRef" :class="{ visible: introVisible }">
        Interested in working together or have a question? Feel free to reach out!
      </p>
      <div class="contact-layout">
        <form class="contact-form reveal-left" ref="formRef" :class="{ visible: formVisible }" @submit.prevent="handleSubmit" novalidate>
          <div class="form-group" :class="{ error: errors.name }">
            <label for="name">Name</label>
            <input
              id="name"
              v-model="form.name"
              type="text"
              placeholder="Your name"
              @blur="validateField('name')"
            />
            <span v-if="errors.name" class="error-msg">{{ errors.name }}</span>
          </div>
          <div class="form-group" :class="{ error: errors.email }">
            <label for="email">Email</label>
            <input
              id="email"
              v-model="form.email"
              type="email"
              placeholder="your.email@example.com"
              @blur="validateField('email')"
            />
            <span v-if="errors.email" class="error-msg">{{ errors.email }}</span>
          </div>
          <div class="form-group" :class="{ error: errors.subject }">
            <label for="subject">Subject</label>
            <input
              id="subject"
              v-model="form.subject"
              type="text"
              placeholder="What's this about?"
              @blur="validateField('subject')"
            />
            <span v-if="errors.subject" class="error-msg">{{ errors.subject }}</span>
          </div>
          <div class="form-group" :class="{ error: errors.message }">
            <label for="message">Message</label>
            <textarea
              id="message"
              v-model="form.message"
              rows="5"
              placeholder="Your message..."
              @blur="validateField('message')"
            ></textarea>
            <span v-if="errors.message" class="error-msg">{{ errors.message }}</span>
          </div>
          <button type="submit" class="btn-submit" :disabled="submitted">
            {{ submitted ? '✓ Message Sent!' : 'Send Message' }}
          </button>
        </form>
        <div class="contact-info stagger-children" ref="infoRef" :class="{ visible: infoVisible }">
          <div class="info-card">
            <div class="info-icon">
              <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><rect x="2" y="4" width="20" height="16" rx="2"/><path d="m22 7-8.97 5.7a1.94 1.94 0 0 1-2.06 0L2 7"/></svg>
            </div>
            <div>
              <h4>Email</h4>
              <a href="mailto:nguyennhutrong69@gmail.com">nguyennhutrong69@gmail.com</a>
            </div>
          </div>
          <div class="info-card">
            <div class="info-icon">
              <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M22 16.92v3a2 2 0 0 1-2.18 2 19.79 19.79 0 0 1-8.63-3.07 19.5 19.5 0 0 1-6-6 19.79 19.79 0 0 1-3.07-8.67A2 2 0 0 1 4.11 2h3a2 2 0 0 1 2 1.72 12.84 12.84 0 0 0 .7 2.81 2 2 0 0 1-.45 2.11L8.09 9.91a16 16 0 0 0 6 6l1.27-1.27a2 2 0 0 1 2.11-.45 12.84 12.84 0 0 0 2.81.7A2 2 0 0 1 22 16.92z"/></svg>
            </div>
            <div>
              <h4>Phone</h4>
              <a href="tel:0948847448">0948 847 448</a>
            </div>
          </div>
          <div class="info-card">
            <div class="info-icon">
              <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M20 10c0 6-8 12-8 12s-8-6-8-12a8 8 0 0 1 16 0Z"/><circle cx="12" cy="10" r="3"/></svg>
            </div>
            <div>
              <h4>Location</h4>
              <p>Ho Chi Minh City, Vietnam</p>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import { reactive, ref } from 'vue'
import { useScrollReveal } from '../composables/useScrollReveal'

const { elementRef: titleRef, isVisible: titleVisible } = useScrollReveal()
const { elementRef: introRef, isVisible: introVisible } = useScrollReveal()
const { elementRef: formRef, isVisible: formVisible } = useScrollReveal({ threshold: 0.2 })
const { elementRef: infoRef, isVisible: infoVisible } = useScrollReveal({ threshold: 0.2 })

const form = reactive({ name: '', email: '', subject: '', message: '' })
const errors = reactive({ name: '', email: '', subject: '', message: '' })
const submitted = ref(false)

const emailRegex = /^[^\s@]+@[^\s@]+\.[^\s@]+$/

function validateField(field) {
  errors[field] = ''
  if (field === 'name' && !form.name.trim()) errors.name = 'Please enter your name'
  if (field === 'email') {
    if (!form.email.trim()) errors.email = 'Please enter your email'
    else if (!emailRegex.test(form.email)) errors.email = 'Please enter a valid email'
  }
  if (field === 'subject' && !form.subject.trim()) errors.subject = 'Please enter a subject'
  if (field === 'message' && !form.message.trim()) errors.message = 'Please enter a message'
}

function handleSubmit() {
  ;['name', 'email', 'subject', 'message'].forEach(validateField)
  if (Object.values(errors).some(e => e)) return

  // In production, this would send to a backend API
  submitted.value = true
  setTimeout(() => {
    submitted.value = false
    Object.keys(form).forEach(k => form[k] = '')
  }, 3000)
}
</script>

<style scoped>
.reveal-up {
  opacity: 0;
  transform: translateY(30px);
  transition: opacity 0.7s ease, transform 0.7s ease;
}
.reveal-up.visible {
  opacity: 1;
  transform: none;
}
.reveal-left {
  opacity: 0;
  transform: translateX(-30px);
  transition: opacity 0.7s ease 0.2s, transform 0.7s ease 0.2s;
}
.reveal-left.visible {
  opacity: 1;
  transform: none;
}
.contact {
  padding: 6rem 2rem;
}
.container {
  max-width: 1000px;
  margin: 0 auto;
}
.section-title {
  text-align: center;
  font-size: 2.2rem;
  font-weight: 700;
  color: #fff;
  margin-bottom: 1rem;
}
.section-title::after {
  content: '';
  display: block;
  width: 60px;
  height: 4px;
  background: linear-gradient(135deg, #6366f1, #8b5cf6);
  margin: 0.8rem auto 0;
  border-radius: 2px;
}
.contact-intro {
  text-align: center;
  color: #94a3b8;
  font-size: 1.05rem;
  margin-bottom: 3rem;
}
.contact-layout {
  display: grid;
  grid-template-columns: 1.2fr 0.8fr;
  gap: 3rem;
  align-items: start;
}
.contact-form {
  display: flex;
  flex-direction: column;
  gap: 1.2rem;
}
.form-group {
  display: flex;
  flex-direction: column;
  gap: 0.4rem;
}
.form-group label {
  color: #cbd5e1;
  font-size: 0.9rem;
  font-weight: 500;
}
.form-group input,
.form-group textarea {
  background: rgba(255, 255, 255, 0.04);
  border: 1px solid rgba(255, 255, 255, 0.1);
  border-radius: 8px;
  padding: 0.8rem 1rem;
  color: #e2e8f0;
  font-size: 0.95rem;
  font-family: inherit;
  transition: all 0.3s;
  outline: none;
}
.form-group input::placeholder,
.form-group textarea::placeholder {
  color: #475569;
}
.form-group input:focus,
.form-group textarea:focus {
  border-color: #6366f1;
  background: rgba(99, 102, 241, 0.05);
  box-shadow: 0 0 0 3px rgba(99, 102, 241, 0.1);
}
.form-group.error input,
.form-group.error textarea {
  border-color: #ef4444;
}
.error-msg {
  color: #ef4444;
  font-size: 0.8rem;
}
.btn-submit {
  padding: 0.9rem 2rem;
  background: linear-gradient(135deg, #6366f1, #8b5cf6);
  color: #fff;
  border: none;
  border-radius: 8px;
  font-size: 1rem;
  font-weight: 600;
  cursor: pointer;
  transition: all 0.3s;
  font-family: inherit;
}
.btn-submit:hover:not(:disabled) {
  transform: translateY(-2px);
  box-shadow: 0 8px 25px rgba(99, 102, 241, 0.4);
}
.btn-submit:disabled {
  background: linear-gradient(135deg, #22c55e, #16a34a);
  cursor: default;
}
.contact-info {
  display: flex;
  flex-direction: column;
  gap: 1.2rem;
}
.info-card {
  display: flex;
  align-items: center;
  gap: 1rem;
  background: rgba(255, 255, 255, 0.03);
  border: 1px solid rgba(255, 255, 255, 0.06);
  border-radius: 12px;
  padding: 1.2rem 1.5rem;
  transition: all 0.3s;
}
.info-card:hover {
  border-color: rgba(99, 102, 241, 0.2);
  background: rgba(99, 102, 241, 0.03);
}
.info-icon {
  width: 44px;
  height: 44px;
  display: flex;
  align-items: center;
  justify-content: center;
  background: rgba(99, 102, 241, 0.15);
  border-radius: 10px;
  color: #a78bfa;
  flex-shrink: 0;
}
.info-icon svg { width: 22px; height: 22px; }
.info-card h4 {
  color: #e2e8f0;
  font-size: 0.9rem;
  font-weight: 600;
  margin-bottom: 0.2rem;
}
.info-card a,
.info-card p {
  color: #94a3b8;
  text-decoration: none;
  font-size: 0.9rem;
  margin: 0;
}
.info-card a:hover { color: #a78bfa; }

@media (max-width: 768px) {
  .contact-layout {
    grid-template-columns: 1fr;
  }
}
</style>
