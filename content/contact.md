---
title: "Contact"
date: 2026-01-12
draft: false
description: "Send me a message"
type: "contact"
layout: "contact"
---

<div class="text-center mb-12">
  <h1 class="text-6xl md:text-7xl font-bold text-gray-800 mb-6 font-poppins">Contact</h1>
</div>

<form action="https://formspree.io/f/mreeglld" method="POST" style="max-width:640px;margin:2rem auto;display:flex;flex-direction:column;gap:1rem;font-family:-apple-system,BlinkMacSystemFont,'Segoe UI',sans-serif;">
<p style="margin:0 0 1rem 0;color:#4b5563;">Drop me a line and it will reach my inbox (george.trevnenski@gmail.com).</p>

  <label for="name" style="font-weight:600;color:#374151;">Name</label>
  <input id="name" name="name" type="text" required placeholder="Your name" style="padding:0.65rem;border:1px solid #d1d5db;border-radius:8px;font-size:1rem;">

  <label for="email" style="font-weight:600;color:#374151;">Email</label>
  <input id="email" name="_replyto" type="email" required placeholder="you@example.com" style="padding:0.65rem;border:1px solid #d1d5db;border-radius:8px;font-size:1rem;">

  <label for="message" style="font-weight:600;color:#374151;">Message</label>
  <textarea id="message" name="message" rows="4" required placeholder="Let me know what you’re reaching out about." style="padding:0.65rem;border:1px solid #d1d5db;border-radius:8px;font-size:1rem;"></textarea>

  <button type="submit" style="padding:0.75rem 1.4rem;background:#2563eb;color:#fff;border:none;border-radius:8px;font-weight:700;cursor:pointer;">Send message</button>
</form>
