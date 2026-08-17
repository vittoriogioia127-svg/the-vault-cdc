# VAULT PITCH DECK - Design Contract

Deliverable: a 12-slide stakeholder pitch deck presenting The Vault. Claude Design composes on the frozen
Showroom design language. This is a SHAREABLE artifact: it will be shown to the business owner, the finance
sponsor and the process referent, and may circulate beyond them.

## Hard rules

- DA is frozen: Showroom. Compose with the attached vault-tokens.css, do not restyle, do not invent tokens.
- Geist for UI text, Geist Mono for every number, code, ref or date. Light mode default.
- Muted means complete; colour marks only the exception. One black pill maximum per slide.
- Hairlines and soft fills only. No gradients, no glow, no shadows, no stock imagery, no icons beyond the
  existing minimal set. The mark is M4 Checksum, plain-text fallback [.].
- Slide format 16:9, generous margins, one idea per slide. Headlines short, support copy max three lines.
- Language: English.
- No em dashes or en dashes anywhere in the copy. Hyphens only.

## Confidentiality constraints (breaching any of these fails the deliverable)

Never mention or imply: the build stack, any AI involvement, effort estimates, the simulation strategy, or
internal politics. Do not promise automatic extraction of any document type as a day-one capability: the
product narrative is the pipeline and the gate, extraction depth arrives progressively. The data horizon
slide (10) presents future capability enabled by the register, never a pilot deliverable. Analytics on HR
or payroll data is explicitly gated on cyber (CDS) sign-off.

## Numbers allowed in the deck

Structural and defensible only: 7 cost heads, 40 cost elements mapped (16 Salary, 6 Contribution, 18
Fringe Benefit), 39 active on MMSP, 3 conditions to one gate, 1 engine and N projects, a 28-day notice
window (configurable per contract), configuration returned by the Cost Controller with all 40 rows
verdicted in 48 hours. Claims are "worth hundreds of millions of PHP". Do not use demo amounts
(421.9M etc.) and do not invent any financial figure.

## The 12 slides

### 01 Cover
Headline: The Vault. Subline: Every cost, proven. Footer: Colas Rail, MMSP EOT001 pilot. Mark M4 top left.

### 02 The problem
Headline: Claims worth hundreds of millions of PHP rest on manual substantiation.
Content: today the cost data of an EOT claim is fragmented across departments, reassembled by hand when an
event occurs, and gaps surface too late. Slow, hard to trace, financially exposed. Frame the process as the
problem, never the people.

### 03 Today's pipeline
Headline: Three layers of documents, one person holding them together.
Visual: the three-layer strip, Source files, Working files, Evidences, with the middle layer highlighted as
manual effort. One line: the working layer is human today.

### 04 The Vault
Headline: Drop. Extract. Substantiate. Validate.
Content: departments drop their source files, the tool files each cost down to the person, ties it to its
proof, and routes it through validation. A permanent cost register, with claim dossiers assembled on top.
Visual: the four-stage pipeline in the existing visual grammar.

### 05 The gate
Headline: Three conditions, one door.
Visual: the completeness gate figure, 01 Source deposited, 02 Evidence on file, 03 Validator sign-off,
arrow, the single black pill: Complete. Caption: complete is a fact, not a document count. What is complete
stays quiet, colour marks only the exception.

### 06 Granularity
Headline: Down to one person, one element, one month.
Visual: the cascade, Cost Head A to Category to Cost Element to Staff x Origin x Currency x Month.
Support: 40 cost elements mapped across Salary, Contribution and Fringe Benefit, 39 active on the pilot.

### 07 Traction
Headline: The rulebook is written by the person who runs the process today.
Content: the substantiation configuration, what proves each of the 40 cost elements, who provides it and
how often, was returned fully verdicted by the Cost Controller in 48 hours. The tool encodes the real
process, validated at element level, not an assumption.

### 08 The claim lifecycle
Headline: Notice, versions, seal.
Content: each contractual event carries its notice countdown (28 days on this contract, configurable). A
sealed claim is never altered: reopening creates the next version with a mandatory reason and a line-level
diff. Every client submission is traced with its disclosure profile.

