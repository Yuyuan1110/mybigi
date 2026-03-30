# 🧠 Knowledge Operating System (KOS) Manual

**Version**: v0.1

**Target Audience**: Me

**Core Philosophy**: **"Capture via Cornell, Store via Zettel, Navigate via MOC, and Visualize via Canvas."**

---

## 📁 Part I: Structural Framework (The Filesystem)

The system follows a numerical prefix system to ensure fixed sorting and logical flow. Sub-folders are strictly prohibited within the Zettelkasten to prevent "information silos."

|Folder ID|Name|Purpose|Rules|
|---|---|---|---|
|**000**|`Index`|Ingestion point for Cornell notes & logs.|Entry point for all new data. Clear weekly.|
|**001**|`DailyNotes`|Daily reviews, habits, and peripheral records.|**Excluded** from the knowledge cycle.|
|**100**|`Projects`|Short-term goals with deadlines.|Move to `900_Archives` when "Done."|
|**200**|`Areas`|Long-term responsibilities (Math, Kernel).|Contains domain-specific overviews.|
|**300**|`Zettelkasten`|Permanent, atomic technical notes.|**Flat structure.** No sub-folders.|
|**700**|`MOCs`|High-level indices and maps.|The centralized "Navigation Hub."|
|**800**|`Templates`|System automation (Cornell, Zettel, MOC).|Maintain system integrity here.|
|**900**|`Archives`|Completed projects and inactive data.|Read-only storage for historical context.|
|**999**|`Resources`|Non-markdown assets (PDFs, Images).|Use clear naming: `Ref_Title_Date`.|

---

## 🔄 Part II: The Knowledge Pipeline (Lifecycle)

### 1. Capture Phase (Ingestion)

- **Location**: `000_Index`
- **Method**: Use the **Cornell Template**.
- **Requirement**: Every entry must include a "Cues" section (left column) for active recall and an "Abstract" (bottom) for high-level synthesis.

### 2. Refinement Phase (Atomization)

- **Location**: Move from `000` to `300_Zettelkasten`.
- **Atomicity**: One note must represent one discrete concept (e.g., `[[Interrupt_Context_Restrictions]]`).

### 3. Synthesis Phase (Mapping)

- **Location**: `700_MOCs`
- **Action**: Connect new Zettels to their respective Map of Content.
- **Evolution**: Transform list-based MOCs into "Narrative MOCs" that explain the _relationship_ between concepts.

---

## 🎨 Part III: Canvas Visualization Standards

- **Architecture Analysis**: Visualize MOCs or explain somehow.
- **Cross-Domain Mapping**: Use Canvas to bridge Mathematics (Linear Algebra) with Technical Implementation (Graphics/Optimization).
- **War Room**: During active debugging (e.g., `cros_ec_ishtp` panic), use Canvas to align Logs, Code, and Datasheets.
- **Rule**: Annotations in Canvas exceeding 200 words must be extracted into a `300_Zettelkasten` note.

---

## 🏷️ Part IV: Metadata & Naming Conventions

### 1. Naming Standards

- **Zettel**: `[[Concept_Name]]` (e.g., `[[Two_Phase_Locking]]`).
- **MOC**: `[[Subject_Name_MOC]]` (e.g., `[[Calculus_MOC]]`).
- **Project**: `[[Project_CodeName_YYYY]]`.

### 2. Tagging Strategy

- `#inbox`: Unprocessed data in `000_Index`.
- `#permanent`: Verified knowledge in `300_Zettelkasten`.
- `#context/work` | `#context/study` | `#context/english`.
- `#status/active` | `#status/refactoring`.

---

## 📜 Part V: The Role of "Areas" (200_Areas)

- **Definition**: Ongoing responsibilities that require a high standard over time (e.g., Linux Kernel Expertise, Mathematical Proficiency).
- **Storage Logic**: While the **Knowledge Hub** lives in `700_MOCs`, the **Area folder** handles specific resources and long-term tracking.
    
- **Refining the Intersection**:
    
    - If a concept is purely theoretical (e.g., `[[Taylor_Series]]`), link it in `[[Math_MOC]]`.
    - If a concept is applied (e.g., `[[Kernel_Timer_Approximation]]`), link it in both `[[Math_MOC]]` and `[[Kernel_MOC]]`.

---

## 🤖 Part VI: AI Collaboration Protocol (For Gemini/LLMs)

1. **Technical Accuracy**: Always prioritize Linux Kernel coding standards. Use **C** for logic and **Bash** for tooling.
2. **Linguistic Precision**: Evaluate all English notes against **IELTS 7.5** standards. Focus on "Formal Oral" and "Coherence & Cohesion."
3. **Socratic Pressure**: When generating a Zettel, ask the user one "Edge Case" question to stress-test the note’s logic.
4. **Implicit Discovery**: Suggest links between `200_Areas` (e.g., "This Linear Algebra concept could optimize your RISC-V vector processing note").

---

## 🚀 Part VII: Maintenance (The "Janitor" Routine)

- **The Friday Sweep**: Clear `000_Index`. Move items to `300_Zettelkasten` or `900_Archives`.
- **The Monthly Refactor**: Open `700_MOCs`. Look for "Orphan Notes" (unlinked Zettels) and integrate them into the map.
- **Template Audit**: Update `800_Templates` based on evolving needs (e.g., adding a specific field for RISC-V CSRs).