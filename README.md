# Terminalize - Userscript

Turn every website into a retro terminal vibe. Terminalize applies a monospace font across the page, animates text with a subtle typewriter effect, and sneaks in a Matrix-style rain easter egg when you type "hacking" into inputs.

- Script file: `terminalize.user.js`
- Live demo (no install needed): open `demo-website/index.html`
- Greasy Fork page: https://greasyfork.org/en/scripts/540217-terminalize

## Features

- Monospace everywhere: Sets `Courier New, Courier, monospace` for most elements.
- Typewriter effect: Gradually reveals text in paragraphs, headings, simple spans, list items, and plain links.
- Smart skipping: Leaves interactive/nested content alone (links with images, list items with forms, etc.).
- Dynamic pages supported: Re-applies automatically via `MutationObserver` when content changes.
- Matrix rain easter egg: Type "hacking" in any input/textarea to trigger a green character rain.

## Install via Greasy Fork

1. Install a userscript manager (pick one):
   - Tampermonkey (Chrome, Edge, Safari)
   - Violentmonkey (Chrome, Edge, Firefox)
   - Greasemonkey (Firefox)
2. Visit the Terminalize page on Greasy Fork: https://greasyfork.org/en/scripts/540217-terminalize
3. Click the "Install" button. Your userscript manager will open a confirmation tab.
4. Confirm installation in the manager. That's it - visit any site to see the effect.

Tip: Use the userscript manager's toolbar button to quickly disable/enable the script per site or globally.

## How It Works (Brief)

- Runs on all sites (`@match *://*.*/*`).
- Applies monospace styling across elements the first time and whenever new DOM nodes appear.
- For eligible text elements, replaces content with a typewriter reveal at a slightly randomized speed for a natural feel.
- Listens to input events; if the value contains "hacking", it spawns animated green letters that fall like "Matrix rain".

## Permissions and Safety

- Grants: `@grant none` - the script does not request privileged APIs.
- Dependency: `@require https://code.jquery.com/jquery/3.6.0.min.js` (loaded from the official jQuery CDN).
- Updates: Auto-updates via Greasy Fork (`@updateURL`/`@downloadURL` are set).

Because the script matches all websites, you may want to exclude specific domains you frequently use for work. See "Disable or Scope It" below.

## Disable or Scope It

If a site doesn't play nicely, you can:

- Temporarily toggle it off: Click your userscript manager's icon and disable Terminalize on that tab/site.
- Exclude a domain permanently:
  - Tampermonkey: Dashboard → Terminalize → Settings → "Excluded pages" → add the domain (e.g., `https://mail.example.com/*`).
  - Violentmonkey/Greasemonkey: Similar per-script exclude controls are available in the script settings.

## Editing and Development

- Main script: `terminalize.user.js`
- To tweak behavior (e.g., speed), adjust the `setTimeout` delay inside the `typeChar()` function.
- To test locally in a manager, create a new script in your userscript manager, paste the contents of `terminalize.user.js`, and save. Alternatively, install from the Greasy Fork page while you iterate.

## Known Limitations

- Very dynamic apps may occasionally re-render text being animated; the script re-applies, but some flicker can occur.
- Sites with strict CSP might block external dependencies in some contexts; installation via Greasy Fork with a standard userscript manager typically works fine.

## License

MIT - see the header in `terminalize.user.js`.

## Credits

- Author: BluePhi09
- Thanks to the userscript community and the jQuery team.

---
If you have feedback or ideas, feel free to open an issue or propose changes.
