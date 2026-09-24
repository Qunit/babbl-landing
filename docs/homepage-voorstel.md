# Babbl homepage — analysis & proposal (pre-implementation)

Status: homepage implemented 2026-09-24 (index.html). Subpages not yet updated. Covers steps 1–9 of the brief.

> ⚠️ Correction (2026-09-24): the local repo is **behind the live site** (babbl.family, Netlify). Live differs in: Netlify Forms waitlist (POST + honeypot + optional message + consent checkbox — sign-ups *are* captured), `hallo@babbl.family`, pretty URLs (`/hoe-het-werkt`), stats ("75-plussers woont zelfstandig thuis", "5,5 mln"), medication use case rewritten to "Wat staat er op dit doosje?", and voor-organisaties has a dorpsauto/vervoer card + "Van hulpvraag naar hulp" section. Proposal below still applies; findings about the form and email are superseded. Implementation must start from the live version.

---

## 1. Analysis of current homepage (`index.html`)

Tech: static HTML + one `style.css`, no build step. Warm identity (cream `#F2EDE3`, terracotta `#C4624A`, Playfair Display + Inter, large radii, soft shadows). This identity fits the new brief — **keep it**.

| # | Current section | Verdict | Why |
|---|---|---|---|
| — | Nav (6 links + "Kom op de wachtlijst") | **Rewrite** | Audience-split links ("Voor ouderen / Voor familie") frame two products. CTA "wachtlijst" implies a launch queue; next phase is testing. |
| 1 | Hero "Langer zelfstandig thuis. Minder zorgen voor familie." | **Rewrite copy, keep layout** | Family is co-protagonist. Image `01-hero.png` shows the old rectangular device render. |
| 2 | Stats bar (live: 1 op 4 / 75-plussers / 5,5 mln mantelzorgers) | **Remove** | Unsourced numbers, mantelzorg framing, investor-deck feel. |
| 3 | Problem cards ("vergeten", "mantelzorg geeft zorgen") | **Remove** | Deficit framing ("ouderen kunnen niet…"). |
| 4 | Solution pillars ("Geen schermen of apps") | **Reuse component** for §5 "Wat Babbl nog meer kan" | Claim "geen apps" conflicts with the app now being part of Babbl. |
| 5 | Use cases (medicatie, afspraak, welzijn, brief, oplichting) | **Replace** with scenario component; reuse the chat-bubble visual language | Every case ends in a *family notification* ("Uw moeder heeft haar medicatie niet ingenomen") = monitoring, family as protagonist. Medicatie/welzijn imply medical capability. ~190 inline `style=""` attributes → move to classes. |
| 6 | "Open platform" + chip wall (apotheek, verzekering…) | **Rewrite** as "De wereld rondom Babbl" | "Platform" word, logo-wall feel, implies integrations that don't exist. |
| 7 | "Alles over Babbl" 6 detail cards | **Shrink** to a compact link row near the footer | Keeps subpages reachable without competing with the story. |
| 8 | "Ontworpen voor mensen" checklist | **Remove**, merge useful bits into Privacy | Contains "geen apps" and "lokale verwerking" claims — needs verification (see open questions). |
| 9 | Waitlist form | **Reuse form** (live Netlify version), reframe as "Samen ontdekken wat echt werkt" | Live: Netlify Forms, consent checkbox, optional message. Add "Ik ben…" select as extra field. |
| 10 | FAQ | **Keep component**, update answers | "Is Babbl alleen voor ouderen?" answer and privacy answer need new framing. |
| — | Footer | **Update** | © 2025, mission line. |

### Imagery finding (updated after pulling origin/main)

All 18 assets are AI renders (prompts in `assets/image-prompts.md`). Commit `11efbec` replaced the old rectangular box with a **round, low, fabric-wrapped puck**: warm-white light ring on the top edge, one button on top, fabrics in oatmeal / sand / sage / terracotta / grey-blue. That is much closer to the prototype DNA (rounded, fabric, top control, light ring).

