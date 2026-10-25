# Alpegg - Een Familiepodcast

> Opdat de bijzondere verhalen van Alpegg blijven leven, voor het nageslacht.

Een besloten familiepodcast voor de huidige en toekomstige generaties. Tijdcapsule van stemmen, verhalen en herinneringen.

## Projectpagina

Open `index.html` lokaal (of `npx serve`). De pagina staat bewust niet online - het luisterplatform voor de familie komt later als eigen, besloten Next.js-site op Vercel (zie ROADMAP.md).

## Inhoud

- `index.html` - projectpagina met roadmap, afleveringenlijst, rollen en technisch overzicht

## Afleveringen

| # | Titel |
|---|-------|
| 0 | Intro: Wie zijn wij? |
| 1 | Otto Lanz & het ontstaan van Alpegg |
| 2 | Het huis door de tijd |
| 3 | Verhalen uit de oude doos |
| 4 | Het (buiten)leven om Alpegg |
| 5 | Vrienden van Alpegg |
| 6 | Verhalen uit de nieuwe doos |
| 7 | Het ritme van het jaar |
| 8 | Beheer in harmonie |
| ✦ | Bonus: Het verhaal van Moelie |
| ✦ | Bonus: Zwitserse les |

## Productie

Hoe een aflevering gemaakt wordt, van opname tot publicatie. Opnemen en monteren
gebeuren in **Adobe Audition** (Windows), buiten deze repo. Dit is het volledige
stappenplan zodat het later opnieuw te doen is zonder uitzoeken.

### Vooraf instellen (eenmalig)

- **Audio Hardware:** `Edit > Preferences > Audio Hardware` > Device Class op
  **Windows Sound (WASAPI)** (niet ASIO4ALL). Default Output = je koptelefoon/earbuds.
  Bij Bluetooth: Default Input op **None** laten, anders valt de geluidskwaliteit terug.
- **Opnametip (op de opnamedag):** neem **hard genoeg** op, pieken rond **-12 tot -6 dB**
  op de recorder. Te stil opnemen betekent veel ruis zodra je het later optilt naar -16.
  Geen enkele software-truc verslaat een hard, schoon bronsignaal.

### Mappen per aflevering

```
Aflevering-XX/
  01_ruw/       originele opnames, hier nooit in bewerken
  02_bewerkt/   losse bewerkte stukken
  03_sessie/    Audition-sessies (.sesx)
  04_export/    WAV-master en MP3
```

### Stap 1 - Kerngesprek monteren (de losse mics)

1. Zet de mic-opnames in een nieuwe multitrack-sessie.
2. **Synchroniseer** de sporen op de klap: zet de klap-piek in alle sporen recht onder elkaar.
3. Check of de stemmen ongeveer even hard zijn (golfvormhoogte, of `Window > Amplitude
   Statistics` en kijk naar **RMS**, binnen ongeveer 2-3 dB is prima). Alleen bijsturen met
   clip-gain als er eentje duidelijk afwijkt.
4. Selecteer alle clips (Ctrl+A). In het **Essential Sound**-paneel, type **Dialogue**:
   - **Reduce Noise** ongeveer **5**
   - **Reduce Rumble** ongeveer **5**

   Houd ze laag: te hoog maakt de stem metalig of "onderwater". Auto-Match is op deze stap
   niet nodig.
5. `File > Export > Multitrack Mixdown > Entire Session` > **WAV** (48 kHz, stereo,
   32-bit float). Met kopruimte, dus hier **geen** limiter of loudness.
6. **Knippen** doe je nu makkelijk op dat ene WAV: open in de Waveform-editor, selecteer
   versprekingen/stiltes en Delete. Knip bij voorkeur op een adempauze.

### Stap 2 - Aflevering opbouwen

