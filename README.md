# EEG Fellows Training

Open-source interactive training platform for the lab's EEG fellows program.
Theory Track, Module 1 (Origin of the EEG signal) and Module 2 (Volume conduction, source problems, reference and montage).

The whole site is one file, `index.html`, with no build step and no dependencies
beyond Google Fonts and (for PDF slides only) pdf.js from cdnjs.

## What is in Module 1

| Section | What it does |
|---|---|
| Overview | Learning objectives checklist, explainer outline, prep readings |
| Lab 1: From membrane to field | Pyramidal neuron with sink/source field, return currents and a draggable electrode; EPSP vs action potential |
| Lab 2: Synchrony and summation | Two populations on a shared scale; √N vs N summation |
| Lab 3: Open and closed fields | Pyramidal, stellate, radial nucleus and random arrangements; falloff with distance |
| Lab 4: Orientation and folding | Coronal slice of folded cortex; crown, sulcal wall, fundus; patch width and input layer |
| Lab 5: The view from the scalp | 3D head with 21 electrodes (10-20) and a flat topomap; presets for motor, sulcal, visual, auditory and deep sources |
| What EEG misses | Synthesis and common misconceptions |
| Misconceptions check | 7-question quiz linked back to the labs |
| Discussion | The four seminar questions with private notes |
| Slides and videos | Library for every module, filterable, with per-section tagging |

## What is in Module 2

| Section | What it does |
|---|---|
| Overview | Objectives, explainer outline, prep readings |
| Lab 1: Volume conduction | Two cortical sources seen on the cortex and at the scalp; skull resistivity, source distance and depth; correlation between channels |
| Lab 2: Forward and inverse problems | Fit a single dipole to four recorded maps (focal, bilateral auditory, extended patch, two distant sources), then reveal the true sources |
| Lab 3: What high density buys | Sample the same field with 21 to 256 electrodes, rebuild it with spherical splines, and compare error with and without the skull |
| Lab 4: Choosing a reference | Simulated auditory ERP (N1, P2, P3) under infinity, vertex, linked mastoids, average (with coverage options) and surface Laplacian |
| Lab 5: Montage and layout | How 10-20 positions are measured; 10-20, 10-10 and illustrative geodesic 128/256 layouts |
| Reading a scalp channel | Synthesis, checklist, what to report, misconceptions |
| Misconceptions check | 8-question quiz |
| Discussion | The four seminar questions with private notes |

Models are deliberately simple (point sources and dipoles in a uniform medium,
relative units). Module 1 leaves out the skull. Module 2 approximates it as a spatial blur plus attenuation and uses spherical splines (Perrin et al., m = 4) for maps and the surface Laplacian. Geodesic layouts are illustrative; use the net's sensor file for analysis.

## Running it

- Open `index.html` in a browser, or
- Host it on GitHub Pages: push this folder to a repo, then Settings > Pages > deploy from the main branch.

## Adding slides and videos

- **On the hosted claude.ai version:** editors upload PDFs, images, MP4/WebM (up to 20 MB) or add links from the Slides and videos page. Everyone with access sees them.
- **On a self-hosted copy:** put files in a `media/` folder and list them in `STATIC_MEDIA` near the top of the script:

```js
const STATIC_MEDIA = [
  { module:"m1", section:"membrane", kind:"slides", title:"Session 1 slides", src:"media/m1-session1.pdf" },
  { module:"m1", section:"general",  kind:"video",  title:"Recorded lecture", src:"media/m1-lecture.mp4" },
];
```

`kind` is `slides` (PDF), `image`, `video` or `link`. Export PowerPoint or Keynote decks as PDF.

## Adding a module

1. In `COURSE.modules`, change the module's `status` to `"live"` and give it `sections` (id, title, kind). The first section is the module's overview.
2. Write a renderer for each section in `PAGES` (see `labPage(...)`, `quizPage(...)` and `discussionPage(...)`, and the Module 2 code for the pattern).
3. Add the module's quiz to `QUIZZES` and its objective count to `NOBJ`. The sidebar, pager and progress bar pick up the rest automatically.

## License

MIT. See `LICENSE`.
