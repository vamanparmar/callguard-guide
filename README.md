# 📱 Phone Call Forwarding — Security Awareness Guide

![Educational](https://img.shields.io/badge/Purpose-Educational%20Only-blue?style=flat-square)
![GSM Standard](https://img.shields.io/badge/Standard-GSM%20USSD-green?style=flat-square)
![License](https://img.shields.io/badge/License-MIT-yellow?style=flat-square)
![Contributions Welcome](https://img.shields.io/badge/Contributions-Welcome-brightgreen?style=flat-square)

> **Disclaimer:** This guide is strictly for **educational and personal security purposes**. The information provided here is intended to help you **protect your own device**. Unauthorized access to another person's phone or configuring settings on someone else's device without their explicit consent is **illegal** under cybercrime and privacy laws in most countries.

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

---

## 📡 What is Call Forwarding?

Call forwarding is a **legitimate telecom feature** that redirects incoming calls from your number to another number. While useful in valid scenarios (e.g., forwarding to voicemail), it can also be **misconfigured or abused** if someone gains physical access to your device.

Understanding how to detect and remove unwanted call forwarding is an important part of **mobile security hygiene**.

---

## 🔄 How Call Forwarding Works

### Normal Call Flow
```
Caller ──────────────────────────► Your Phone 📱
                                    (Rings normally)
```

### With Unwanted Call Forwarding Active
```
Caller ──────► Network Tower 📶 ──► Forwarded Number ☎️
                                    (Your phone never rings)
```

When call forwarding is active, incoming calls are silently redirected **before they even reach your device** — which means you may never know a call came in.

---

## ⚡ Quick Reference — All Codes

A one-stop cheat sheet for all check and cancel codes:

| Action | Unconditional | Unreachable | Busy |
|--------|--------------|-------------|------|
| **Check** | `*#21#` | `*#62#` | `*#67#` |
| **Cancel** | `##21#` | `##62#` | `##67#` |

> After entering any code, press the **Call/Dial** button (green icon) if the result does not appear automatically.

---

## 🔀 Types of Call Forwarding

| Type | Description | Check Code | Cancel Code |
|------|-------------|------------|-------------|
| **Unconditional** | All calls forwarded regardless of phone status | `*#21#` | `##21#` |
| **Unreachable / No-Answer** | Calls forwarded when phone is off or out of network | `*#62#` | `##62#` |
| **Busy** | Calls forwarded when you are already on another call | `*#67#` | `##67#` |

---

## 🔍 How to Check If Your Calls Are Being Forwarded

Open your phone's **dial pad** and enter the following codes one at a time.

### ① Check Unconditional Forwarding
```
*#21#
```
Checks if **all calls** are being forwarded at all times.

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

---

## 📊 Understanding the Results

### ✅ Safe — No Forwarding Active

```
Voice:    Not Forwarded  ✅
Messages: Not Forwarded  ✅
Fax:      Not Forwarded  ✅
```

This means no call forwarding is currently configured on your line. You are safe.

---

### ⚠️ Forwarding Detected

```
Voice Forwarded to: +91XXXXXXXXXX  ⚠️
```

This means your calls are being redirected. This could be:

- ✅ A **carrier voicemail number** (often legitimate — see carrier list below)
- ✅ A **number you set yourself** and forgot about
- ❌ In rare cases, **unauthorized forwarding** set without your knowledge

Do not panic — simply follow the steps in the next section to disable it.

---

## 🛑 How to Disable Call Forwarding

Open your **dial pad**, enter the code, and press **Call**.

```
##21#   →  Cancels ALL unconditional call forwarding
##62#   →  Cancels unreachable / no-answer forwarding
##67#   →  Cancels busy call forwarding
```

After entering each code, re-run the corresponding **check code** to confirm forwarding is disabled.

---

## 📱 Android vs iOS — Important Differences

| Feature | Android | iPhone (iOS) |
|--------|---------|--------------|
| USSD code popup | ✅ Shows result instantly on screen | ⚠️ May route through carrier instead |
| `*#21#` support | ✅ Fully supported | ⚠️ Partially — depends on carrier |
| Recommended alternative | Dial pad codes | **Settings → Phone → Call Forwarding** |

**iPhone Users:** If USSD codes don't work as expected, go to:
> **Settings → Phone → Call Forwarding**

This will show you exactly whether forwarding is on or off, with no need for dial codes.

---

## 📋 Common Carrier Voicemail Numbers (India)

If you see a forwarding number you don't recognize, it might simply be your carrier's default voicemail service — which is completely normal.

| Carrier | Voicemail Number |
|---------|-----------------|
| **Jio** | +91-40-4121-0000 or 1800-889-9999 |
| **Airtel** | +91-98-1800-0543 |
| **Vi (Vodafone Idea)** | +91-98-2009-8200 |
| **BSNL** | 56789 |

> If the forwarded number matches your carrier's voicemail, there is no cause for concern. You can still disable it using `##21#` if you prefer.

---

## 📞 When to Contact Your Carrier

In some situations, dial codes alone may not be enough. Contact your carrier's customer support if:

- `##21#` does **not** successfully cancel forwarding
- The forwarding number is **unrecognized** and does not match any voicemail service
- Forwarding **reactivates** after you cancel it
- You suspect **SIM cloning** or **account-level tampering**

| Carrier | Support Number |
|---------|---------------|
| Jio | 199 |
| Airtel | 121 |
| Vi | 199 |
| BSNL | 1800-180-1503 |

---

## 🔐 Final Security Tips

1. **Never dial unknown `*` or `#` codes** from strangers — USSD codes can modify your phone settings instantly without confirmation.
2. **Never share OTPs** — Not with anyone, not even callers claiming to be your bank or telecom provider.
3. **Lock your phone** — Physical access is the most common way call forwarding gets misconfigured. A strong PIN or biometric lock is your first line of defense.
4. **Run a security check regularly** — Make it a habit to dial `*#21#` every few weeks to verify your settings.
5. **Check after repairs** — Always verify your call forwarding settings after handing your phone to a repair shop.
6. **Use your carrier's official app** — Most carriers (Jio, Airtel, Vi) have apps where you can review and manage call settings securely.

---

## 🤝 Contributing

Contributions are welcome! If you have:
- Carrier voicemail numbers for other countries
- Carrier-specific USSD code variations
- iOS/Android version-specific behavior notes

Please open a **Pull Request** or file an **Issue**. Let's make this guide more comprehensive for everyone.

---

## 📚 Additional Resources

- [GSMA — Understanding USSD](https://www.gsma.com/)
- [TRAI (India) — Consumer Information](https://www.trai.gov.in/)
- Your mobile carrier's official support page

---

<div align="center">

### 🛡️ Your Phone. Your Calls. Your Privacy.

*In a world where your silence can be stolen,*
*awareness is the most powerful weapon you own.*
*Stay curious. Stay cautious. Stay in control.*

**— Because security isn't a feature. It's a right.**

</div>