### 09 One engine, N projects
Headline: Configuration, not code.
Content: taxonomy, owners, sources, proof rules, notice periods and disclosure profiles are configuration
objects per project. Any Colas project onboards by loading its configuration. MMSP is the first
configuration loaded, not a bespoke tool.

### 10 The data horizon
Headline: From claims defense to cost intelligence.
Content: every cost in the register is dated, attributed, categorised and proven. That discipline produces
a clean financial dataset as a byproduct: a cost control data foundation. What it unlocks, as flags and
reports: a utility invoice deviating from its own history, a duplicate invoice, a cost per staff outlier
against its package, evidence aging without validation, period-on-period variance, and cross-project
comparison once several projects are onboarded.
Mandatory closing line on the slide: none of this is built for the pilot; all of it becomes possible
because the register exists.
Visual: a restrained flag list or a quiet variance sparkline in tokens, no dashboard theatre.

### 11 Governance
Headline: Role-based, isolated, tamper-evident.
Content: nominative HR and payroll data isolated at the data level per role. Every document fingerprinted
on upload, write-once history, any later change detectable. Production with real HR data is gated on cyber
sign-off; the pilot runs on test data until then.

### 12 Roadmap and the ask
Headline: Two gates govern everything.
Content: configuration gate, substantially closed with the process referent; mandate gate, this room. Then
the phased build: core workflow first, extraction deepening by stages, pilot on one cost head, then group
onboarding. The ask: the mandate to build the pilot.

## Page naming
Name pages: Vault Pitch 01 Cover, Vault Pitch 02 Problem, and so on. One page per slide.

## Acceptance checklist

- 12 pages, 16:9, light mode, tokens only, zero gradients or glow, one black pill max per slide.
- All numbers match the allowed list; no invented figures; no demo amounts.
- Slide 10 carries the mandatory closing line verbatim.
- No stack, no AI mention, no effort estimates, no extraction promises, no dashes other than hyphens.
- Every number, ref and date set in Geist Mono.

---

# Amendment v1.1 (post checkpoint, 2026-08-17)

The 3-slide checkpoint (01, 05, 10) passed on register and failed on three points. This amendment is
binding for the completion run.

## Checkpoint fixes (apply before or while completing the remaining slides)

1. Slide 10: add the mandatory closing line, verbatim, as the last line of the slide: "None of this is
   built for the pilot; all of it becomes possible because the register exists." This is an acceptance
   item; the slide fails without it.
2. Slide 05: the composition overflows the frame, the Complete pill is clipped at the right edge.
   Recompose inside the 16:9 stage: conditions, arrow and the full pill visible with a proper right
   margin. The pill reads "Complete", whole.
3. Slide 01: add the contract footer, quiet, Geist Mono, bottom left: Colas Rail, MMSP EOT001 pilot.
   If the drawn M4 mark exists in this project, use it consistently on every page; the plain-text [.]
   stays the acceptable fallback.

## Language toggle (new requirement)

- Every page carries a quiet FR | EN segmented control, top right, Geist Mono 11px, styled like the CDC
  topbar segments. English is the default.
- The toggle swaps all copy on the page. Numbers, refs, dates, proper nouns (The Vault, MMSP EOT001,
  Colas Rail, people, BIR, CDS) and the mark are identical in both languages.
- The French copy is provided below and is the copy: do not retranslate, do not add claims. Same
  typographic laws in both languages. No em dashes or en dashes in either language, hyphens only.

## French copy, slide by slide

### 01 Cover
Headline: The Vault. Subline: Chaque cout, prouve. Footer: Colas Rail, pilote MMSP EOT001.

### 02 The problem
Headline: Des claims de plusieurs centaines de millions de PHP reposent sur une substantiation manuelle.
Body: aujourd'hui, les donnees de cout d'un claim EOT sont fragmentees entre les departements,
rassemblees a la main quand un evenement survient, et les trous apparaissent trop tard. Lent, difficile
a tracer, financierement expose. Le probleme est le process, jamais les personnes.

### 03 Today's pipeline
Headline: Trois couches de documents, une personne pour les tenir ensemble.
Strip labels: Fichiers sources, Fichiers de travail, Preuves. Line: la couche du milieu est humaine
aujourd'hui.

