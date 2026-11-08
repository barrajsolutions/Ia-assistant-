# Lovable website review — « Conseiller Securite Financiere »

Project `b4161a5f-d953-41bd-8263-dcb6928be764` · published · read-only review, **no change sent to Lovable**. Every item below needs your approval before it is sent to the Lovable agent (which spends Lovable credits; workspace is on the free plan).

## What exists (verified in code)
- Bilingual FR/EN, French default, mobile-first; 13 service pages; solutions directory; life-moments homepage; FAQ; privacy page (`/confidentialite`).
- Two lead entry points, both writing to Lovable Cloud table `leads` through server function `submitLead`:
  - **Quiz** (« Faire mon bilan gratuit ») → `source = quiz`, quiz answers/score.
  - **Booking form** (« Réserver un appel gratuit » / « Parler avec Mohamad · 20 min ») → `source = booking`, topic (14 codes), preferred language (FR/EN/AR), best time, consent checkbox required.
- Attribution: `utm_source`, `utm_campaign` and topic captured per visit (cookie banner states no advertising cookies).
- Booking is **not self-serve**: the thank-you text says Mohamad will contact the person to set the Teams call.
- AMF certificate 272553 and iA affiliation in footer.

## Measured (Lovable analytics, Oct 30 – Nov 8)
30 visitors · 32 pageviews · 1.07 pages/visit · 87% mobile · source **100% « Direct »** · 1 lead (quiz) → ≈ 3% visitor→lead (small sample; not statistically meaningful).

## Recommendations (ranked by impact ÷ effort)
| # | Change | Why | Data/compliance note |
|---|---|---|---|
| L1 | **New-lead alert with no personal data**: when a row is inserted, send an email to your iA address saying only « Nouveau lead (booking, sujet : vie) — ouvrez le tableau ». | Today nobody is notified; a booking can wait days. | Alert contains no name/email/phone. Uses Lovable's email integration (Resend) — new service, needs your OK and possibly company approval. Alternative with no new service: W1 adds « new leads since yesterday: N » from an aggregate count (I can enable this immediately on your OK). |
| L2 | **UTM on every link you publish**: Instagram bio `?utm_source=instagram&utm_campaign=bio`, Facebook, LinkedIn, TikTok, Google Business, email signature. | 100% « Direct » means social results are invisible. | No code change; the site already stores UTMs. |
| L3 | **Self-serve booking**: replace « on vous contactera » with a Microsoft Bookings link (company Teams) after the form. | Removes a manual step; enables lead→appointment measurement. | Must be your company-approved Bookings page. |
| L4 | **Arabic language option** on the site (you serve FR/EN/AR; only FR/EN pages exist). | Arabic-speaking newcomers are a stated audience. | Content review for AMF wording required. |
| L5 | Sticky mobile CTA « Appel gratuit 20 min » | 87% mobile traffic. | — |
| L6 | Add `topic` + `source` counts to the W5 weekly report (aggregate). | Measure which themes convert. | Aggregate only — already in W5 prompt. |

## Safe Make integration (proposal, not built)
Only if L1 email is not acceptable: a Lovable database webhook → Make webhook that receives **only** `{source, topic, utm_source, created_at}` and posts a Notion row in AI Tasks (« Rappeler un nouveau lead — voir tableau Lovable »). No PII leaves Lovable. Uses one Make active-scenario slot.

## Campaign tracking without exposing client data
- Track at the **campaign level**: UTM source/campaign + topic, counted weekly. Never export individual rows.
- Appointment conversion: count booked Teams meetings in Google Calendar by title prefix (e.g. « RDV – lead site ») — requires you to use that prefix; no client names in titles.
