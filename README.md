# 📱 Phone Call Forwarding — Security Awareness Guide

![Educational](https://img.shields.io/badge/Purpose-Educational%20Only-blue?style=flat-square)
![GSM Standard](https://img.shields.io/badge/Standard-GSM%20USSD-green?style=flat-square)
![License](https://img.shields.io/badge/License-MIT-yellow?style=flat-square)
![Contributions Welcome](https://img.shields.io/badge/Contributions-Welcome-brightgreen?style=flat-square)

> **Disclaimer:** This guide is strictly for **educational and personal security purposes**. The information is intended to help you protect and audit **your own device and line**. Configuring settings on someone else's device without their explicit consent is **illegal** under cybercrime and privacy laws in most jurisdictions.

---

## 📖 Table of Contents

- [Why This Guide Exists](#-why-this-guide-exists)
- [Who This Is For](#-who-this-is-for)
- [What Is Call Forwarding?](#-what-is-call-forwarding)
- [How Call Forwarding Works](#-how-call-forwarding-works)
- [Technical Deep Dive — USSD & GSM Internals](#-technical-deep-dive--ussd--gsm-internals)
- [Types of Call Forwarding](#-types-of-call-forwarding)
- [Quick Reference — All Codes](#-quick-reference--all-codes)
- [Step-by-Step: Check Your Line in 2 Minutes](#-step-by-step-check-your-line-in-2-minutes)
- [How to Read USSD Results](#-how-to-read-ussd-results)
- [How to Disable Forwarding Safely](#-how-to-disable-forwarding-safely)
- [⚠️ Attack Scenario Modeling](#%EF%B8%8F-attack-scenario-modeling)
- [Android vs iOS Differences](#-android-vs-ios-differences)
- [Troubleshooting Guide](#-troubleshooting-guide)
- [When to Contact Your Carrier](#-when-to-contact-your-carrier)
- [India Voicemail Quick List](#-india-voicemail-quick-list)
- [Hardening Checklist](#-hardening-checklist)
- [FAQ](#-faq)
- [Contributing](#-contributing)
- [Additional Resources](#-additional-resources)

---

## 🎯 Why This Guide Exists

Call forwarding is one of the most commonly misunderstood telecom settings. This README helps you:

- Understand what each forwarding mode does at a technical level.
- Detect unexpected forwarding quickly using standard GSM codes.
- Disable forwarding with confidence.
- Recognize real-world attack scenarios that exploit forwarding.
- Escalate correctly if a carrier-side issue is suspected.

---

## 👥 Who This Is For

- Everyday users who want a fast personal security check.
- People who recently shared, repaired, or factory-reset their phone.
- Anyone investigating missed calls, unexplained voicemail behavior, or suspicious account activity.
- Students and professionals studying mobile network security.

---

## 📡 What Is Call Forwarding?

Call forwarding is a **legitimate telecom feature** that redirects incoming calls from your primary number to a different destination — usually voicemail, another line, or a virtual number.

It is normally useful, but if changed without your knowledge, it can cause:

- Missed calls you never see or hear.
- Privacy risks (someone else receiving your calls and voicemails).
- Social-engineering opportunities against your contacts.
- Account takeover risk when combined with OTP-based authentication.

---

## 🔄 How Call Forwarding Works

### Normal Flow

```text
Caller ──────────────────────────► Your Phone 📱
                                    (Rings normally)
```

### Forwarded Flow

```text
Caller ──────► Carrier Network 📶 ──► Forwarded Number ☎️
                                    (Your phone may not ring at all)
```

Because forwarding is configured at the **carrier/network level**, calls can be rerouted before your handset ever receives them — making it invisible without an explicit check.

---

## 🔬 Technical Deep Dive — USSD & GSM Internals

### How USSD Works (GSM Signaling)

**USSD (Unstructured Supplementary Service Data)** is a GSM protocol used to communicate with the carrier's systems in real time. Unlike SMS, USSD sessions are:

- **Synchronous** — the network holds the session open while processing.
- **Low-latency** — responses typically arrive in under 2 seconds.
- **Session-based** — the connection closes once the reply is received.

When you dial `*#21#` and press Call, your handset encodes it as a **MMI (Man-Machine Interface)** string, which is transported as a USSD message over the **SS7 (Signaling System 7)** signaling plane — not over voice or data.

```
Your Handset
     │  MMI string (*#21#)
     ▼
BSS (Base Station Subsystem)
     │  USSD-Request (GSM MAP)
     ▼
MSC (Mobile Switching Centre)
     │  MAP-Process-USSD-Request
     ▼
HLR (Home Location Register)  ◄──── Stores your forwarding rules
     │  Returns CF status
     ▼
Response rendered on your screen
```

### HLR and VLR — Where Forwarding Lives

| Component | Full Name | Role |
|-----------|-----------|------|
| **HLR** | Home Location Register | Permanent subscriber database. Stores all call forwarding rules (CFU, CFB, CFNR) for your number. |
| **VLR** | Visitor Location Register | Temporary register at the current serving MSC. Copies relevant HLR data when you roam or move. |

> Key insight: Because forwarding rules live in the **HLR**, they persist even if your phone is off, the SIM is removed, or you travel internationally. This is why **physical access to your device alone is enough** to set forwarding that survives a reboot.

### CFU vs CFB vs CFNR — Technical Differences

| Code | Full Name | Trigger Condition | GSM Service Code |
|------|-----------|-------------------|-----------------|
| **CFU** | Call Forwarding Unconditional | Every call, immediately, no ringing | SS 21 |
| **CFB** | Call Forwarding on mobile Busy | You are already on an active call | SS 67 |
| **CFNR** | Call Forwarding on No Reply | Phone rings but is not answered within a timer (default: 20 sec) | SS 61 / 62 |

> **CFNR** is the most commonly used by carriers for voicemail. **CFU** is the most dangerous — it silently diverts every call without your phone ever ringing.

---

## 🔀 Types of Call Forwarding

| Type | What It Means | Check Code | Cancel Code |
|------|----------------|------------|-------------|
| **Unconditional (CFU)** | Every incoming call is forwarded immediately | `*#21#` | `##21#` |
| **Unreachable / No-Answer (CFNR)** | Calls forward when phone is off, out of signal, or unanswered | `*#62#` | `##62#` |
| **Busy (CFB)** | Calls forward while you're already on another call | `*#67#` | `##67#` |

---

## ⚡ Quick Reference — All Codes

> Enter each code in your dialer and press **Call** (green button).

| Action | Unconditional (CFU) | Unreachable / No-Answer (CFNR) | Busy (CFB) |
|--------|---------------------|-------------------------------|------------|
| **Check** | `*#21#` | `*#62#` | `*#67#` |
| **Cancel** | `##21#` | `##62#` | `##67#` |

---

## ✅ Step-by-Step: Check Your Line in 2 Minutes

1. Open your dial pad.
2. Dial `*#21#` — press Call — note the result.
3. Dial `*#62#` — press Call — note the result.
4. Dial `*#67#` — press Call — note the result.
5. If any **unknown number** appears in results, cancel with the matching `##` code.
6. Re-run all `*#` checks to confirm the cancellation succeeded.

> 💡 **Tip:** Screenshot each result before and after changes. Useful when speaking with carrier support.

---

## 📊 How to Read USSD Results

### ✅ Safe — No Forwarding Active

```text
Voice:    Not forwarded ✅
Data:     Not forwarded ✅
Fax:      Not forwarded ✅
```

### ⚠️ Forwarding Detected

```text
Voice forwarded to: +91XXXXXXXXXX ⚠️
```

This means calls are being redirected. This could be:

- ✅ A **carrier voicemail number** (often legitimate — see India list below)
- ✅ A **number you set yourself** and forgot about
- ❌ In rarer cases, **unauthorized forwarding** configured without your knowledge

Do not panic — verify the number against known carrier voicemail lists, then disable if unrecognized.

---

## 🛑 How to Disable Forwarding Safely

Open your dial pad, enter each code, and press **Call**:

```
##21#   →  Cancels ALL unconditional forwarding (CFU)
##62#   →  Cancels unreachable / no-answer forwarding (CFNR)
##67#   →  Cancels busy forwarding (CFB)
```

Immediately re-run the corresponding **check codes** to confirm each rule is removed. If a rule reappears after cancellation, treat it as a carrier/account-level issue and escalate.

---

## ⚠️ Attack Scenario Modeling

Understanding how call forwarding is exploited helps you recognize risks before they affect you.

---

### 🔴 Scenario 1 — Physical Access Attack (30-Second CFU)

```
Timeline:
  T+0s   Attacker gains brief physical access to unlocked phone
  T+10s  Attacker opens dial pad
  T+15s  Dials *21*<attacker_number># → press Call → CFU activated
  T+20s  Returns phone. Victim is unaware.
  T+∞    Every call to victim is silently forwarded to attacker
```

**Impact:** Victim misses all calls. Attacker can intercept voicemail, OTPs delivered via call, and impersonate the victim to callers.

**Defense:** Screen lock before handing phone to anyone. Run `*#21#` check after any unattended access.

---

### 🔴 Scenario 2 — SIM Swap + CFNR Account Takeover

```
Attack Chain:
  Step 1  Attacker social-engineers carrier support using leaked PII
  Step 2  Carrier ports victim's number to attacker's SIM (SIM swap)
  Step 3  Attacker enables CFNR on their new SIM → victim's original SIM goes dark
  Step 4  Attacker requests "forgot password" on bank/email account
  Step 5  OTP call is routed to attacker's device
  Step 6  Account is compromised. No malware required.
```

**Impact:** Full account takeover of any service using SMS or call-based 2FA — banking, email, social media.

**Defense:** Set a carrier account PIN. Enable SIM lock. Use authenticator apps (TOTP) over SMS/call-based 2FA wherever possible.

---

### 🟡 Scenario 3 — Repair Shop CFB Exploit

```
Attack Chain:
  Step 1  Victim hands phone to repair technician (trusted context)
  Step 2  Technician dials *67*<number># → CFB activated quietly
  Step 3  Victim receives phone back, doesn't notice
  Step 4  While victim is on any call, all other incoming calls silently route to attacker
```

**Impact:** Selective interception of calls during busy periods — less visible, harder to detect.

**Defense:** Always run all three `*#` checks after any device repair or handoff.

---

### 🟡 Scenario 4 — Social Engineering via Fake Tech Support

```
Attack Chain:
  Step 1  Attacker calls victim, claims to be "carrier technical support"
  Step 2  Instructs victim to dial *21*<attacker_number># to "fix a network issue"
  Step 3  Victim unknowingly activates CFU themselves
  Step 4  Attacker now receives all victim's calls
```

**Impact:** Victim's calls forwarded with their own cooperation, making it harder to dispute with the carrier.

**Defense:** Never dial `*` or `#` codes given by strangers. Carriers will **never** ask you to do this.

---

## 📱 Android vs iOS Differences

| Feature | Android | iPhone (iOS) |
|---------|---------|--------------|
| USSD response | Usually immediate popup | Carrier dependent; may vary |
| `*#21#` support | ✅ Fully supported | ⚠️ Partially — depends on carrier |
| Reliable manual path | Dialer USSD codes | **Settings → Phone → Call Forwarding** |
| Recommendation | Use USSD + settings | Use Settings view first, then test with real call |

**iPhone users:** If USSD codes don't work reliably, go to **Settings → Phone → Call Forwarding** — this reads directly from your carrier profile and is the most reliable check on iOS.

---

## 🧰 Troubleshooting Guide

### "Code failed" / "MMI invalid"
- Retry with strong signal and an active SIM.
- Remove any spaces or extra symbols from the code.
- Some MVNOs or roaming contexts block specific USSD queries — contact carrier.

### "Forwarding turns back on after cancel"
- Check if carrier voicemail auto-re-enables CFNR/CFB.
- Ask carrier to remove all conditional forwarding and voicemail provisioning temporarily.
- If it persists, suspect account-level tampering — escalate immediately.

### "I still miss calls after disabling everything"
- Test with airplane mode off and Wi-Fi calling toggled.
- Verify DND (Do Not Disturb), call blocking apps, and spam filters.
- Run controlled tests from two different carrier networks.

---

## 📞 When to Contact Your Carrier

Contact support when:

- Cancel codes report success but forwarding remains active.
- Unknown destination numbers persist after cancellation.
- Forwarding reactivates repeatedly on its own.
- You suspect SIM swap, SIM cloning, or account compromise.

When contacting support, request:

1. Full forwarding status for your voice service (CFU/CFB/CFNR).
2. Timestamped change history (if available).
3. Removal and reset of all forwarding rules.
4. Account PIN reset and SIM revalidation.

| Carrier | Support Number |
|---------|---------------|
| Jio | 199 |
| Airtel | 121 |
| Vi (Vodafone Idea) | 199 |
| BSNL | 1800-180-1503 |

---

## 🇮🇳 India Voicemail Quick List

If you see a forwarding number you don't recognize, it may simply be your carrier's default voicemail — which is completely normal. Verify before canceling.

> This list is illustrative and may change. Always verify with official carrier websites or apps.

| Carrier | Common Voicemail Number |
|---------|--------------------------|
| **Jio** | +91-40-4121-0000 / 1800-889-9999 |
| **Airtel** | +91-98-1800-0543 |
| **Vi (Vodafone Idea)** | +91-98-2009-8200 |
| **BSNL** | 56789 |

---

## 🔐 Hardening Checklist

- [ ] Set a strong screen lock (PIN / biometric).
- [ ] Enable a SIM PIN to prevent unauthorized SIM use.
- [ ] Set a carrier account PIN to protect against SIM swap.
- [ ] Review all three forwarding codes monthly.
- [ ] Re-check after travel, eSIM migration, device repair, or any handoff.
- [ ] Switch to TOTP-based 2FA (e.g., Google Authenticator) away from SMS/call-based 2FA.
- [ ] Use only official carrier apps/portals for line management.
- [ ] Never dial `*` or `#` codes given verbally by strangers.

---

## ❓ FAQ

**Q: Is all forwarding suspicious?**
No. Voicemail and business call routing are common legitimate uses. Always verify the destination number before canceling.

**Q: Can malware enable forwarding remotely?**
In most documented cases, unauthorized changes require physical device access or carrier-account compromise rather than sophisticated malware. The threat model is usually social engineering, not zero-day exploits.

**Q: Do these codes work worldwide?**
GSM/MMI USSD behavior is carrier-dependent. The codes listed here are standard and work on most GSM networks globally, but specific MVNOs or CDMA carriers may not support them.

**Q: Should I disable voicemail entirely for security?**
Not always necessary. The safer approach: verify the destination number, secure your carrier account with a PIN, and monitor for unexpected changes monthly.

**Q: Why does CFU survive a phone reboot?**
Because CFU rules are stored in the **HLR** (carrier database), not on your device. They persist regardless of phone state.

---

## 🤝 Contributing

Contributions are welcome. Helpful additions:

- Carrier-specific USSD behavior by country/region.
- Verified voicemail destination number references.
- iOS/Android version differences with screenshots.
- Better troubleshooting flows for MVNO users.
- Attack scenario additions with documented real-world cases.

Open a **Pull Request** or **Issue** with reproducible details: carrier, country, device, OS version, and observed output.

---

## 📚 Additional Resources

- [GSMA — GSM Standards & USSD](https://www.gsma.com/)
- [TRAI (India) — Consumer Information](https://www.trai.gov.in/)
- [3GPP TS 22.082 — Call Forwarding Supplementary Services Specification](https://www.3gpp.org/)
- Your carrier's official support portal

---

<div align="center">

### 🛡️ Your Phone. Your Calls. Your Privacy.

*Security improves when checks become habits.*

**Understand the protocol. Know the threat. Stay in control.**

</div>
