1. 🎯 OBJECTIVE
Build a lightweight interactive web app embedded on the My Little France website that helps French Working Holiday Visa holders generate a personalized post-arrival checklist based on their current situation.

The assistant acts like a mini onboarding coach that:

Asks a few simple questions

Outputs a tailored step-by-step checklist

Links each step to a service/product My Little France offers

Optionally collects email to send the checklist & upsell

2. 👥 TARGET USERS
Primary audience:

French citizens aged 18–30

On a Working Holiday Visa (WHV) or planning to arrive in Australia soon

Limited understanding of Australian admin systems

Seeking clear guidance & practical services (postal address, TFN, bank, job, SIM)

3. 🧩 KEY FEATURES
Feature	Description
Dynamic Questionnaire	5–6 quick questions to assess their situation
Personalized Checklist Generator	Creates a custom to-do list with CTA buttons
Service Integration	Each checklist item links to a product/service (e.g. Job Club, Postal Address, TFN help)
Optional Email Capture	Let users email themselves their checklist (for marketing follow-up)
Multi-device Responsive UI	Mobile-first friendly

4. 🧪 QUESTIONNAIRE FLOW (FR/EN)
Question	Type	Logic
As-tu déjà atterri en Australie ? (Have you arrived?)	Yes/No	Triggers different list items
As-tu un TFN ? (Do you already have a TFN?)	Yes/No	If No → include TFN step
As-tu déjà ouvert un compte bancaire ? (Bank account?)	Yes/No	If No → show bank setup
As-tu besoin d’une adresse postale ? (Postal address?)	Yes/No	If Yes → link to Postal service
Tu cherches un job ? (Looking for work?)	Yes/No	If Yes → link to Job Club / CV services
Tu veux une carte SIM australienne ? (Need a SIM?)	Yes/No	If Yes → link to SIM page or partner

5. 📋 OUTPUT EXAMPLE (CHECKLIST)
markdown
Copy
Edit
🎯 Ton plan d'action personnalisé

✅ Crée ton compte bancaire → [Ouvrir maintenant]
✅ Obtiens ton TFN → [Accède à notre service]
✅ Commande une adresse postale → [Adresse 30% off]
✅ Rédige ton CV australien → [Voir nos options]
✅ Rejoins notre Job Club → [Découvrir]
✅ Obtiens une carte SIM → [Voir nos bons plans]

📩 Tu veux recevoir ce plan par mail ? [Entrer ton adresse mail]
6. 🧠 AI CODING TASKS
Here’s what you ask Codex or another AI dev to build step-by-step:

a. Basic App Structure
plaintext
Copy
Edit
- One HTML/CSS/JS file (or React if preferred)
- Embedded via iframe or section on Shopify (My Little France)
- Questionnaire with conditional rendering
- Checklist result generation
b. Data Model
js
Copy
Edit
const steps = [
  { id: 'tfn', title: 'Obtiens ton TFN', cta: 'Accède à notre service', link: '/tfn', condition: (answers) => answers.tfn === false },
  { id: 'bank', title: 'Ouvre un compte bancaire', cta: 'Ouvrir maintenant', link: '/bank', condition: (answers) => answers.bank === false },
  { id: 'postal', title: 'Commande une adresse postale', cta: 'Adresse 30% off', link: '/adresse-postale', condition: (answers) => answers.postal === true },
  { id: 'cv', title: 'Rédige ton CV australien', cta: 'Voir nos options', link: '/cv', condition: (answers) => answers.job === true },
  { id: 'jobclub', title: 'Rejoins notre Job Club', cta: 'Découvrir', link: '/job-club', condition: (answers) => answers.job === true },
  { id: 'sim', title: 'Obtiens une carte SIM', cta: 'Voir nos bons plans', link: '/sim', condition: (answers) => answers.sim === true },
];
c. Logic to Display Checklist
Loop through steps, filter those with condition(answers) === true, and render.

d. Add Email Input (optional)
js
Copy
Edit
<input type="email" placeholder="Ton adresse mail" />
<button onclick="sendChecklist()">Recevoir par mail</button>
Use EmailJS or similar free email client-side API.

7. 🔌 INTEGRATION TO WEBSITE
On Shopify:

Host the app as a public HTML file on your domain (e.g., checklist.mylittlefrance.com)

Embed it using a Shopify section or <iframe> in a page

Optionally integrate with analytics (Hotjar, Meta Pixel)

8. 🖼️ VISUAL DESIGN GUIDELINES
Follow MLF color palette: white background, blue/red accents, clean layout

Fun but professional font (same as existing branding)

Emojis for clarity ✅ 🇦🇺 📩

Button style: rounded corners, soft hover effects

9. 🚀 FUTURE FEATURES (PHASE 2+)
Save progress with cookies

Multilingual toggle (French ↔ English)

Admin dashboard to analyze answers for marketing insights

CRM integration (e.g., Klaviyo for email flows)


## Usage
Open index.html in a browser to try the onboarding form and generate a custom checklist.