1. Nieuwe multitrack-sessie.
2. Sleep de onderdelen in volgorde achter elkaar (één spoor volstaat):
   intro-jingle > vaste intro > raadsel (vraag) > kerngesprek (de WAV uit stap 1) >
   vraag van Otto > raadsel (antwoord) > outro-jingle.
3. Overgangen: clips iets over elkaar schuiven geeft een automatische **crossfade**; een
   hoekje naar binnen slepen geeft een **fade** in of uit.
4. Balans met Essential Sound **Auto-Match**: spraak = type **Dialogue** (gaat naar -23),
   muziek = type **Music** (gaat naar -25). Muziek daarna op het oor bijstellen met clip-gain.
5. **Let op de pan:** zet de pan van elk spoor op **center**, anders speelt een spoor maar
   in één oor (en dat blijft zo in de mixdown).
6. `File > Export > Multitrack Mixdown > Entire Session` > **WAV**. Nog steeds met kopruimte.

### Stap 3 - Masteren (loudness) - de laatste stap, op het complete WAV

1. Open het samengevoegde WAV uit stap 2.
2. `Window > Match Loudness` > sleep het bestand erin > klik het **scan-icoon** (vergrootglas)
   om de huidige loudness te zien.
3. **Match Loudness Settings:**
   - Match To: **ITU-R BS.1770-3 Loudness**
   - Target Loudness: **-16 LUFS**
   - Max True Peak Level: **-1 dBTP**
   - Use Limiting: **aan**
4. Het **Export-vinkje UIT** laten (dan past hij het toe op het geopende bestand) > **Run**.
5. Resultaat rond -16 LUFS. Net ernaast (bijv. -16,9) is prima. Veel te zacht (bijv. -19)?
   Nog een keer **Run**, of eerst een **Hard Limiter** (`Effects > Amplitude and Compression`,
   max -1 dB) erover. Voor een familiepodcast is een klein verschil geen probleem.

Waarom pas hier: Match Loudness meet de **hele aflevering als geheel**. Elke aflevering op
-16 LUFS zetten zorgt dat ze allemaal even hard klinken. Doe dit nooit op losse tracks, en
master maar **één keer** (opschonen hoort bij stap 1, loudness alleen hier).

### Stap 4 - Opslaan en exporteren

- **Sessie bewaren:** `File > Save` (de `.sesx`, je bewerkbare project).
- **Archief:** `File > Export > File` > **WAV** (de gemasterde versie).
- **Deelversie:** `File > Export > File` > **MP3, 192 kbps CBR stereo**.
- **Voor WhatsApp** (max 16 MB): maak een aparte MP3 op **128 kbps**.

### Stap 5 - Publiceren (in deze repo)

1. Upload de MP3 naar **Google Drive** > rechtsklik > Delen > **Iedereen met de link (Viewer)**.
2. Kopieer de deel-link. De **file-ID** staat tussen `/d/` en `/view`.
3. Werk `feed.xml` bij: voeg een `<item>` toe met de juiste enclosure-URL (de `id` = die
   file-ID), een **unieke** `<guid>` (`alpegg-ep-00X`), titel, beschrijving en `pubDate`
   (de weekdag moet bij de datum kloppen). `length` mag op `"1"` blijven.
4. **Commit + push** `feed.xml`. In de podcast-app de feed verversen.

Cover wijzigen: vervang `cover_image.jpeg` (vierkant, 3000x3000, JPEG). Abonneer-uitleg voor
de familie staat in `luister.html`.

### Vaste waarden om te onthouden

| Onderdeel | Waarde |
|---|---|
| Opname (recorder) | pieken -12 tot -6 dB |
| Essential Sound | Reduce Noise/Rumble ~5 (laag houden) |
| Mixdown-WAV | 48 kHz, stereo, 32-bit float |
| Match Loudness | -16 LUFS, -1 dBTP, limiting aan |
| MP3 | 192 kbps (128 voor WhatsApp) |
| Audio Hardware | Windows Sound (WASAPI) |
