# Flamingos Day Finder

A one-page web app that tells Ellis Lower School kindergarten families which day of the 8-day
rotation it is, whether it's a PE uniform day, and what the schedule looks like.

Not an official Ellis School tool. Built by a parent from the school's draft 2026–27 Lower School
day calendar (6/17/2026), the Flamingos (KA) schedule sheet, and the teachers' Seesaw newsletters.
MyEllis, Seesaw, and the classroom teachers are the final word.

## Put it online (about 10 minutes, free)

1. On github.com, click **New repository**. Name it `flamingo-day-finder`, set it to **Public**, and
   create it. Pages only works on public repos for free accounts.
2. On the repo page, click **Add file → Upload files**, drag in everything from this folder
   (`index.html`, `manifest.webmanifest`, `sw.js`, and the three PNG icons), then **Commit changes**.
3. Go to **Settings → Pages**. Under "Build and deployment," set Source to **Deploy from a branch**,
   branch **main**, folder **/ (root)**. Save.
4. Wait a minute, then reload that page. It will show your address, which looks like
   `https://yourname.github.io/flamingo-day-finder/`. That's the link to share with parents.

## Tell parents to install it

On the phone, open the link, then:

- **iPhone (Safari):** Share button → Add to Home Screen.
- **Android (Chrome):** menu → Add to Home screen, or tap the install prompt.

It then opens like an app, with its own icon, and works without a signal.

## Update it later

Edit `index.html` on GitHub (click the file, then the pencil icon) and commit. The page updates in
about a minute.

Two spots you'll touch most often, both near the top of the `<script>` block:

- **`LAB_AS`** — when a Friday newsletter says a LAB day will be run as a specific day, add a line:

  ```js
  const LAB_AS = {
    "2026-09-16": {n:1, why:"Make-up for the half-day first day of school (Sep 1)."},
    "2026-10-07": {n:4, why:"Announced in the Oct 2 newsletter."}
  };
  ```

- **`CAL`** — the day number for every date, taken from the printed calendar. Codes are a number
  (1–8), `L` for a LAB day, `X|reason` for no school, and `S|label` for a special schedule.

**Important:** after any change, open `sw.js` and bump the version, for example `day-finder-v1` to
`day-finder-v2`. Phones that installed the app cache the old files otherwise.

## Known gaps

The draft calendar breaks its own pattern on Oct 26, Apr 26, and around the March musical days, and
gives no day number to Dec 18 or Jun 4. The in-app "How it works" page lists all of these. Confirm
them with the teachers, then correct `CAL`.
