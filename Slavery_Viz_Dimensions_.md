“slavery” is not a single phenomenon, and treating all slave systems as equivalent hides enormous variation in:

conditions of capture

transport

labor expectations

legal status

bodily autonomy

hereditary transmission

violence, torture, mutilation

likelihood of social mobility

mortality rates

gendered exploitation

For a global project like yours, we need a taxonomy that is:

Historically accurate

Cross-cultural (Roman, Chinese, Islamic, Atlantic, African, American)

Analytically compact (so categories are meaningful and not too many)

Compatible with your Sankey structure

Below is the best possible classification system, capturing the actual diversity of human enslavement across 3,000 years.

✅ THE 12 ESSENTIAL CATEGORIES OF SLAVERY

These categories are distinct modes of enslavement.
Each slavery system in history can contain multiple modes.

This is the most granular academically credible classification.

CATEGORY SET 1 — HOW ENSLAVED PEOPLE WERE OBTAINED

These describe the mechanism of capture.

1. War Captives & Conquest Slavery

Most ancient empires (Rome, Assyria, Mongols)

Aztec, Inca, Southeast Asian kingdoms

Common across Africa

Distinctive traits: high mortality, mass enslavement, gender-selective (men killed, women enslaved)

2. Raiding-Based Slave Acquisition

Viking/Slavic trade

Crimean–Tatar raids

Barbary corsair raids

Amazonian tribal wars

Distinctive traits: continuous, predatory, not tied to formal warfare.

3. Child Levies / Tribute Slavery

Devshirme

Imperial Chinese tribute systems

Ethiopian debo levies

Ottoman Caucasus child markets

Distinctive traits:

Children selected based on criteria (fitness, beauty, intelligence)

Often provided elite status later

Not “brutal transport slavery” but still involuntary removal

4. Debt Bondage / Forced Labor Through Financial Obligation

Ancient Near East

India & Southeast Asia

Colonial Latin America

Modern bonded labor in South Asia

Distinctive traits:

Not chattel

Often inheritable

Still coerced, often lifelong

CATEGORY SET 2 — CONDITIONS OF OWNERSHIP
5. Chattel Slavery (People as Property)

Transatlantic slave trade

Roman slavery

Many African kingships

Southeast Asian hereditary slavery

Islamic world (partial chattel, partial domestic)

Distinctive traits:

Can be sold

No legal personhood

Hereditary status

This is the category most people imagine when they hear “slavery.”

6. Household / Domestic Slavery

Islamic world

China and Korea

Roman familia urbana

Ottoman harems

Distinctive traits:

Mixed treatment (sometimes benign, sometimes horrifying)

High exploitation risk for women (sexual slavery)

7. Military Slavery

Mamluks

Janissaries (post-training)

Mongol conscript slaves

Aztec/Maya war slaves

Distinctive traits:

Often given prestige and mobility

Still legally slaves (kul, mamluk)

8. State/Administrative Slavery

Ottoman palace system

Chinese eunuchs

Roman bureaucracy slaves

Incan administrators

Distinctive traits:

High-status roles

Power ≠ freedom

CATEGORY SET 3 — TREATMENT AND BODILY VIOLENCE
9. Eunuch Slavery (Castration-Based)

Islamic courts

China (largest eunuch system in world history)

Byzantium

Ethiopia

Distinctive traits:

Castration mortality 30–90%

Elite roles for survivors

One of the most violent forms of slavery in history

10. Plantation / Agricultural Slavery

Transatlantic

Roman latifundia

Persian estates

Southeast Asian rice slavery

Distinctive traits:

Extreme mortality

Gendered division

Mass-scale labor

11. Sexual Slavery & Concubinage

Ottoman harems

Mongol conquests

Roman slavery (widespread)

African domestic slavery

Modern trafficking

Distinctive traits: gendered, continuous across all societies

12. Penal Slavery / Forced Labor as Punishment

Qin/Han China

Rome

Tsarist Russia

Modern forced labor camps

North Korea today

Distinctive traits:

Not hereditary

Extremely harsh conditions

Ranges from mines to construction to military labor

✅ These 12 categories allow you to classify all historical and modern systems with great precision.
HOW TO APPLY THIS TO YOUR PROJECT

Each slavery system should have:

A. A “Slavery Profile” listing which categories apply

Example for Devshirme:

❌ Chattel slavery (not applicable)

❌ Plantation slavery (not applicable)

✔ Child levy / tribute slavery

✔ Military slavery

✔ Administrative slavery

✔ Domestic slavery (some)

❌ Eunuch slavery (not central, though some Balkan boys were castrated after arrival)

This gives audiences nuance without overwhelming them.

---

"categories": [
  "child_levy",
  "military_slavery",
  "administrative_slavery",
  "domestic_slavery"
]


direction: treat “slavery” as a set of dimensions, attach those to your data, and then let the user filter or recolor the Sankey by those dimensions instead of only by trade.

Let me lay out a concrete, buildable scheme.

1. Think in dimensions, not more “trade types”

You already have the “which trade?” axis (Roman, Transatlantic, etc.).

Now we add a small set of orthogonal dimensions that we can attach to each trade (or even to each flow):

Dimension A – How were people obtained? (acquisition_mode)

Binary flags, any number can be true:

war_captive

raid

