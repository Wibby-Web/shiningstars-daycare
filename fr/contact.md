---
layout: layouts/contact.njk
title: Nous joindre
metaDescription: Contactez le Centre de la petite enfance ShiningStars pour planifier une visite ou poser vos questions. Au plaisir de vous entendre !
section: contact
date: 2024-01-01
permalink: /fr/contact/index.html
eleventyNavigation:
  key: Contact
  order: 4
---
<div class="contact-hero">
  <h1>Nous joindre</h1>
  <p>Nous serions ravis de vous faire visiter nos installations et de vous présenter notre formidable équipe !</p>
</div>

<div class="contact-grid">

<div>
<h3>Envoyez-nous un message</h3>
<form name="contact" method="POST" data-netlify="true">
  <label for="name">Nom</label>
  <input type="text" name="name" id="name" autocomplete="name" placeholder="Votre nom" title="Veuillez entrer votre nom" required>
  <label for="email">Courriel</label>
  <input type="email" name="email" id="email" autocomplete="email" placeholder="Votre adresse courriel" title="La partie du domaine de l'adresse courriel (après le @) est invalide." pattern="^([^\x00-\x20\x22\x28\x29\x2c\x2e\x3a-\x3c\x3e\x40\x5b-\x5d\x7f-\xff]+|\x22([^\x0d\x22\x5c\x80-\xff]|\x5c[\x00-\x7f])*\x22)(\x2e([^\x00-\x20\x22\x28\x29\x2c\x2e\x3a-\x3c\x3e\x40\x5b-\x5d\x7f-\xff]+|\x22([^\x0d\x22\x5c\x80-\xff]|\x5c[\x00-\x7f])*\x22))*\x40([^\x00-\x20\x22\x28\x29\x2c\x2e\x3a-\x3c\x3e\x40\x5b-\x5d\x7f-\xff]+|\x5b([^\x0d\x5b-\x5d\x80-\xff]|\x5c[\x00-\x7f])*\x5d)(\x2e([^\x00-\x20\x22\x28\x29\x2c\x2e\x3a-\x3c\x3e\x40\x5b-\x5d\x7f-\xff]+|\x5b([^\x0d\x5b-\x5d\x80-\xff]|\x5c[\x00-\x7f])*\x5d))*(\.\w{2,})+$" required>
  <label for="message">Message</label>
  <textarea name="message" id="message" placeholder="Écrivez votre message ici" rows="7" required></textarea>
  <button type="submit">Envoyer</button>
</form>
</div>

<div class="card" style="margin-bottom: 2rem;">
  <h3>Coordonnées</h3>
<div class="feature-list">
      <div class="feature-item">
        <div class="feature-icon"><i data-lucide="map-pin"></i></div>
        <div class="feature-text">
          <h4>Adresse</h4>
          <p>123, boul. Sunshine, Montréal (Québec) H2Y 1A1, Canada</p>
        </div>
      </div>
      <div class="feature-item">
        <div class="feature-icon"><i data-lucide="phone"></i></div>
        <div class="feature-text">
          <h4>Téléphone</h4>
          <p>(514) 123-4567</p>
        </div>
      </div>
<div class="feature-item">
        <div class="feature-icon"><i data-lucide="mail"></i></div>
        <div class="feature-text">
          <h4>Courriel</h4>
          <p><a href="mailto:hello@shiningstars-example.com">hello@shiningstars-example.com</a></p>
        </div>
      </div>
    </div>
<div class="bg_card">
<div class="card_title">
<div class="card_icon"><i data-lucide="clock"></i></div>
<h3>Heures d'ouverture</h3>
</div>
<ul class="hours">
<li><span>Du lundi au vendredi</span><strong>De 6 h 30 à 18 h</strong></li>
<li><span>Samedi et dimanche</span><strong>Fermé</strong></li>
</ul>
</div>
</div>
</div>