### 04 The Vault
Headline: Deposer. Extraire. Substantifier. Valider.
Body: les departements deposent leurs fichiers sources, l'outil classe chaque cout jusqu'a la personne,
le relie a sa preuve, et le fait passer par la validation. Un registre de couts permanent, et des
dossiers de claim assembles par-dessus.

### 05 The gate
Headline: Trois conditions, une porte.
Cards: 01 Source deposee, 02 Preuve au dossier, 03 Validation signee. Pill: Complet.
Caption: complet est un fait, pas un nombre de documents. Ce qui est complet reste silencieux, la
couleur ne marque que l'exception.

### 06 Granularity
Headline: Jusqu'a une personne, un element, un mois.
Support: 40 elements de cout repartis entre Salary, Contribution et Fringe Benefit, 39 actifs sur le
pilote. Cascade labels unchanged (Cost Head A, Category, Cost Element, Staff x Origin x Currency x Month).

### 07 Traction
Headline: Le livre de regles est ecrit par celui qui fait tourner le process aujourd'hui.
Body: la configuration de substantiation, ce qui prouve chacun des 40 elements de cout, qui le fournit
et a quelle frequence, a ete retournee entierement verdictee par le Cost Controller en 48 heures.
L'outil encode le process reel, valide element par element, pas une hypothese.

### 08 The claim lifecycle
Headline: Notice, versions, sceau.
Body: chaque evenement contractuel porte son compte a rebours de notice (28 jours sur ce contrat,
configurable). Un claim scelle n'est jamais modifie: le rouvrir cree la version suivante avec une
raison obligatoire et un diff ligne a ligne. Chaque soumission au client est tracee avec son profil
de divulgation.

### 09 One engine, N projects
Headline: De la configuration, pas du code.
Body: taxonomie, responsables, sources, regles de preuve, delais de notice et profils de divulgation
sont des objets de configuration par projet. N'importe quel projet Colas embarque en chargeant sa
configuration. MMSP est la premiere configuration chargee, pas un outil sur mesure.

### 10 The data horizon
Headline: De la defense des claims a l'intelligence des couts.
Body: chaque cout du registre est date, attribue, categorise et prouve. Cette discipline produit un
jeu de donnees financieres propre comme sous-produit: une fondation de donnees de cost control.
Kicker list title: Ce que ca debloque.
List: 01 une facture d'electricite qui devie de son propre historique, 02 une facture en doublon,
03 un cout par personne aberrant par rapport a son package, 04 une preuve qui vieillit sans
validation, 05 la variance periode sur periode, 06 la comparaison inter-projets une fois plusieurs
projets embarques.
Mandatory closing line: rien de tout cela n'est construit pour le pilote; tout devient possible parce
que le registre existe.

### 11 Governance
Headline: Des roles, une isolation, une trace inalterable.
Body: les donnees RH et paie nominatives sont isolees au niveau de la donnee, par role. Chaque
document recoit une empreinte au depot, historique write-once, toute alteration ulterieure est
detectable. La production avec des donnees RH reelles est conditionnee a la validation cyber; le
pilote tourne sur donnees de test d'ici la.

### 12 Roadmap and the ask
Headline: Deux gates gouvernent tout.
Body: le gate de configuration, substantiellement ferme avec le referent process; le gate du mandat,
cette salle. Puis la construction par phases: le coeur du workflow d'abord, l'extraction approfondie
par paliers, le pilote sur un cost head, puis l'embarquement groupe.

## Slide 12, the ask: two variants

Build variant A by default. Hold the final wording of the ask until confirmation; switching is one line.
- Variant A (mandate not yet granted). EN: The ask: the mandate to build the pilot. FR: La demande: le
  mandat pour construire le pilote.
- Variant B (mandate already granted). EN: The ask: sponsor The Vault as a group platform beyond MMSP.
  FR: La demande: sponsoriser The Vault comme plateforme groupe au-dela de MMSP.

## Amended acceptance checklist additions

- Every page carries the FR | EN toggle; the French copy matches this amendment word for word.
- Slide 10 carries the mandatory closing line in both languages.
- Slide 05 shows the full Complete pill inside the frame.
- Slide 01 carries the footer.
