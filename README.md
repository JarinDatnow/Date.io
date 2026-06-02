# Date.io
Date.io 💌
An over-the-top, single-page "will you go out with me?" experience — built as a joke that got out of hand (in a good way). It walks one person through a whole flirty journey: a fake compatibility scan, a question you can't actually say no to, a vibe picker that talks back, an auto-generated date itinerary, and a locked-in confirmation that saves their answer.
🔗 Live: https://jarindatnow.github.io/Date.io/

What it does
The page runs as a guided, multi-screen flow with a progress bar tying it together:

Compatibility intro — a mock "calculating compatibility" loader that counts up to 99%.
The question — a "Yes / No" prompt where the No button refuses to cooperate (it grows the Yes button and cycles through panic text until it gives up and says yes anyway).
Vibe picker — choose the date type (food, movie, hiking, coffee, beach, surprise); each choice fires a custom reaction.
Calendar — pick a day from a working date picker (past dates disabled).
Itinerary — auto-generates a timed, tongue-in-cheek plan based on the chosen vibe.
Confirmation — recap card, confetti, sound, and a text box to leave a one-liner.

Responses (vibe, chosen day, how many times "No" was tapped, and the one-liner) are saved to a connected Google Sheet.

Built with

HTML / CSS / vanilla JavaScript — no framework, single file, zero dependencies
Web Audio API — all sound effects generated in code (no audio files)
CSS animations — floating hearts, confetti bursts, screen transitions, animated progress bar
Google Apps Script — lightweight serverless endpoint that writes responses into a Google Sheet
GitHub Pages — static hosting over HTTPS


How the saving works
The page is fully static, so it has no backend of its own. The final step sends a POST request to a Google Apps Script Web App URL, which appends a row to a Google Sheet:
TimestampVibeDayNoClicksOneLiner
To wire up your own copy:

Create a Google Sheet with the headers above.
In Extensions → Apps Script, add a doPost handler that parses the JSON body and calls sheet.appendRow(...).
Deploy → New deployment → Web app, set access to Anyone, and copy the /exec URL.
Paste that URL into the SAVE_URL constant near the top of the <script> block in index.html.

The request uses no-cors, so the page can't read the response — test by submitting once and checking the sheet for a new row.

Run it locally
It's a single file — just open index.html in any browser. No build step, no install.

Notes
A for-fun project to practice front-end flow, animation, and wiring a static page to a simple data store. Built to be sent to one person. 🌹
