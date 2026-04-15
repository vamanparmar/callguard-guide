# 📱 Phone Call Forwarding — Security Awareness Guide

![Educational](https://img.shields.io/badge/Purpose-Educational%20Only-blue?style=flat-square)
![GSM Standard](https://img.shields.io/badge/Standard-GSM%20USSD-green?style=flat-square)
![License](https://img.shields.io/badge/License-MIT-yellow?style=flat-square)
![Contributions Welcome](https://img.shields.io/badge/Contributions-Welcome-brightgreen?style=flat-square)

> **Disclaimer:** This guide is strictly for **educational and personal security purposes**. The information provided here is intended to help you **protect your own device**. Unauthorized access to another person's phone or configuring settings on someone else's device without their explicit consent is **illegal** under cybercrime and privacy laws in most countries.
> **Disclaimer:** This guide is strictly for **educational and personal security purposes**. The information provided here is intended to help you secure **your own line and devices**. Unauthorized access to another person's phone or account without explicit consent may violate cybercrime and privacy laws.

---

## 📖 Table of Contents

- [What is Call Forwarding?](#what-is-call-forwarding)
- [How Call Forwarding Works](#how-call-forwarding-works)
- [Quick Reference — All Codes](#quick-reference--all-codes)
- [Types of Call Forwarding](#types-of-call-forwarding)
- [How to Check If Your Calls Are Being Forwarded](#how-to-check-if-your-calls-are-being-forwarded)
- [Understanding the Results](#understanding-the-results)
- [How to Disable Call Forwarding](#how-to-disable-call-forwarding)
- [Android vs iOS — Important Differences](#android-vs-ios--important-differences)
- [Common Carrier Voicemail Numbers (India)](#common-carrier-voicemail-numbers-india)
- [When to Contact Your Carrier](#when-to-contact-your-carrier)
- [Final Security Tips](#final-security-tips)
- [Contributing](#contributing)
- [Why this guide exists](#-why-this-guide-exists)
- [Who this is for](#-who-this-is-for)
- [What is call forwarding?](#-what-is-call-forwarding)
- [How call forwarding works](#-how-call-forwarding-works)
- [Quick reference — check and cancel codes](#-quick-reference--check-and-cancel-codes)
- [Types of call forwarding](#-types-of-call-forwarding)
- [Step-by-step: check your line in 2 minutes](#-step-by-step-check-your-line-in-2-minutes)
- [How to read USSD results](#-how-to-read-ussd-results)
- [How to disable forwarding safely](#-how-to-disable-forwarding-safely)
- [Android vs iOS differences](#-android-vs-ios-differences)
- [Troubleshooting guide](#-troubleshooting-guide)
- [When to contact your carrier](#-when-to-contact-your-carrier)
- [India voicemail quick list (example)](#-india-voicemail-quick-list-example)
- [Hardening checklist](#-hardening-checklist)
- [FAQ](#-faq)
- [Contributing](#-contributing)
- [Additional resources](#-additional-resources)

---

## 📡 What is Call Forwarding?
## 🎯 Why this guide exists

Call forwarding is a **legitimate telecom feature** that redirects incoming calls from your number to another number. While useful in valid scenarios (e.g., forwarding to voicemail), it can also be **misconfigured or abused** if someone gains physical access to your device.
Call forwarding is useful, but it is also one of the most commonly misunderstood telecom settings. This README helps you:

Understanding how to detect and remove unwanted call forwarding is an important part of **mobile security hygiene**.
- Understand what each forwarding mode does.
- Detect unexpected forwarding quickly.
- Disable forwarding with confidence.
- Escalate correctly if a carrier-side issue is suspected.

---

## 🔄 How Call Forwarding Works
## 👥 Who this is for

### Normal Call Flow
```
- Everyday users who want a fast security check.
- People who recently shared, repaired, or reset their phone.
- Anyone investigating missed calls, unexplained voicemail behavior, or suspicious account activity.

---

## 📡 What is call forwarding?

Call forwarding redirects incoming calls from your primary number to a different destination (usually voicemail, another line, or a virtual number).

It is normally legitimate, but if changed without your knowledge, it can cause:

- Missed calls you never see.
- Privacy risks (someone else receiving your calls).
- Social-engineering opportunities against your contacts.

---

## 🔄 How call forwarding works

### Normal flow

```text
Caller ──────────────────────────► Your Phone 📱
                                    (Rings normally)
```

### With Unwanted Call Forwarding Active
```
Caller ──────► Network Tower 📶 ──► Forwarded Number ☎️
                                    (Your phone never rings)
### Forwarded flow

```text
Caller ──────► Carrier Network 📶 ──► Forwarded Number ☎️
                                    (Your phone may not ring)
```

When call forwarding is active, incoming calls are silently redirected **before they even reach your device** — which means you may never know a call came in.
Because forwarding is often configured at the carrier/network level, calls can be rerouted before your handset receives them.

---

## ⚡ Quick Reference — All Codes
## ⚡ Quick reference — check and cancel codes

A one-stop cheat sheet for all check and cancel codes:
> Enter each code in your dialer and press **Call**.

| Action | Unconditional | Unreachable | Busy |
|--------|--------------|-------------|------|
| Action | Unconditional | Unreachable / No signal | Busy |
|--------|---------------|--------------------------|------|
| **Check** | `*#21#` | `*#62#` | `*#67#` |
| **Cancel** | `##21#` | `##62#` | `##67#` |

> After entering any code, press the **Call/Dial** button (green icon) if the result does not appear automatically.

---

## 🔀 Types of Call Forwarding
## 🔀 Types of call forwarding

| Type | Description | Check Code | Cancel Code |
|------|-------------|------------|-------------|
| **Unconditional** | All calls forwarded regardless of phone status | `*#21#` | `##21#` |
| **Unreachable / No-Answer** | Calls forwarded when phone is off or out of network | `*#62#` | `##62#` |
| **Busy** | Calls forwarded when you are already on another call | `*#67#` | `##67#` |
| Type | What it means | Check | Cancel |
|------|----------------|-------|--------|
| **Unconditional** | Every incoming call is forwarded immediately | `*#21#` | `##21#` |
| **Unreachable / No-answer** | Calls forward when phone is off, unreachable, or no signal | `*#62#` | `##62#` |
| **Busy** | Calls forward while you're already on another call | `*#67#` | `##67#` |

---

## 🔍 How to Check If Your Calls Are Being Forwarded
## ✅ Step-by-step: check your line in 2 minutes

Open your phone's **dial pad** and enter the following codes one at a time.

### ① Check Unconditional Forwarding
```
*#21#
```
Checks if **all calls** are being forwarded at all times.
1. Open your dial pad.
2. Dial `*#21#` and note the result.
3. Dial `*#62#` and note the result.
4. Dial `*#67#` and note the result.
5. If any unknown number appears, cancel with matching `##` code.
6. Re-run all `*#` checks to confirm the final state.

### ② Check Unreachable / No-Answer Forwarding
```
*#62#
```
Checks if calls are forwarded when your phone is **switched off or has no signal**.

### ③ Check Busy Call Forwarding
```
*#67#
```
Checks if calls are forwarded when you are **already on a call**.
Tip: Save screenshots of results before/after changes for records when speaking with carrier support.

---

## 📊 Understanding the Results
## 📊 How to read USSD results

### ✅ Safe — No Forwarding Active
### Safe example

```text
Voice:    Not forwarded ✅
Data:     Not forwarded ✅
Fax:      Not forwarded ✅
```
Voice:    Not Forwarded  ✅
Messages: Not Forwarded  ✅
Fax:      Not Forwarded  ✅

### Potentially risky example

```text
Voice forwarded to: +<country_code><number> ⚠️
```

This means no call forwarding is currently configured on your line. You are safe.
Forwarding can still be legitimate (e.g., voicemail), but verify every unfamiliar number.

---

### ⚠️ Forwarding Detected
## 🛑 How to disable forwarding safely

Run all three cancel codes:

```text
##21#
##62#
##67#
```
Voice Forwarded to: +91XXXXXXXXXX  ⚠️

Then immediately verify with:

```text
*#21#
*#62#
*#67#
```

This means your calls are being redirected. This could be:
If a rule reappears after cancellation, treat it as a carrier/account issue and escalate.

- ✅ A **carrier voicemail number** (often legitimate — see carrier list below)
- ✅ A **number you set yourself** and forgot about
- ❌ In rare cases, **unauthorized forwarding** set without your knowledge
---

Do not panic — simply follow the steps in the next section to disable it.
## 📱 Android vs iOS differences

| Feature | Android | iPhone (iOS) |
|--------|---------|---------------|
| USSD response behavior | Usually immediate popup | Carrier dependent; may vary |
| Reliable manual path | Dialer USSD + call settings | **Settings → Phone → Call Forwarding** |
| Recommendation | Use both USSD + settings for confirmation | Use Settings view first, then test with real call |

---

## 🛑 How to Disable Call Forwarding
## 🧰 Troubleshooting guide

Open your **dial pad**, enter the code, and press **Call**.
### “Code failed” / “MMI invalid”
- Retry with strong signal and active SIM.
- Remove spaces or extra symbols.
- Some MVNOs/roaming contexts block specific USSD queries.

```
##21#   →  Cancels ALL unconditional call forwarding
##62#   →  Cancels unreachable / no-answer forwarding
##67#   →  Cancels busy call forwarding
```
### “Forwarding turns back on”
- Check if carrier voicemail auto-enables on unreachable/busy states.
- Ask carrier to remove all conditional forwarding and voicemail provisioning temporarily.

After entering each code, re-run the corresponding **check code** to confirm forwarding is disabled.
### “I still miss calls after disabling everything”
- Test with airplane mode off and Wi-Fi calling on/off.
- Verify DND, call blocking apps, and spam filters.
- Place controlled tests from two different networks.

---

## 📱 Android vs iOS — Important Differences
## 📞 When to contact your carrier

| Feature | Android | iPhone (iOS) |
|--------|---------|--------------|
| USSD code popup | ✅ Shows result instantly on screen | ⚠️ May route through carrier instead |
| `*#21#` support | ✅ Fully supported | ⚠️ Partially — depends on carrier |
| Recommended alternative | Dial pad codes | **Settings → Phone → Call Forwarding** |
Contact support when:

- Cancel codes report success but forwarding remains active.
- Unknown destination numbers persist.
- Forwarding reactivates repeatedly.
- You suspect SIM swap, SIM cloning, or account compromise.

**iPhone Users:** If USSD codes don't work as expected, go to:
> **Settings → Phone → Call Forwarding**
When contacting support, request:

This will show you exactly whether forwarding is on or off, with no need for dial codes.
1. Full forwarding status for voice service.
2. Timestamped change history (if available).
3. Removal/reset of all CFU/CFNR/CFB rules.
4. Account PIN reset and SIM revalidation.

---

## 📋 Common Carrier Voicemail Numbers (India)
## 🇮🇳 India voicemail quick list (example)

If you see a forwarding number you don't recognize, it might simply be your carrier's default voicemail service — which is completely normal.
> This list is illustrative and may change. Always verify with carrier websites/apps.

| Carrier | Voicemail Number |
|---------|-----------------|
| **Jio** | +91-40-4121-0000 or 1800-889-9999 |
| Carrier | Common voicemail number |
|---------|--------------------------|
| **Jio** | +91-40-4121-0000 / 1800-889-9999 |
| **Airtel** | +91-98-1800-0543 |
| **Vi (Vodafone Idea)** | +91-98-2009-8200 |
| **BSNL** | 56789 |

> If the forwarded number matches your carrier's voicemail, there is no cause for concern. You can still disable it using `##21#` if you prefer.

---

## 📞 When to Contact Your Carrier
## 🔐 Hardening checklist

In some situations, dial codes alone may not be enough. Contact your carrier's customer support if:
- [ ] Set a strong screen lock (PIN/biometric).
- [ ] Lock SIM with a SIM PIN.
- [ ] Enable account-level telecom PIN where available.
- [ ] Review forwarding settings monthly.
- [ ] Re-check after travel, eSIM migration, or device repair.
- [ ] Use only official carrier apps/portals for line management.

- `##21#` does **not** successfully cancel forwarding
- The forwarding number is **unrecognized** and does not match any voicemail service
- Forwarding **reactivates** after you cancel it
- You suspect **SIM cloning** or **account-level tampering**
---

| Carrier | Support Number |
|---------|---------------|
| Jio | 199 |
| Airtel | 121 |
| Vi | 199 |
| BSNL | 1800-180-1503 |
## ❓ FAQ

---
**Q: Is all forwarding suspicious?**  
No. Voicemail and business routing are common legitimate uses.

**Q: Can malware enable forwarding?**  
In many cases, unauthorized changes require account/device access rather than advanced malware.

## 🔐 Final Security Tips
**Q: Do these codes work worldwide?**  
GSM/MMI behavior is carrier-dependent. Codes are common but not universal.

1. **Never dial unknown `*` or `#` codes** from strangers — USSD codes can modify your phone settings instantly without confirmation.
2. **Never share OTPs** — Not with anyone, not even callers claiming to be your bank or telecom provider.
3. **Lock your phone** — Physical access is the most common way call forwarding gets misconfigured. A strong PIN or biometric lock is your first line of defense.
4. **Run a security check regularly** — Make it a habit to dial `*#21#` every few weeks to verify your settings.
5. **Check after repairs** — Always verify your call forwarding settings after handing your phone to a repair shop.
6. **Use your carrier's official app** — Most carriers (Jio, Airtel, Vi) have apps where you can review and manage call settings securely.
**Q: Should I disable voicemail for security?**  
Not always necessary. Safer approach: verify destination, secure carrier account, and monitor changes.

---

## 🤝 Contributing

Contributions are welcome! If you have:
- Carrier voicemail numbers for other countries
- Carrier-specific USSD code variations
- iOS/Android version-specific behavior notes
Contributions are welcome. Helpful additions:

Please open a **Pull Request** or file an **Issue**. Let's make this guide more comprehensive for everyone.
- Carrier-specific behavior by country/region.
- Verified voicemail destination references.
- iOS/Android version differences and screenshots.
- Better troubleshooting flows for MVNO users.

Open a Pull Request or Issue with reproducible details (carrier, country, device, OS version, and observed output).

---

## 📚 Additional Resources
## 📚 Additional resources

- [GSMA — Understanding USSD](https://www.gsma.com/)
- [TRAI (India) — Consumer Information](https://www.trai.gov.in/)
- Your mobile carrier's official support page
- [GSMA](https://www.gsma.com/)
- [TRAI (India)](https://www.trai.gov.in/)
- Your carrier's official support portal

---

<div align="center">

### 🛡️ Your Phone. Your Calls. Your Privacy.

*In a world where your silence can be stolen,*
*awareness is the most powerful weapon you own.*
*Stay curious. Stay cautious. Stay in control.*

**— Because security isn't a feature. It's a right.**
Security improves when checks become habits.

</div>