child_levy (Devshirme, some African systems)

debt_bondage

judicial_penal

birth_into_slavery (hereditary)

kidnapping_trafficking (modern)

Dimension B – What was their legal status? (legal_status)

Choose 1–2 predominant ones per system:

chattel_property (can be bought/sold; Atlantic, Roman, much of Islamic world)

state_slave (kul, eunuchs, penal labor)

bonded_labor (debt/family obligation)

corvee_subject (forced state labor, not fully property)

clientage_serfdom (attached to land or patron)

Dimension C – What did they mainly do? (labor_types)

Again, multiple can be true, with rough weights if you want:

plantation_agriculture

smallholder_agriculture

domestic_household

military

administrative_bureaucratic

construction_infrastructure

mining_quarry

maritime_pearl_fishing

sexual_concubinage

pastoral_nomadic

Dimension D – Brutality profile (severity indices)

Here you can start to differentiate Devshirme from Atlantic chattel slavery.

Use simple 0–3 scales (0 = none/rare, 3 = systematic/extreme):

transport_mortality (0–3)

bodily_mutilation (castration, branding, etc.) (0–3)

sexual_exploitation (0–3)

hereditary_rigidity (0–3: how likely children are automatically enslaved)

upward_mobility (0–3, but note: high mobility = lower severity)

You don’t need numerical precision; you just need comparative structure:

Atlantic Middle Passage: transport_mortality: 3

Devshirme: transport_mortality: 1, upward_mobility: 3, etc.

2. How this plugs into your existing data

Right now each trade has something like:
{
  id: "transatlantic",
  name: "Transatlantic Trade",
  period: "1500 - 1867",
  startYear: 1500,
  endYear: 1867,
  lowEstimate: 10000000,
  highEstimate: 12800000,
  flows: [ ... ],
  description: "...",
  ending: "...",
  destinationDetails: { ... }
}

We extend it like this:

{
  id: "transatlantic",
  ...,
  acquisition_mode: ["war_captive", "raid", "kidnapping_trafficking"],
  legal_status: ["chattel_property", "hereditary"],
  labor_types: [
    { type: "plantation_agriculture", weight: 0.7 },
    { type: "domestic_household", weight: 0.15 },
    { type: "smallholder_agriculture", weight: 0.1 },
    { type: "sexual_concubinage", weight: 0.05 }
  ],
  brutality_profile: {
    transport_mortality: 3,
    bodily_mutilation: 2,
    sexual_exploitation: 2,
    hereditary_rigidity: 3,
    upward_mobility: 0
  }
}

And Devshirme might look like:
{
  id: "devshirme",
  name: "Devshirme Child Levy",
  ...,
  acquisition_mode: ["child_levy"],
  legal_status: ["state_slave"],
  labor_types: [
    { type: "military", weight: 0.5 },
    { type: "administrative_bureaucratic", weight: 0.3 },
    { type: "domestic_household", weight: 0.2 }
  ],
  brutality_profile: {
    transport_mortality: 1,
    bodily_mutilation: 1,   // some castration but not universal
    sexual_exploitation: 1,
    hereditary_rigidity: 1, // not always hereditary, often broken
    upward_mobility: 3      // many could reach high office
  }
}

3. How the filters change the Sankey

Once every trade has these tags, you can offer UI filters that:

Include/exclude whole trades

Example: “Show only systems with chattel_property.”

Implementation: filter slaveryData before drawing.

Fade or highlight by dimension

Example: a slider “Transport mortality ≥ 2”

Anything below threshold is drawn at low opacity.

Recolor by dimension instead of by trade

Toggle: “Color by trade” / “Color by brutality”

E.g., map transport_mortality 0–3 to a color ramp (blue→red).

Filter by labor type

Checkbox list: plantation, military, domestic, etc.

Only flows from trades whose labor_types include those tags are shown fully.

Technically, in your React/D3 code:
const [filters, setFilters] = useState({
  acquisition: [],
  legalStatus: [],
  laborTypes: [],
  minMortality: 0
});

const filteredTrades = slaveryData.filter(trade => {
  // acquisition filter
  if (filters.acquisition.length &&
      !filters.acquisition.some(tag => trade.acquisition_mode.includes(tag))) {
    return false;
  }

  // legal status filter
  if (filters.legalStatus.length &&
      !filters.legalStatus.some(tag => trade.legal_status.includes(tag))) {
    return false;
  }

  // brutality filter
  if (trade.brutality_profile.transport_mortality < filters.minMortality) {
    return false;
  }

  return true;
});

Then you draw the Sankey using filteredTrades instead of the full array.

4. Minimal viable set for v1

To keep you from drowning in metadata, I’d start with just four dimensions per trade:

acquisition_mode (array of 1–3 tags)

legal_status (1–2 tags)

labor_types (2–4 tags, no weights at first)

brutality_profile.transport_mortality (0–3 scale)

Filters for v1:

Checkbox group: Acquisition: ☑ war captives ☑ raids ☑ child levy ☑ debt bondage …

Checkbox group: Legal status: ☑ chattel ☑ state slave ☑ bonded labor …

Slider: Transport mortality: min level 0–3

Optional: Highlight military vs plantation vs domestic systems

That’s enough to show why Devshirme “looks” very different from the Middle Passage on the same chart, without rewriting your entire data model.


