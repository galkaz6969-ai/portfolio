# Gal Kazaz: personal portfolio site

This file gives Claude the full context for this project, so every new session picks up where the last one left off.

## Who I'm working with
- **Gal Kazaz**: a third-year LL.B. student at Netanya Academic College. He is looking for a tech-oriented legal internship starting **March 2028**.
- Gal is **not a programmer**. Talk to him **in Hebrew**, simply, one step at a time. When he has to click something, give the exact button name and ask for a screenshot if he gets stuck.
- Hebrew text about Gal is always **masculine** (סטודנט, not סטודנטית).
- His name in Hebrew is spelled **גל קזז** (not קזאז).
- Gal does not edit code himself. He asks Claude for a change, Claude commits and pushes to `main`, and Vercel redeploys automatically.

## How the site works
- **GitHub repository:** `galkaz6969-ai/portfolio`. Branch `main` is the live site.
- **Hosting:** Vercel (Hobby plan, free), connected to this repo. Every push to `main` deploys within about a minute.
- The live address is in the Vercel dashboard under the project, then Domains (expected `gal-kazaz.vercel.app`).
- Claude's network in the cloud environment cannot open vercel.app or vercel.com, so after a push, ask Gal to refresh the site (Cmd/Ctrl+Shift+R) and check it.

## Files
| File | What it is |
|---|---|
| `index.html` | The whole site, one self-contained file. The photo and logos are embedded inside it as base64 data. |
| `Gal-Kazaz-CV.pdf` | The CV behind the "Download CV" and "CV" buttons. |
| `source/cv.html` | Source of the CV. To change the CV: edit this file, render it to PDF with Playwright (A4, must stay one page), and replace `Gal-Kazaz-CV.pdf`. |
| `source/photo.jpg` | Gal's portrait, already cropped square (640x640). |
| `source/logos/` | Logo tiles: `iaf.png` (Israeli Air Force), `mol.png` (Ministry of Labor emblem), `arc.png` (American Red Cross). |

## Site structure (`index.html`)
- Two full copies of the content: `<div class="lang-en">` (default) and `<div class="lang-he" dir="rtl">` (hidden). The EN/HE button in the header switches between them and remembers the choice.
- **Any text change must be made in both languages.**
- Browser auto-translate is turned off (`translate="no"` and `<meta name="google" content="notranslate">`), because Google Translate wrote Gal as female.
- Sections, in order: Hero (photo plus a Snapshot card), Highlights (rows with icons that link down the page), Legal experience & education, Projects, Professional experience (with Military and Volunteering subsections), Skills & certifications, Contact.
- The design follows a reference site Gal liked (Michael Mutter's portfolio on Vercel): a sticky top bar, a blue gradient accent, rounded cards. Fonts are Plus Jakarta Sans for English and Heebo for Hebrew.

## Decisions already made (don't re-ask)
- **Gal's Hebrew CV (Word file) is the source of truth for facts.** The English CV, the English site and the Hebrew site must all match it (same employers, roles, dates, sections). Translation wording may differ, facts may not.
- 2021–2025 hotels: Isrotel, The Ritz-Carlton Herzliya and other hotels in central Israel (senior lifeguard and pool team manager, seasonal). Holmes Place (2026–): pool lifeguard, student position. Tamarack Camps sits under Volunteering, as in the Hebrew CV.
- The Hebrew site text follows the wording of Gal's Hebrew CV (Word file, kept by Gal): for example "משתתף בקליניקה לפרקטיקה וסיוע משפטי" and "מפעיל מכלול בחיל האוויר". Job facts (employers, titles) still match the English site.
- The clinic role is **"Student Clinician, Legal Clinic"** (Hebrew: סטודנט בקליניקה המשפטית), described as work **under attorney supervision**. Do not use "Legal Advisor" or "יועץ משפטי": in Israel that wording implies a law license.
- The hero and the Snapshot card stay general (management, lifeguarding, sales). Specific hotels are mentioned only in the Experience section.
- The phone number stays on the site.
- The site uses the official logos of the IAF, the Ministry of Labor and the Red Cross. Gal chose this after he was told these symbols are legally protected.
- There is no GitHub link in the top bar yet. Add one once Gal has real projects on GitHub.

## Open items / next steps
1. **LinkedIn:** add the site link to Gal's profile (Contact info, then Website; also a Featured item). Walk him through it.
2. **More logos (optional):** Gal can send screenshots of the Netanya Academic College, Holmes Place, Ritz-Carlton, U-Boat, Tamarack Camps and Taglit logos. Entries take a logo with `class="entry with-logo"` plus `<span class="logo"><img ...></span>`; see the IAF entry.
3. **Projects:** Gal plans AI projects. For each one: create a new GitHub repo, build it with Claude, then replace the "More projects coming soon" card with a real project card (EN and HE), and add GitHub to the top bar (`github.com/galkaz6969-ai`).
4. **GitHub username:** `galkaz6969-ai` looks less professional. A rename (for example to `gal-kazaz`) was suggested, but nothing has been decided.
5. A real photo of a car LED install would make a strong image for the LED project card.

## How to push (for Claude)
```
git add -A
git commit -m "..."
git -c push.negotiate=true push origin main
```
Commit as the repo owner: `-c user.name="galkaz6969-ai" -c user.email="galkaz6969-ai@users.noreply.github.com"`.
