
# LocalTutor 🎓
> **Private, 100% Browser-Based Adaptive AI Tutor (NotebookLM Alternative)**  
> Built with WebLLM (WebGPU), Transformers.js (WASM), Dexie (IndexedDB), and React.

LocalTutor is a client-side AI learning platform that lets students upload textbooks, syllabi, notes, or essays and receive adaptive, interactive tutoring with **zero cloud servers, zero API costs, and absolute student data privacy**.

---

## 🌟 Key Features

1. **100% Client-Side Private RAG**:
   - **Document Parsing**: In-browser extraction of PDF (`pdfjs-dist`), Word DOCX (`mammoth`), and Text (`.txt`, `.md`).
   - **Semantic Embeddings**: Generates 384-dimensional dense vectors using `@xenova/transformers` (`all-MiniLM-L6-v2`) via WebAssembly.
   - **Local Vector Database**: All document text, overlapping chunks, and vector embeddings persist across browser sessions in `IndexedDB` via `Dexie.js`.
   - **Cosine Similarity Search**: Fast client-side vector ranking to retrieve top context passages.

2. **WebLLM On-Device GPU Inference**:
   - Powered by `@mlc-ai/web-llm` running directly on your laptop's GPU via WebGPU.
   - Supports lightweight, fast student models:
     - `SmolLM2-360M-Instruct-q4f16_1-MLC` (~230 MB - rapid download for any laptop)
     - `Qwen2.5-0.5B-Instruct-q4f16_1-MLC` (~390 MB)
     - `Llama-3.2-1B-Instruct-q4f16_1-MLC` (~880 MB)
     - `Phi-3.5-mini-instruct-q4f16_1-MLC` (~2.2 GB)
   - Real-time token streaming with cancel/stop controls.
   - **Instant Simulation Mode**: Built-in instant testing mode that allows instant evaluation of adaptive prompts, RAG citations, and UI even on older devices without WebGPU flags.

3. **Adaptive Learning & Pedagogy**:
   - **4-Stage Complexity Slider**:
     - 🧒 **Elementary (Age 10)**: Explanations built on fun analogies, visual metaphors, and accessible stories.
     - 🎒 **High School**: Clear foundational concepts with relatable real-world connections.
     - 🎓 **Undergraduate**: Rigorous collegiate terminology and systematic mechanism breakdowns.
     - 🔬 **Expert / Research**: In-depth biochemical kinetics, thermodynamics, and cellular pathways.
   - **Socratic Tutor Mode**:
     - Toggle between direct explanations and guided Socratic questioning. Rather than spoon-feeding answers, LocalTutor points to clues in the text and asks questions to guide the student to discover the answer.
   - **Clickable Source Citations**:
     - Interactive citation chips (e.g. `[Source 1, Page 2]`). Clicking any chip opens the exact source excerpt with similarity scores.
   - **Auto-Generated Quizzes**:
     - Automatically generates 4-choice questions from reading materials.
     - Confetti animation on correct answers (`canvas-confetti`).
     - Socratic intervention hints when a question is missed.
   - **Active Recall Flashcards**:
     - Flip cards for review before exams.
   - **Pre-loaded Biology Sample**:
     - 1-click load of a sample chapter on *Mitochondria & Cellular Respiration* to test everything immediately without needing a PDF.

---

## 🚀 Getting Started

### Prerequisites
- Node.js (v18+)
- A modern browser with WebGPU enabled (Google Chrome 113+, Microsoft Edge 113+, or Arc)

### Running Locally
```bash
# Install dependencies
npm install

# Start Vite dev server
npm run dev
```

Visit `http://localhost:5173/` in your browser.

### Building for Production / Static Deployment
Because LocalTutor runs entirely in the browser, you can host it as a pure static site on GitHub Pages, Vercel, or Netlify:

```bash
npm run build
```
Upload the `dist/` directory directly to any static host.

---

## 🔒 Privacy & Security Guarantee
- **No data leaves the student's browser.**
- Uploaded essays, lecture slides, and notes never touch external servers or third-party APIs.
- Perfect for educational institutions and privacy-conscious students.
