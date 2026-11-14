# Safe Start 👶🏥

**Safe Start** is a newborn registration and verification platform built for the **Tamil Nadu Government**. It enables hospitals to securely register birth records while giving the Government Medical Council oversight, auditability, and fraud-detection capabilities — without ever granting edit/delete access to government users.

---

## 🎯 Problem Statement

Newborn registration in hospitals today is fragmented, paper-heavy, and hard to audit. Safe Start digitizes this process end-to-end with:

- Biometric-backed birth records (father, mother, and child footprints)
- Automatic duplicate detection to prevent fraudulent or duplicate registrations
- Parent verification via displayed confirmation + SMS before a record is finalized
- Strict, role-based access control between hospitals and government oversight
- A dispute/verification pathway for a child to later confirm parentage records

---

## 👥 User Roles

| Role | Capabilities |
|---|---|
| **Hospital Staff** | Create new birth records, edit within a 24-hour window only, cannot view other hospitals' data |
| **Government Medical Council** | Search/view all hospital records (read-only), receive unusual-login alerts, approve password resets and verification disputes |

---

## ✨ Core Features

- **Role-based login** — separate authentication flows for Hospital and Government Medical Council users, each with a unique ID
- **Forgot password flow** — hospital resets require Government Medical Council approval + a submitted reason
- **Multi-step registration wizard** — biometric capture → duplicate check → parent verification screen → SMS confirmation
- **24-hour edit/lock logic** — records become immutable after 24 hours
- **Duplicate detection** — biometric comparison blocks registration if a match is found
- **Masked sensitive data** — mobile numbers shown masked (e.g. `98XXXXXX21`) with timed reveal for authorized officials
- **Unusual login alerts** — Government Medical Council is notified of anomalous hospital logins
- **10-year data retention** — records auto-purge 10 years from their last update
- **Dispute & verification flow** — individuals can request official verification of their parentage records via the Government Medical Council

---

## 🏗️ Architecture

Built in **Flutter** with no third-party dependencies, using a clean, layered structure:

```
lib/
├── models/     # Data models (BirthRecord, Hospital, User, etc.)
├── data/       # Mock/repository data layer (swap for real API later)
├── theme/      # Centralized styling and design tokens
├── widgets/    # Reusable UI components
├── screens/    # Login, Hospital Dashboard, Government Dashboard, Registration Wizard
└── main.dart   # RootApp — owns session state and hospital-list state
```

**Design principles:**
- Clear separation of concerns across layers
- No visit access for hospital staff beyond their own records
- Read-only, non-destructive access for Government Medical Council
- Production-minded structure even though data/auth are currently mocked

---

## 📊 Data Fields Captured Per Birth Record

1. Father's biometric (footprint) & name
2. Mother's biometric (footprint) & name
3. Child's footprint
4. Child's gender
5. Date, month, year & time of birth
6. Doctor name
7. Hospital name & location
8. Father's or mother's mobile number (masked by default)

---

## 🔒 Security & Compliance

- Encrypted data transmission between hospitals and the government server
- Mobile numbers masked in all normal views; revealed only to authorized officials for verification, with timed access
- Full audit trail of logins and record access
- Records retained for 10 years, then automatically deleted
- No edit or delete permissions for Government Medical Council members

---

## 🚧 Project Status

This repository currently contains a **production-structured prototype**:

- ✅ Functional Requirements Specification
- ✅ Interactive prototype
- ✅ Flutter codebase with mocked data/auth

### Mocked vs. Real

| Component | Status |
|---|---|
| Login/authentication | Mocked |
| Biometric capture | UI only — no SDK integration yet |
| SMS confirmation | Simulated |
| Backend/API | Not connected — local mock data |
| Duplicate detection | Simulated logic |

### Next Steps for Production

1. Replace mock login with real authentication
2. Integrate a backend API
3. Integrate camera & fingerprint SDKs for real biometric capture
4. Connect an SMS gateway for confirmation messages
5. Implement the full edit flow within the 24-hour window
6. Build out the dispute/verification flow for flagged duplicates

---

## 🛠️ Getting Started

```bash
# Clone the repository
git clone https://github.com/<your-username>/safe-start.git
cd safe-start

# Get Flutter dependencies
flutter pub get

# Run the app
flutter run
```

**Requirements:** Flutter SDK (stable channel), no additional third-party packages needed for the current prototype.

---

## 📄 Documentation

- `docs/Functional_Requirements_Specification.docx` — full FRS covering user roles, auth flows, data fields, workflows, security, and data retention

---

## 📜 License

Government of Tamil Nadu internal project. License terms to be determined by the project owner.

---

## 🙋 Contact

Maintained by the Safe Start development team on behalf of the Tamil Nadu Government Medical Council initiative.
---
### 🔒 DEMO LOGIN ID AND PASSWORD:
For hospital admin login : HOSP-TN-448241
Password : DeepCheck@2026
For Govnt login: GMC-TN-227111
Password : DeepCheck@2026

## 📜 Important

### © Original Authorship & Intellectual Ownership

All original written statements, research descriptions, project documentation, and conceptual content presented in this README are the independent work and intellectual creation of **Mr. Vimal P.** These writings were personally researched, developed, and authored by him for the **Safe Start Project**. No individual or organization may reproduce, copy, modify, or claim authorship of these original written materials without prior written permission from Mr. Vimal P., except as permitted by applicable law.

**Original Author & Creator:** Mr.VIMAL P.  (❣️Mr. vîmąľMy1❣️) 
**Project Name:** Safe Start  
**Copyright © 2026 Mr. Vimal P. All Rights Reserved.
