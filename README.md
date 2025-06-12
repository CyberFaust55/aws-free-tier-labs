# aws-free-tier-labs
Labs and projects on AWS Free Tier using Terraform, CI/CD, Docker, and more.
# cybersandbox.pl — Static Website Hosted on AWS S3 + Route 53

## 🔧 Project Overview
This repository documents the setup of `cybersandbox.pl` — a simple static webpage hosted on AWS S3, using Amazon Route 53 for domain resolution.

---

## ✅ What was done (12 June 2025)

### ☁️ AWS S3
- Created a public S3 bucket:
  - Bucket name: `www.cybersandbox.pl`
  - Uploaded file: `index.html`
- Enabled **static website hosting**
- Made bucket public using:
  - Block public access settings: `OFF`
  - Bucket policy for `s3:GetObject` on `arn:aws:s3:::www.cybersandbox.pl/*`

### 🌐 Route 53
- Created a **Public Hosted Zone** for `cybersandbox.pl`
- Created record sets:
  - `A` record for `cybersandbox.pl` → alias to `s3-website-us-east-1.amazonaws.com`
  - `A` record for `www.cybersandbox.pl` → alias to same S3 endpoint
- Set routing policy: `Simple routing`
- Confirmed propagation with `nslookup` via Google DNS (`8.8.8.8`)

### 🌍 Domain DNS Delegation (cyberfolks.pl)
- Delegated `cybersandbox.pl` to AWS Route 53:
  - Used the 4 NS records provided by Route 53
  - Removed parking / forwarding settings from cyber_Folks panel
  - Ensured propagation worked (took ~30–60 mins)

---

## 🔗 Live demo (in progress)
🔸 https://www.cybersandbox.pl  
🔸 https://www.cybersandbox.pl/index.html

---

## 📌 To do next
- Add SSL (via CloudFront or ACM)
- Create non-www redirect (`cybersandbox.pl` → `www.cybersandbox.pl`)
- Add contact or CV page
- Optional: set up CI/CD using GitHub Actions

---

## 💬 Notes
- Remember to **invalidate browser & system cache** when testing DNS changes.
- DNS propagation might take time depending on resolver TTL and local DNS cache.

---

## 🧠 Author
Adam Maślany – `CyberFaust55`

