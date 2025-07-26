# Round-1B


---

## **Round 1B – README.md**

```markdown
# Round 1B – Persona-Driven Document Intelligence
Adobe India Hackathon – Connecting the Dots Challenge

## Problem Statement
Build a system that analyzes a **collection of PDFs** and selects the most relevant sections based on:
- **Persona (role and expertise)**
- **Job-to-be-done (specific task)**

The system outputs a ranked list of important sections and subsections.

---

## Input / Output
```
### Input:
1. 3-10 PDFs in `/app/input`
2. A persona description (text file)
3. A job-to-be-done description (text file)

### Output:
JSON file with:
- Metadata:
  - Documents, persona, job-to-be-done, timestamp
- Extracted Sections:
  - Document, page, section title, importance rank
- Subsection Analysis:
  - Document, page, refined text, importance rank

---
```
## Approach
```
1. **Preprocessing & Outline Parsing**
   - Reuse Round 1A outline extraction.
2. **Relevance Scoring**
   - Embed persona and job-to-be-done description using an offline NLP model.
   - Compute semantic similarity between document sections and persona+task.
3. **Ranking**
   - Assign importance scores to sections/subsections.
4. **Output JSON**
   - Structured JSON with metadata, ranked sections, and refined subsections.

---
```
## Libraries / Tools
```
- Python 3.x
- PyMuPDF / pdfplumber
- Sentence Transformers (offline)
- NumPy, Scikit-learn
- Docker
```
---

## How to Build & Run
```

### Build Docker Image
```bash
docker build --platform linux/amd64 -t persona_doc_intel:latest .
Run the Container
bash
Copy
Edit
docker run --rm \
  -v $(pwd)/input:/app/input \
  -v $(pwd)/output:/app/output \
  --network none persona_doc_intel:latest
Constraints
Must run offline (CPU only)

Processing time ≤ 60s for 3–5 PDFs

Model size ≤ 1GB
```
Notes
```
Sections are ranked for relevance to persona + task.

Works for varied document types and personas.

yaml
Copy
Edit
