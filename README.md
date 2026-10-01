# scamshield
Private, in-browser scam message checker. Paste a text or email to see a risk score and the exact words that gave it away. Naive Bayes classifier plus tactic detection, runs offline.

Built for the ML Empowerment Build Challenge 3.0.

Why

Scam messages cost people billions every year, and older adults and first-time phone users are hit hardest. Most tools just say "spam" without saying why, so people never learn to spot the next scam. ScamShield explains every result, so each check also teaches.

What it does
Gives a risk score from 0 to 100 and a plain verdict: Looks safe, Be careful, or Likely a scam
Highlights the words in the message that pushed the score toward "scam"
Detects six manipulation tactics: fake urgency, money or gift card requests, impersonating a trusted organization, secrecy, suspicious links, and requests for codes or passwords
Gives plain-language next steps based on the tactics found
Runs 100% in the browser: no account, no cost, and no message is ever uploaded
How it works

The final score blends two parts: 60% classifier probability + 40% tactic evidence.

Naive Bayes classifier, written from scratch in JavaScript. It trains in your browser when the page loads on a small set of labeled scam and normal messages. It counts word frequencies per class with Laplace smoothing and sums per-word log-odds for a new message. Words with a large positive contribution are the ones highlighted in red.
Tactic detector. Regex rules look for the six tactics listed above.

Blending the two keeps results sensible on wording the small training set has not seen.

Run it locally

There is no build step and no dependencies. Open index.html in a browser, or serve the folder:

bash
npx serve .
Deploy

It is a static site. Import the repo into Vercel with the framework preset set to Other and no build command.

Tech

JavaScript, HTML, CSS. No frameworks, no external APIs.

Limitations
The classifier is trained on a small hand-written dataset, so it will miss some scams and may flag some normal messages. Treat the score as a prompt to be careful, not a verdict.
English only for now.
Roadmap
Train on a larger multilingual dataset (for example the public SMS Spam Collection) and report measured accuracy
Browser extension that checks messages in place
Family mode that alerts a trusted contact on high-risk messages
Voicemail and screenshot input
Credits

Built by Varun