Open point: the brief calls the prototype *rounded/cylindrical*; the renders are a *low domed disc*. Once the real photo is in, check proportions. If they match → reuse `12` (macro) and the coloured device shots (e.g. `01` terracotta, `03` sage) for §6 "Ontworpen om thuis te horen". If the prototype is taller → the renders show a different product and must not appear on the same page as the photo; regenerate from the photo as image reference.

Hero: `00`/`01-hero` (woman with coffee, device small in frame) works if proportions match; otherwise `07` (couple with coffee, no device).

---

## 2–4. Revised structure and content mapping

| # | New section | Source / reuse |
|---|---|---|
| 1 | **Hero** — Langer zelfstandig. Met Babbl dichtbij. | Hero layout + `.hero-benefit` ticks. Image: crop of `06` (man talking) — no device. |
| 2 | **Zelf. Samen. Met wat hulp.** — philosophy intro | New, short. Uses `.section-head`. |
| 3 | **Scenario component** (Brief · Afspraak · Vervoer · Boodschappen) | New component; chat bubbles restyled from old use-case cards. |
| 4 | **Babbl staat inmiddels op tafel** — real photo + progress | New. Status track reuses `.step-number` styling. |
| 5 | **Wat Babbl nog meer kan** — short, no duplication | `.solution-pillar` component. |
| 6 | **Ontworpen om thuis te horen** — production direction + colourways | New. |
| 7 | **Uw vertrouwde kring** | `.content-2col` + image `16`. |
| 8 | **De wereld rondom Babbl** | Replaces platform section; reuses `.platform-visual` card. |
| 9 | **Privacy & vertrouwen** | `.principle` cards (from privacy page), 4 items + link. |
| 10 | **Samen ontdekken wat echt werkt** — next phase, 3 audiences | Reuses `.org-feature` cards + waitlist form. |
| 11 | **Hoe Babbl begon** — founder story | `.content-2col`. |
| 12 | **Final CTA** + compact FAQ + "Meer weten" link row | `.cta-section`, FAQ, footer. |

Nav: `Wat Babbl doet · Het prototype · Privacy · Meedoen · Over ons` + CTA **Volg onze ontwikkeling**. Subpages stay reachable from footer + link row (they get the same nav; their copy is a follow-up task, not part of this change).

---

## 5. Proposed Dutch copy

