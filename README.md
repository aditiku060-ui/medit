# Medit

**Every case is new. Learn from every case.**

Medit is a medical knowledge-sharing and surgical learning prototype created by **Team Herhavoc** for the IGNITE 2026 No-Code Startup Hackathon. It combines anonymized case discussions with a contextual study workspace so a reader can review a case and make personal revision notes without leaving the article.

## Run locally

1. Extract the repository ZIP.
2. Open `index.html` in a modern browser. No build step or package installation is required.
3. Select **Demo login** to explore the prototype.

The project intentionally uses vanilla HTML, CSS and JavaScript to keep the prototype portable.

## Main pages and user journeys

- **Home / Dashboard:** Community case feed, specialty shortcuts and tags.
- **Explore Cases:** Search and filter cases by specialty, condition, procedure and tags.
- **Case reading view:** Structured case summary, clinical challenge, management description, learning points, references status, related cases and professional discussion.
- **Study Workspace:** Contextual key takeaways, review checkboxes, clinical reflection prompts, quick revision sections, resource placeholders and private notes.
- **Study Materials:** Search and filter saved cases, recently viewed cases, cases with notes and cases with bookmarked learning points.
- **Share a Case:** Structured case submission with an anonymization checklist.
- **Saved Cases, Notifications, Profile and Settings:** Existing prototype features remain available.
- **Guidelines and Privacy:** Community expectations and prototype limitations.

## Study Workspace data model

Study progress is kept separate from the base case content in the `D.study` object:

```js
study: {
  notes: {},       // case-specific private note text, keyed by `case-<id>`
  reviewed: {},    // reviewed state keyed by case and takeaway index
  bookmarks: [],   // bookmarked takeaway keys, `<case-id>-<index>`
  recent: []       // recently opened case IDs, newest first
}
```

Cases use the existing seed and user-submitted case records. The Study Workspace derives its initial takeaways from each case's submitted learning points rather than generating new clinical claims. Resource entries without verified sources are explicitly marked as demonstration placeholders. Personal notes, bookmarks, review state and recent reading state are persisted in browser `localStorage` alongside existing demo data. Notes can be exported as a plain-text file from the case page.

## Interaction and accessibility notes

- The article table of contents links to sections in the same page.
- The Study Workspace can be collapsed and reopened.
- Takeaways can be marked reviewed and bookmarked.
- Notes can be saved, reopened, edited and exported.
- Study Materials supports keyword search, category filters and sorting.
- Responsive layouts stack the study panel above the article on narrower screens.
- Keyboard focus styles, labels and semantic section landmarks are included.
- Light/dark appearance follows the existing theme setting and system preference.

## Medical accuracy and privacy

- All included users and cases are fictional demonstration content.
- Verification badges are simulated and do not verify real credentials.
- No medical reference is claimed to be verified unless a real source is explicitly provided. Generic resource placeholders are labelled as unverified.
- The prototype is for education and discussion only; it does not replace clinical judgment, current guidelines, institutional protocols or specialist consultation.
- Never enter patient-identifiable information. The browser-side checklist is a reminder, not a guarantee of anonymization.

## Storage and security limitations

This is a front-end prototype, not a production medical application. Data is stored in the current browser's `localStorage`, is not encrypted by the app and is not synced across devices. The demo login and credential-verification flow are simulated. A production deployment would need secure server-side authentication and authorization, protected storage, appropriate consent and privacy controls, audit logging, moderation workflows, clinical content review, backups, and legal/regulatory review appropriate to its deployment region.

## Known limitations / next steps

- No backend, multi-device sync or real user authentication.
- Study resources are demonstration placeholders unless a source is explicitly supplied.
- Reading progress is represented through recently viewed cases and reviewed takeaways; continuous scroll-position restoration is not implemented.
- Study Materials currently indexes saved/recent/noted/bookmarked cases rather than a remote catalogue of external publications.
- Production readiness would require testing with clinicians, verified citations, a formal content-review workflow and a security/privacy assessment.

## Medit Guide chatbot and professional connections

The prototype now includes two additional experiences:

- **Medit Guide:** A floating, conversational help widget with quick prompts for navigating the site, finding study tools, sharing anonymized cases and opening the Connect directory. It uses a small local rule-based response set; it is not connected to an AI model and must not be treated as clinical decision support.
- **Connect:** A searchable directory demo for doctors and hospitals, with filters for profile type and specialty, local connection-request states, and saved profiles.

All people and hospital entries in Connect are fictional demo records. Connection requests do not send emails, messages or notifications to real people, and the directory does not represent real clinical services, referrals or vacancies. Chat messages, saved profiles and connection requests are stored in browser `localStorage`; they are not encrypted, synced or suitable for confidential professional or patient information.

### Production integration still required

To turn these demos into real services, Medit would need a secure backend, authenticated accounts, server-side authorization, clinician and institutional verification, request/accept/decline workflows, secure messaging, abuse reporting and moderation, rate limiting, audit trails, consent and privacy controls. A real chatbot would require a selected provider/API, server-side secret management, a reviewed knowledge source and explicit safeguards against diagnosis or treatment advice. Never put API keys in front-end JavaScript. Obtain appropriate legal, clinical, and privacy review before launch.
