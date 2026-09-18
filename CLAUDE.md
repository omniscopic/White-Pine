# White Pine Homecoming — repo guide for Claude Code

A one-page concept site for a wooden surfboard residency hosted at the Art Complex
Museum (ACM) in Duxbury, Massachusetts. Built by Rich Blundell. Static HTML, no
build step, deployed with GitHub Pages.

Live: https://omniscopic.github.io/White-Pine/ (case sensitive)

## The page's job

Start the conversation with potential partners. The project is at the concept
stage. Nothing here is a commitment.

## Framing rules (from Rich — keep these)

- Regional, not Duxbury-specific. The theme is love and appreciation for one's
  home habitat. New England is the region; Duxbury appears only as Rich's roots.
- The ACM is the host and has expressed enthusiasm. Everyone else (Levitate Music
  Festival and its emerging artists program, a high school wood arts program such
  as Duxbury High School, a white pine source, surf shops) is a *potential* partner.
- Residency details: at the ACM, 1 to 6 months, timed to the 2026–27 school year,
  culminating in a Spring/Summer 2027 exhibition.
- Do not name Scott Woodruff or Stick Figure. The musician board stays generic.
- Do not say or imply the boards will be surfed. No surfing photos or captions.
- Use Rich's language wherever possible. Edit for grammar and clarity only.
- No em dashes in page copy. Short, simple sentences. Warm and plainspoken, no hype.
- No emoji.

## Repo layout

```
index.html   the whole page: markup, CSS in <style>, gallery JS at the bottom
img/         hero and section photos (bridge, quiver, portrait, etc.)
gallery/     gallery photos: name.jpg (full) + name-t.jpg (thumbnail)
```

## Page order

Hero (Powder Point Bridge sunset) · The Idea · Who Could Be In It (partners) ·
Shape of the Residency (where / how long / when / culminates) · The Boards ·
What It Celebrates · Gallery (filter tabs + lightbox) · The Provenance of Rich (bio + "An Earth Story" film) · Closing invitation + links.

## Design tokens (CSS variables on :root)

Colors: cream #F4E8D0 (page), band #EFE0C4, deep brown #3A2818, night #2A1D12,
text #40301F / #5C462E, captions #7A6144, sunset #C6592C, rust #A8431F,
sun #DA8A34, sun core #E7B84D, mustard #D2982E, pine #6E7A31,
creams on dark #F7ECD2 / #F1DBB0 / #EBC77A.

Type (Google Fonts): Yeseva One for display, Bitter for body and italic captions,
Oswald uppercase with letter-spacing for labels.

Motifs: radial-gradient sun disc, the four-color striped divider, and a light
sepia filter on every photo: `sepia(.2) saturate(.94) contrast(1.03)`.
Single light theme by design. Breakpoints at 860px, 720px, 440px.

Derive from these. No new fonts or colors.

## Adding gallery photos

1. Make two JPEGs per photo from the original (fix EXIF rotation first):
   - `gallery/<name>.jpg`   longest side 1800px, quality ~80, progressive
   - `gallery/<name>-t.jpg` longest side 640px, quality ~74
   Use lowercase, hyphenated names. Home habitat photos use the `hh-` prefix.
2. Add a button inside `<div class="ggrid" id="ggrid">`:
   ```html
   <button type="button" data-g="Home Habitat" data-full="gallery/<name>.jpg"
     data-cap="Caption." aria-label="Open photo: Caption.">
     <img src="gallery/<name>-t.jpg" alt="Caption." loading="lazy"></button>
   ```
3. `data-g` must match a filter tab: Home Habitat, From the Tree, The Build,
   The Boards, On Display. To add a group, add a matching tab button in `.gtabs`.
4. Captions: one short line in Rich's voice. Don't name a place unless Rich
   confirmed it.

Photo sources: Rich's "Duxbury Selects" folder on his Desktop, the
omniscopic/woodwaterwaves repo (`uploads/`), and omniscopic/richblundell.com
(`images/`).

## Deploying

Commit and push to `main`. Pages rebuilds in about a minute. If a change doesn't
appear, check the Actions tab for the "pages build and deployment" run, then
hard-refresh.