### 1 · Hero
- Tag: *In ontwikkeling — de eerste Babbls staan op tafel* (small, honest; not "startup")
- **H1:** Langer zelfstandig.<br>Met Babbl dichtbij.
- Sub: Babbl is een vertrouwde assistent die helpt met de dingen van alledag. Een brief begrijpen, een afspraak onthouden of iets regelen. Gewoon door erover te praten.
- Ticks: Gewoon praten · Zelf de regie houden · Hulp dichtbij als dat nodig is
- CTAs: **Ontdek wat Babbl doet** (→ #zelf-samen) · Volg onze ontwikkeling (→ #meedoen)

### 2 · Zelf. Samen. Met wat hulp.
- Tag: *Hoe Babbl helpt*
- **H2:** Zelf. Samen. Met wat hulp.
- Zelfstandig blijven betekent niet dat u alles alleen hoeft te doen. Soms regelt u iets gewoon zelf. Soms doet u het liever samen met iemand die u vertrouwt. En soms is wat extra hulp prettig. Babbl sluit aan bij wat u op dat moment nodig heeft — terwijl u zelf de regie houdt.
- Lead-in to component: *Zo werkt dat bij vier gewone situaties.*

### 3 · Scenarios

Each level: user quote (spoken), Babbl's reply (short), one-line explanation.

**Een brief op de mat** — Een brief van de gemeente, het ziekenhuis of een andere organisatie. Wat staat er precies? En moet u er iets mee?
- **Zelf** — "Babbl, kun je uitleggen wat er in deze brief staat?" → *"Natuurlijk. Houd de brief even voor de camera van uw telefoon. … Het is een brief van de gemeente over uw afvalpas. U hoeft niets te doen; de nieuwe pas komt vanzelf."* — Babbl leest mee en legt in gewone taal uit wat er staat, wat belangrijk is en of u iets moet doen.
- **Samen** — "Wil je deze brief ook even met mijn dochter delen?" → *"Ik stuur de brief en mijn uitleg naar Anne. Alleen deze brief, niets anders."* — U bepaalt zelf of en met wie u iets deelt. Zo kunt u er samen naar kijken.
- **Met wat hulp** — "Ik moet hier iets voor regelen. Kun je me helpen?" → *"Er staat dat u vóór 15 oktober moet bellen. Zal ik het nummer opzoeken en u maandagochtend herinneren?"* — Babbl helpt de volgende stap te zetten: iets onthouden, een afspraak in de agenda, het juiste telefoonnummer. En waar nodig iemand die kan helpen.

**Een afspraak** — Een afspraak maken is één ding. Weten wanneer u waar moet zijn en eraan denken is minstens zo belangrijk.
- **Zelf** — "Wanneer moet ik ook alweer naar de tandarts?" → *"Dinsdag om half elf, bij tandarts De Vries. Zal ik u maandagavond en dinsdagochtend even herinneren?"* — Babbl kijkt in uw agenda en helpt u eraan denken.
- **Samen** — "Wil je Peter laten weten hoe laat mijn afspraak is?" → *"Ik laat Peter weten dat u dinsdag om half elf bij de tandarts bent."* — U deelt een afspraak met wie u wilt, wanneer u wilt.
- **Met wat hulp** — "Kun je me helpen zorgen dat ik dinsdag op tijd bij mijn afspraak ben?" → *"Dan zet ik een herinnering om tien uur. Wilt u ook dat ik kijk hoe u er kunt komen?"* — Babbl denkt mee over wat er rond de afspraak nodig is: herinneringen, informatie en — als u dat wilt — vervoer. (Links to Vervoer tab.)

**Vervoer** — Naar de tandarts, het ziekenhuis of een activiteit in de buurt. Babbl kan helpen om er te komen op een manier die bij u past.
- **Zelf** — "Hoe laat moet ik weg voor de tandarts?" → *"Uw afspraak is om half elf. Als u om tien uur vertrekt, bent u ruim op tijd. Ik geef u om kwart voor tien een seintje."* — U gaat zelf. Babbl zorgt dat u op tijd weg bent.
- **Samen** — "Wil je mijn dochter vragen of ze me naar de tandarts kan brengen?" → *"Ik vraag het aan Anne. Als zij kan, weet ze meteen waar en hoe laat."* — Babbl vraagt het voor u, en zorgt dat iedereen weet waar en wanneer.
- **Met wat hulp** `STRAKS` — "Ik moet dinsdag naar de tandarts, maar ik heb niemand die me kan brengen." → *"Er rijdt een dorpsauto in uw buurt. Zal ik voor dinsdag een rit voor u aanvragen?"* — In de toekomst kan Babbl bijvoorbeeld een lokale vervoersdienst zoals de dorpsauto voor u reserveren. Hulp hoeft niet altijd van familie te komen.

**Boodschappen** — Even onthouden wat er nodig is. Samen boodschappen doen. Of iemand vragen iets mee te nemen.
- **Zelf** — "Zet koffie en melk op mijn boodschappenlijst." → *"Staat erop. Er staan nu vijf dingen op uw lijst."* — Babbl houdt bij wat u nodig heeft.
- **Samen** — "Mijn dochter doet straks boodschappen." → *"Zal ik Anne uw lijst laten zien? Dan kan ze meteen zien wat u nog nodig heeft."* — Een gedeelde lijst: wie u vertrouwt ziet wat er nodig is en kan zelf iets aanvullen. Het blijft úw lijst.
- **Met wat hulp** `STRAKS` — "Het lukt me deze week niet om zelf boodschappen te doen." → *"Zal ik iemand uit uw kring vragen? Of kijken welke mogelijkheden er in uw buurt zijn?"* — Straks kan Babbl ook helpen met een lokaal initiatief of een bezorgdienst. Altijd met u als uitgangspunt — nooit omdat een winkel ervoor betaalt.

Under the component:
- **H3:** Babbl neemt niet zomaar over.
- Babbl helpt op de manier die op dat moment bij u past. Zelf waar het kan, samen waar het fijn is en met wat hulp wanneer dat nodig is. Vandaag met wat hulp, morgen weer gewoon zelf. Het hangt af van de situatie, niet van een etiket.

Name note: "Anne" and "Peter" are illustrative. Brief uses "dochter" + "Peter"; giving the daughter a name makes it feel less like a role.

### 4 · Babbl staat inmiddels op tafel
- Tag: *Echt, en in ontwikkeling*
- **H2:** Babbl staat inmiddels op tafel.
- Wat begon met een eenvoudig idee — ouderen helpen om langer zelfstandig te blijven — krijgt steeds meer vorm. Dit zijn onze eerste echte Babbls.
- Ze zijn nog niet af. En dat is precies de bedoeling. Want pas als je Babbl op tafel kunt zetten, ermee kunt praten en hem iedere dag kunt gebruiken, ontdek je wat echt prettig werkt.
- [PHOTO, large]
- Caption: *Een kijkje aan onze werktafel — de eerste Babbl-prototypes, september 2026.*
- **H3:** We bouwen Babbl stap voor stap
- Hoe groot moet Babbl zijn? Is de bediening prettig? Is hij goed te verstaan? En misschien nog wel belangrijker: voelt het vanzelfsprekend om gewoon iets aan Babbl te vragen?
- Dat willen we niet alleen achter een bureau bedenken. Met deze eerste prototypes kunnen we Babbl uitproberen, verbeteren en straks samen met ouderen ontdekken wat er anders of beter moet.
- Zo groeit Babbl stap voor stap van een eerste prototype naar een vertrouwde assistent die gewoon een plekje in huis kan krijgen.
- Progress track: **✓ Eerste prototypes** → **● Eerste versie in ontwikkeling** → ○ Uitproberen in de praktijk → ○ Babbl voor thuis
- Under "in ontwikkeling", small text: *Nu in de maak: de Babbl-app, eenvoudig instellen, brieven laten uitleggen, uw agenda, en veilig omgaan met belangrijke gegevens.*

(Avoid "MVP" on the consumer page; "eerste versie" says the same.)

### 5 · Wat Babbl nog meer kan
Keep to 3 pillars, no repetition of scenarios:
- **Gewoon praten** — Geen menu's of knoppen onthouden. U vraagt het zoals u het aan iemand zou vragen.
- **Babbl en de app** — Babbl zelf is om mee te praten. De app is er voor wanneer een scherm handig is: bij het instellen, om een brief te fotograferen of iets veilig te bevestigen.
- **Een vraag tussendoor** — Hoe laat is de markt? Wat betekent dit woord? Kleine vragen mogen ook.

(Scam/phishing check from old page: drop from homepage until it is on the roadmap — confirm.)

### 6 · Ontworpen om thuis te horen
- Tag: *Waar we naartoe werken*
- **H2:** Ontworpen om thuis te horen.
- Babbl zit vol technologie, maar hoeft er niet zo uit te zien. Het uiteindelijke apparaat bouwen we voort op wat we met onze prototypes leren: eenvoudig te bedienen, prettig om tegen te praten en ontworpen om gewoon een plek in huis te krijgen.
- Visual: 4 devices side-by-side, same silhouette as prototype, fabric in ivoor · salie · terracotta · rustig blauw.
- Caption: *Ontwerprichting — geen eindproduct. De stoffen bekleding kan straks misschien worden gewisseld, zodat Babbl past bij uw interieur.*

### 7 · Uw vertrouwde kring
- **H2:** Mensen dichtbij, als u dat wilt.
- Babbl is er in de eerste plaats voor u. Maar soms is het fijn om iemand erbij te halen. In de Babbl-app kunt u mensen die u vertrouwt uitnodigen in uw kring — uw dochter, een buurman, een vriendin.
- List: Meedenken over een afspraak · Samen een boodschappenlijst bijhouden · Reageren als u om hulp vraagt · Een brief of bericht bekijken dat ú met hen deelt
- Closing line: *U bepaalt wie erbij hoort en wat zij mogen zien. Babbl houdt niemand in de gaten.*

### 8 · De wereld rondom Babbl
- Tag: *Straks*
- **H2:** U vertelt Babbl wat u wilt regelen. Babbl helpt u de juiste weg te vinden.
- Steeds meer loopt via apps, websites en inlogcodes. U hoeft niet te weten welke organisatie of welk systeem erachter zit. Babbl kan straks de brug zijn: naar familie en buren, maar ook naar de wereld om u heen.
- Visual: one worked example path, not a logo wall — "Ik moet dinsdag naar de tandarts" → Babbl → *dorpsauto* / *buurtvrijwilliger* / *Anne*. Then a quiet row of kinds (not names): vervoer in de buurt · welzijn en ontmoeting · gemeente · zorgverleners · agenda · boodschappen en bezorging.
- Trust line: *Babbl adviseert in uw belang. Als er ooit diensten van bedrijven bij komen, is dat altijd duidelijk — en betaalt niemand om door Babbl aanbevolen te worden.*

### 9 · Privacy & vertrouwen
- **H2:** Uw gegevens, uw regie.
- 4 cards: **U houdt de regie** — Babbl deelt alleen iets als u dat wilt. · **Duidelijke afspraken** — Mensen in uw kring zien alleen waar u toestemming voor geeft. · **Extra bescherming** — Gevoelige gegevens krijgen een extra beveiligingslaag. · **Vanaf het begin** — Privacy en veiligheid zijn geen toevoeging achteraf, maar een uitgangspunt.
- Link: Lees hoe we met uw gegevens omgaan →

### 10 · Samen ontdekken wat echt werkt
- **H2:** Samen ontdekken wat echt werkt.
- De volgende stap is de belangrijkste: Babbl gebruiken met de mensen voor wie we hem maken. De komende tijd zoeken we mensen en organisaties die mee willen doen.
- 3 cards:
  - **Ouderen en families** — Wilt u Babbl uitproberen en vertellen wat u ervan vindt? Meld u aan; we nemen contact op zodra er plek is.
  - **Organisaties** — Werkt u met ouderen, in welzijn, buurtinitiatieven of zelfstandig wonen? Denk mee over praktijktesten.
  - **Partners** — Biedt u een dienst die makkelijker bereikbaar zou moeten zijn? Laten we kijken hoe dat via Babbl kan.
- Form: Voornaam · E-mail · "Ik ben…" (select: oudere / familielid / organisatie / partner / anders) · button **Houd mij op de hoogte**
- Note: *We bouwen dit nu op. Er is nog geen groot testprogramma — u hoort van ons als er plek is.*

### 11 · Hoe Babbl begon
- **H2:** Begonnen aan de keukentafel.
- [Founder story, 3 short paragraphs — needs your input: what you observed, when; conversations; first prototypes.] Draft skeleton:
  Babbl begon met iets wat ik om me heen zag: [observation]. Mensen die prima zelf hun leven regelden, maar steeds vaker vastliepen op een brief, een app of een inlogcode.
  Na veel gesprekken met ouderen, familie en mensen uit zorg en welzijn werd het idee concreter. Inmiddels staan de eerste prototypes op tafel en wordt de software gebouwd.
  Babbl is nu nog klein. De volgende stap: de eerste versie, testen in de praktijk, samenwerken met organisaties en een team bouwen. — *[Naam], oprichter*

### 12 · Final CTA
- **H2:** Wilt u meedenken, meedoen of meer weten?
- Buttons: Volg onze ontwikkeling · Neem contact op (mailto)
- Then compact FAQ (5 items, updated) and "Meer weten" link row.

FAQ updates:
- *Is Babbl al te koop?* — Nog niet. De eerste prototypes zijn er en de eerste versie wordt gebouwd. Daarna volgen testen in de praktijk.
- *Voor wie is Babbl?* — Voor iedereen die zo lang mogelijk zelf de dingen van alledag wil blijven regelen. Mensen om u heen kunnen meedoen als u dat wilt.
- *Heb ik een smartphone nodig?* — [needs answer: is the app required for onboarding?]
- *Kijkt mijn familie mee?* — Nee. Mensen in uw kring zien alleen wat u met hen deelt.
- *Wat kost Babbl?* — keep existing answer.

---

## 7. Prototype photograph usage

- Placement: section 4, right after scenarios (≈ screen 4–5 on mobile). Also a small thumbnail/crop could appear in the hero tag area — **no**, keep hero mission-only per brief.
- Size: `max-width: 1100px` figure, ~85% of the 1200px container; full-bleed minus 16px gutter on mobile. Aspect ratio as shot (no crop to a device-only framing).
- Treatment: no filters, no background removal, `border-radius: var(--radius-lg)`, subtle shadow. Caption below in `--text-muted`.
- Format: export WebP ~2000px + JPEG fallback via `<picture>`, `loading="lazy"`, explicit `width/height` to avoid layout shift. Target < 400 KB.
- The same photo is the design reference for section 6 renders.

## 8. Scenario component UI

```
[ Brief ] [ Afspraak ] [ Vervoer ] [ Boodschappen ]      ← role="tablist", pill buttons
Intro line for the scenario (1–2 sentences)

 ┌ ZELF ─────────────┐ → ┌ SAMEN ────────────┐ → ┌ MET WAT HULP ─────┐
 │ 🗣 "user quote"   │   │ 🗣 "user quote"   │   │ 🗣 "user quote"   │
 │ ◯ Babbl reply     │   │ ◯ Babbl reply     │   │ ◯ Babbl reply     │
 │ explanation line  │   │ explanation line  │   │ explanation line  │
 └───────────────────┘   └───────────────────┘   └── [Straks] ───────┘
```

- Desktop: 3 equal columns in one card, joined by a thin connecting line with arrows; same neutral card colour for all three (no traffic-light colours → no "decline" progression). Level label in small caps + a one-word sub ("U regelt het zelf" / "Met iemand die u vertrouwt" / "Met een dienst of organisatie").
- Mobile (<768px): tabs become a horizontally scrollable pill row (all 4 fit at ~360px with short labels); levels stack vertically, joined by a short vertical connector "↓". Each level ~1 screen-third, so one scenario ≈ 2 screens.
- User quote: warm bubble (`--bg-muted`), Babbl reply: white bubble with small Babbl dot icon (drawn from prototype top/LED ring, not a robot).
- Accessibility: real `<button role="tab">`, arrow-key navigation, `aria-selected`, panels `role="tabpanel"`; all 4 panels in the HTML (works without JS: shown stacked). Hash deep links `#scenario-vervoer`.
- No auto-rotating carousel.

## 9. Current vs future

Two quiet labels only:
- No label = part of the first version being built now (letter explanation, calendar/reminders, sharing with your circle, shopping list).
- `Straks` pill (outlined, muted sage, small) on: Vervoer → Met wat hulp; Boodschappen → Met wat hulp; section 8 "De wereld rondom Babbl"; production design (labelled "Ontwerprichting").
- Future replies worded as possibility ("kan straks…", "zal ik voor u aanvragen?" in a future-labelled card only).
- A one-line legend under the scenario tabs: *Met "Straks" gemarkeerd: waar Babbl naartoe groeit.*

Question to confirm below: are shopping list and "share with trusted person" part of the first version? If not, they also get `Straks`.

---

## Open questions (blocking implementation)

1. **Prototype photo** — not in the repo and not attached to what I received. Path?
2. **Production visualisation (§6)** — I can't produce photoreal renders. Options: (a) clean SVG/CSS illustrations traced from the prototype silhouette in 4 fabric colours, clearly labelled "ontwerprichting"; (b) placeholder until you supply renders. Proposal: (a).
3. ~~Waitlist endpoint~~ — resolved: live uses Netlify Forms.
4. **Privacy claims** — old site says "lokale verwerking / gevoelige gegevens niet in de cloud". Still true with the current architecture? If not, the privacy page needs correcting too.
5. **Current scope** — which of these are in the first version: letter explanation, calendar, reminders, sharing with circle, shopping list, departure-time hint?
6. **Founder section** — your name, photo (real), 2–3 sentences on what you observed. Show name or keep "de oprichter"?
7. ~~Contact email~~ — resolved: `hallo@babbl.family`.
8. **Subpages** (voor-familie, voor-ouderen, voor-organisaties, hoe-het-werkt) still carry the old family-first story and the rectangular device images. In scope now, or follow-up?
