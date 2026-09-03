# 🕵️ OhSINT — TryHackMe Writeup

**Room:** OhSINT · **Category:** OSINT · **Difficulty:** 🟢 Easy

## 📌 Overview

I was handed one file: `WindowsXP_1551719014755.jpg`. No name, no context — just a picture.

OhSINT is a beginner-friendly OSINT (Open Source Intelligence) room on TryHackMe. The challenge starts with nothing but a single image and asks you to trace it all the way to a real person's location, online accounts, and even a hidden credential — using only public, freely accessible information.

## 🔍 Step 1: Metadata Extraction

Ran exiftool on the provided image:

`exiftool "WindowsXP_1551719014755.jpg"`

📍 Found GPS coordinates, and more usefully, a Copyright field listing the username `OWoodflint`. This became my pivot point for everything else.



![exiftool output](./images/exiftool-output.png)



## 🐦 Step 2: Social Media

Searched X (Twitter) for @OWoodflint — found an active account with a tweet containing a BSSID he'd carelessly shared.

## 💻 Step 3: GitHub

Same username on GitHub led to a repo (people_finder) with a README confirming he's based in London 🇬🇧, plus a personal email in the project description.

## ✍️ Step 4: WordPress Blog

Found his personal blog via the same username pattern. A post revealed he was currently traveling in New York 🗽.

## 🔐 Step 5: Hidden Credential

Nothing on the rendered WordPress page hinted at a password — but inspecting the raw HTML via DevTools revealed a hidden credential string embedded in the page source.

💡 Biggest lesson of the room: OSINT isn't just what's displayed — it's what's embedded.



![DevTools hidden credential](./images/devtools-hidden-string.png)



## 🛰️ Step 6: WiGLE Roadblock

Tried to resolve the BSSID via WiGLE.net, but its search required a login I didn't have. Cross-referenced through an alternate source instead.

🧩 Tools failing doesn't mean the investigation stops.

## ✅ Key Takeaways

- 🧵 Metadata is often the biggest leak
- 🔗 Usernames are pivot points across platforms
- 👀 Never trust only the rendered page — check the source
- 🔄 Tools fail; adapt and keep going

**🛠️ Tools used:** exiftool · Kali Linux · Chrome DevTools · WiGLE.net · X (Twitter) · GitHub · WordPress. 