# ImpSci Navigator 🧭

**ImpSci Navigator** is an interactive, browser-based tool designed for implementation scientists, public health practitioners, and clinical leaders. It bridges the gap between assessing contextual barriers and selecting evidence-based implementation strategies, culminating in the generation of a publication-ready Implementation Research Logic Model (IRLM).

> **Note:** The current instance is pre-loaded with an example project based on the **Youth Readiness Intervention (YRI) Sierra Leone Protocol**. To remove these example data and use the tool for your own project, click on the trashcan in the upper righthand corner of the web app.

---

## 📖 README

### Core Frameworks
This application digitizes and integrates several foundational frameworks in Implementation Science:

1.  **CFIR 2.0 (Consolidated Framework for Implementation Research):** Used to map and categorize operational determinants (barriers and facilitators).
2.  **ERIC Taxonomy (Expert Recommendations for Implementing Change):** Used to algorithmically suggest implementation strategies to address specific CFIR barriers.
3.  **Proctor's Implementation Outcomes:** Used to specify the targeted outcome of each selected strategy (e.g., Feasibility, Fidelity, Acceptability).
4.  **IRLM (Implementation Research Logic Model):** A visual blueprint mapping the relationships between Context, Strategies, Mechanisms, and Outcomes.

### Key Features
* **Contextual Assessment Panel:** Document barriers and facilitators using the CFIR 2.0 taxonomy. Rate their valence, impact, feasibility, frequency, and duration.
* **MCDA Prioritization Matrix:** An interactive, drag-and-drop scatterplot (powered by D3.js) that maps determinants into "Go Zones" (Quick Wins, Secondary Targets, Long-term Advocacy, Monitor/Filter).
* **Algorithmic Strategy Engine:** Automatically suggests ERIC implementation strategies based on the specific CFIR barriers you've identified, sorted by expert consensus.
* **Strategy Specification Sandbox:** Detail the "Actor, Target, Dose, and Justification" for each chosen strategy to move from abstract ideas to concrete operational plans.
* **Automated IRLM Generation:** Instantly builds a visual logic model mapping your determinants to strategies and outcomes. Exportable as a high-resolution PNG for grant proposals or publications.
* **Local, Private Storage:** All data is saved automatically to your browser's local storage. No server is required, ensuring complete data privacy for sensitive operational assessments.

### Development Stack
This application is built as a lightweight, client-side-only web app using the following technologies:

* **Alpine.js:** For reactive state management and UI interactions, offering robust data binding without the overhead of a virtual DOM.
* **Tailwind CSS:** For rapid, utility-first styling, ensuring a clean and responsive user interface.
* **D3.js:** For rendering and managing the interactive, drag-and-drop MCDA Prioritization scatterplot.
* **html-to-image & html2canvas:** For capturing DOM elements and rendering high-resolution, publication-ready PNG exports of the IRLM.
* **Web Storage API (`localStorage`):** Used for zero-backend, session-persistent data storage to guarantee data privacy.

### How to Use the App
1.  **Configure Project:** Enter the name of your Innovation and the Setting.
2.  **Map Context (Left Sidebar):** Add determinants. Select a CFIR construct, rate its valence (is it a barrier or facilitator?), and set its Multi-Criteria Decision Analysis (MCDA) scores.
3.  **Prioritize (Center Matrix):** Review your determinants on the matrix. Drag the nodes to adjust their Impact vs. Feasibility scores. Focus your efforts on the "Quick Wins" (High Impact, High Feasibility).
4.  **Select Strategies (Right Sidebar):** Review the suggested strategies. Click one to open the specification modal, define *how* you will do it, and add it to your blueprint.
5.  **Export IRLM (Top Nav):** Scroll down to review your automated logic model, then click "Export IRLM" to download a publication-ready image.

---

## ❓ Frequently Asked Questions (FAQ)

### How does the MCDA Prioritization Matrix work?
The matrix uses Multi-Criteria Decision Analysis to help you figure out which barriers to tackle first.

* **X-Axis (Importance/Impact):** How severely does this determinant affect implementation?
* **Y-Axis (Feasibility/Addressability):** How easy is it for your team to change or overcome this determinant?
* **Node Color:** Represents valence (Red = Strong Barrier; Green = Strong Facilitator; Gray = Neutral).
* **Node Size:** Represents the *Frequency* of the determinant.
* **Node Opacity:** Represents the *Duration* or persistence of the determinant.

### How does the Strategy Engine know what to suggest?
The Strategy Engine uses published matching algorithms (specifically, the CFIR-ERIC matching project). When you log a barrier (Valence < 50) that has a high impact (> 5), the engine looks up which ERIC strategies implementation experts have agreed are most effective at overcoming that specific CFIR construct.

### What is an IRLM and why do I need one?
An Implementation Research Logic Model (IRLM), pioneered by J.D. Smith and colleagues, is a standardized visual format that clearly displays the relationships between your implementation context, the strategies you are using, the mechanisms they trigger, and the ultimate implementation outcomes. It is highly recommended by funders (like the NIH) for implementation science grant proposals.

### Where is my data saved? Can others see it?
Your data is saved securely in your own browser using `localStorage`. It is **not** sent to any external server or database. If you clear your browser cache, the data will be lost. To share your work, use the "Export Matrix" or "Export IRLM" buttons.

### Can I use this for my own project instead of the Sierra Leone example?
Yes! Click the **Red "Reset Session" Button** (the circular arrow icon) in the top right corner. This will clear the pre-loaded Sierra Leone YRI data and allow you to define your own Innovation and Setting from a blank slate.

### Why won't my IRLM export properly?
The IRLM export relies on converting HTML to an image canvas. If you are using a very strict browser (like Safari with aggressive privacy protections) or have heavily zoomed in/out, the rendering engine might struggle. Ensure your browser is at 100% zoom and try again. The app includes a built-in fallback engine if the primary high-resolution export fails.
