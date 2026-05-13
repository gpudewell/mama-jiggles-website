# Editing the Mama Jiggles Website From Your Phone

This is for **Mama Jiggles (the business owner)** to update her own website using the Claude app.

You don't need to know how to code. You'll have a normal chat with Claude, tell it what you want changed, and Claude will make a "proposed change" (called a Pull Request, or PR) that Greg approves with one tap. After that, the live website updates by itself in about 30 seconds.

---

## One-time setup

You only do this once.

1. **Open Claude on your phone** — either the Claude app or claude.ai in your phone's browser. Log in with the account you created.
2. **Connect GitHub.** Tap your profile (top-left or top-right depending on the version) → **Settings** → **Connectors** → find **GitHub** and tap **Connect**. Sign in with your GitHub account when it asks, and approve access.
3. **Confirm Greg has added you** as a collaborator on the `mama-jiggles-website` repo. (He'll get a notification when you accept the invite via email or in GitHub.)

That's it. You're set up.

---

## How to make an edit

Open a new chat with Claude and paste this **starter message**, filling in the bracketed part with what you actually want to change:

> Hi Claude — I'd like to update the Mama Jiggles website. The repo is **gpudewell/mama-jiggles-website**. Please read the CLAUDE.md file in the repo first, then [describe your change in plain English]. Make the change on a new branch and open a Pull Request — don't push to main directly.

**Examples of how to fill that in:**

- *"...add a new flavor called 'Watermelon Wonder' — it's vodka and watermelon."*
- *"...update the tagline on the hero. Change 'Hand-crafted Jell-O shots' to 'Small-batch Jell-O shots, made fresh weekly.'"*
- *"...change the order email from `mamajigglesgelatin@gmail.com` to `orders@mamajiggles.com`."*
- *"...replace the entire flavor list with: 1) Pineapple Upside-Down, rum & pineapple, 2) Mojito Madness, rum & mint, 3) ..."*
- *"...add an Instagram link in the footer. The handle is @mamajiggles."*

Claude will read the project, confirm what it's about to do, make the change, and tell you the PR is ready. Greg gets the notification, reviews it on his phone, and merges. Done.

---

## What Claude can and can't do

| Claude can change | Claude won't change without asking Greg |
| :---------------- | :--------------------------------------- |
| Flavor names and descriptions | The logo, fonts, or brand colors |
| The tagline and "Who's Mama?" copy | How the site is built or deployed |
| The order email and pre-filled order template | The 21+ age-gate (legally required) |
| The 3 ordering steps text | The page layout structure |
| Footer text, copyright, social links | Anything in the `public/` folder (logos, images) |

If you want something on the "won't change" side updated, just ask Greg directly.

---

## When something feels off

- **"Claude says it can't see the repo."** → Re-check the GitHub connector under Settings → Connectors. Make sure you accepted Greg's collaborator invite (check your email or github.com → top-right → notifications).
- **"I made an edit but the website didn't update."** → The change is in a Pull Request waiting for Greg to merge it. Text him: "Hey, I have a website update ready — can you merge the PR?"
- **"Claude wrote something I didn't ask for."** → Tell it what's wrong. "Actually, change the flavor note back to what it was — I just want the name updated, not the description." Claude will fix the PR.
- **"I want to undo something that already went live."** → Open a new chat and say: "Please revert the most recent change to the website." Claude will open a new PR that undoes it.

---

## A tip

Before merging, you can preview the change yourself by opening the **PR on GitHub** and tapping **Files changed** — you'll see the exact text difference. If you want a live preview of the actual rendered page before going live, ask Greg to set up "PR preview deploys" in Cloudflare (it's a one-time setup that gives every PR its own preview URL).
