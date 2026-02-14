# Victim Page Specification: Template & Style Guide

This document defines the architecture, style, and workflow for creating high-impact, single-page victim narratives for the "Stop Deed Theft" campaign (e.g., Ms. Hung Case).

## 1. Architecture

The project uses a **Single HTML File** architecture for portability and rapid deployment. CSS and JavaScript are embedded directly in `index.html`.

### File Structure
```
/Victim-Name/
│
├── index.html          # The entire site (HTML + CSS + JS)
├── assets/             # Media assets
│   ├── portrait.png    # Hero image (cutout of victim)
│   ├── doc-leak.png    # Act 2 Background (blurred document)
│   ├── logo.jpg        # Campaign Logo
│   └── [case-specific] # e.g., house.png, evidence.png
```

### Key Sections (HTML Structure)
1.  **Header**: Meta tags, Google Fonts (`Oswald`, `Inter`), CSS Variables.
2.  **Act 1: The Story**: Hero section with split layout (Portrait | Headline).
3.  **Act 2: The Facts**: Vertical scroll section with "Proof Boxes" (Crime, Law, Trap, Perjury).
4.  **Act 3: The Pattern**: List of related court cases (External Links).
5.  **Reckoning / Action**:
    - "Stop The Attorneys" block.
    - Grievance Form (Name Input + Email Button).
    - "Fast Lane" Sticky Button (Bottom Right).

---

## 2. Style Rules (The "Noir" Aesthetic)

The design language is **Urgent, Gritty, and High-Contrast**. It uses a "Film Noir" influence to convey the gravity of the crime.

### Typography
-   **Headlines**: `Oswald` (Weights: 700, 900). Uppercase.
-   **Body Text**: `Inter` (Weights: 400, 700). High readability.
-   **"Dirty Text" Effect**: Headlines are slightly rotated (`-1deg` to `1deg`) via JS to feel imperfect and raw.

### Color Palette
| Name | Hex | Usage |
| :--- | :--- | :--- |
| **Noir Black** | `#050505` | Main Background, Deep shadows. |
| **Caution Red** | `#D22B2B` | Activity, Alerts, "The Crime", Primary Buttons. |
| **Safety Orange** | `#8c391a` | Accents, Links, Progress Bar, Secondary Buttons (Darker). |
| **Off-White** | `#e0e0e0` | Narrative Text, Contrast against black. |
| **Smoke Grey** | `rgba(255,255,255,0.05)` | Subtle borders, dividers. |

### Visual Effects
-   **Vignette**: Radial gradients on images (`radial-gradient(circle at center, transparent 50%, #000 100%)`) to focus attention and blend edges into the black background.
-   **Overlay**: Dark overlays (`rgba(0,0,0,0.85)`) on background images to ensure text readability.
-   **Scroll Progress**: A thin `#8c391a` bar at the top of the viewport.
-   **Hover States**:
    -   *Buttons*: Brighten on hover.
    -   *Case Links*: "Tactical Selection" - Left border appears (`4px solid #8c391a`) and text nudges right (`padding-left: 12px`).

---

## 3. Workflow: Creating a New Case

Follow this step-by-step process to replicate the Ms. Hung standard.

### Step 1: The Evidence (Research)
-   Gather the core facts:
    1.  **The Victim**: Name, Age, Status (Widow/Elder).
    2.  **The Loss**: Amount Stolen, Property Value.
    3.  **The Tactic**: How did they do it? (Deed theft, Fake notary, LLC loophole).
    4.  **The Villain**: Law Firm, LLC, or Judge involved.
    5.  **The Pattern**: Find 3-5 other cases involving the same bad actors.

### Step 2: The Narrative (Writing)
-   Draft the **4 Key Cards** for Act 2:
    -   **THE DECEIT** (The initial lie/theft).
    -   **THE LAW** (The specific statute violated, e.g., CPLR 3002(f)).
    -   **THE TRAP** (The legal maneuvering/pressure).
    -   **THE PERJURY** (The lie told in court).
-   Draft the **Action Email**: Subject line and body text for the grievance.

### Step 3: Asset Preparation
-   **Portrait**: Start with a high-res photo of the victim. Use Photoshop/AI to remove the background. Save as `assets/portrait.png`.
-   **Documents**: Get a screenshot of a court filing or deed. Blur it slightly or darken it for `assets/doc-leak.png`.

### Step 4: The Build (Code)
1.  **Clone the Template**: Copy the `index.html` from `/.agent/templates/` or a previous case.
2.  **Update Meta**: Title, Description.
3.  **Update Content**:
    -   Replace "Act 1" Story text.
    -   Replace "Act 2" Cards.
    -   Update "Act 3" Case Links (hrefs and text).
4.  **Update Action Logic**:
    -   Edit the `dispatchUltimatum()` JS function.
    -   Update `to`, `cc`, `subject`, and `bodyText` variables.

### Step 5: Refine & Deploy
1.  **Mobile Check**: Verify text sizes (`clamp()`) on mobile.
2.  **Visual Polish**: Check button visibility and sticky logic.
3.  **Git Push**: Commit to main for Netlify auto-deploy.

---

*Verified on: Ms. Hung Case (Feb 2026)*
