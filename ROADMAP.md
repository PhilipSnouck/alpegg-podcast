# Alpegg Podcast — Roadmap

Besloten familiepodcast voor de huidige en toekomstige generaties van de Alpegg-familie.
Philip verzorgt opname, montage en editing. Platform in Next.js op Vercel.

- **Live:** niet live
- **GitHub:** https://github.com/PhilipSnouck/podcast-alpegg
- **Local:** `C:\Users\p.snouckaert\Personal repos\podcast-alpegg`

---

# 🔥 Now

## Voorbereiding & Apparatuur (S)

Opnameapparatuur regelen, jingles kiezen en een testronde doen voordat de echte
opnamedag gepland wordt.
Done when: testronde thuis gedaan, jingles gekozen, akoestiek chalet getest.

- [ ] Zoom H6 of H8 recorder huren — incl. losse microfoon per persoon (S)
- [ ] Royalty-vrije jingles kiezen op Pixabay of Free Music Archive — 1 à 2 fragmenten (S)
- [ ] Akoestiek chalet verbeteren — kussens, dekens en gordijnen klaarzetten (S)
- [ ] Testronde thuis — 15 min opnemen met twee mensen, daarna monteren (S)

---

# 🚀 Next Build

## GarageBand Template & Familiebijdragen (M)

10-track template eenmalig bouwen in GarageBand en alle vaste bijdragen van de
familie verzamelen. Done when: template werkt end-to-end met alle vaste tracks ingevuld.

- [ ] GarageBand template aanmaken met 10 tracks (S)
- [ ] Jingles invoegen in track 1 (intro) en track 10 (outro) (S)
- [ ] Aankondigingen per rubriek inspreken door een familielid — gaan permanent in template (S)
- [ ] Vaste familiebijdragen verzamelen vanuit huis — openingszinnen, raadsels, vraag van Otto, outro (M)
- [ ] Template opslaan en testen met dummy-audio (S)

## Opnamedag plannen (S)

Datum en logistiek vastleggen voor de opnamedag in het chalet.
Done when: datum bevestigd, hosts per aflevering aangewezen.

- [ ] Datum prikken — één hoofddag en één reservedag (S)
- [ ] Hosts aanwijzen per aflevering — 2 tot 4 kinderen, roulerend (S)
- [ ] Aflevering 0 inplannen: "Intro — Wie zijn wij?" (S)

---

# 🔮 Future

## Opnamedag uitvoeren (M)
  Kerngesprekken opnemen met Albertine, Hendrik, Bibianne en Frederik in het chalet. Aflevering 0 opnemen.

## Montage & Editing per aflevering (M)
  Opnames importeren in GarageBand template, content op juiste tracks slepen, monteren en exporteren als MP3. Philip voert dit uit per aflevering.

## Mastering via Auphonic (S)
  MP3 uploaden naar auphonic.com, verwerking afwachten (ruisverwijdering + volumes gelijktrekken), verbeterd bestand downloaden. Gratis: 2 uur/maand. Losse credits: ~€11 per 9 uur.

## Platform bouwen op Vercel (L)
  Next.js site op alpegg.vercel.app. Media Session API voor vergrendelscherm-gebruik (iPhone Safari + Android Chrome). Besloten toegang — niet indexeerbaar, alleen via link. Audio-opslag via Google Drive of S3.

## Lancering (S)
  Eerste aflevering uploaden naar de site en link verspreiden in de familie.

---

# ✅ Done

## Script & Draaiboek (M)
- [x] Draaiboek geschreven
- [x] Afleveringenlijst vastgesteld — 9 afleveringen + 2 bonus
- [x] Vaste structuur per aflevering bepaald — 6 onderdelen
- [x] Rolverdeling bepaald — vertellers, hosts, productie, familie

---

# 📝 Notes

### Afleveringen
```
0  — Intro: Wie zijn wij?
1  — Otto Lanz & het ontstaan van Alpegg
2  — Het huis door de tijd
3  — Verhalen uit de oude doos
4  — Het (buiten)leven om Alpegg
5  — Vrienden van Alpegg
6  — Verhalen uit de nieuwe doos
7  — Het ritme van het jaar
8  — Beheer in harmonie
✦  — Bonus: Het verhaal van Moelie (Albertine)
✦  — Bonus: Zwitserse les (Hendrik, Fre en Bibiane)
```

### Vaste structuur per aflevering
```
1. Vaste intro                    (alle kinderen)
2. Raad het verhaal: de vraag     (alle kinderen)
3. Topic van de dag               (kerngesprek vier vertellers)
4. De vraag van Otto              (alle kinderen)
5. Raad het verhaal: het antwoord
6. Vaste afsluiting
```

### GarageBand template tracks
```
Track 1   Intro-jingle             [vast bestand]
Track 2   Rubriek 1 aankondiging   [vast bestand]
Track 3   Rubriek 1 content        [← nieuwe opname per aflevering]
Track 4   Rubriek 2 aankondiging   [vast bestand]
Track 5   Rubriek 2 content        [← nieuwe opname per aflevering]
Track 6   Rubriek 3 aankondiging   [vast bestand]
Track 7   Rubriek 3 content        [← nieuwe opname per aflevering]
Track 8   Rubriek 4 aankondiging   [vast bestand]
Track 9   Rubriek 4 content        [← nieuwe opname per aflevering]
Track 10  Outro-jingle             [vast bestand]
```

### Kosten
| Onderdeel | Kosten |
|---|---|
| GarageBand | Gratis (al op Mac) |
| Royalty-vrije muziek | Gratis |
| Vercel hosting | Gratis |
| Auphonic (~15 uur materiaal) | ~€18–20 eenmalig |
| Domeinnaam (optioneel) | €10–15 / jaar |

### Deploy flow
1. MP3 exporteren uit GarageBand
2. Uploaden naar Auphonic → verbeterd bestand downloaden
3. Bestand uploaden naar Vercel site
4. Aflevering verschijnt automatisch voor de familie
