# EEG Fellows Training

Open-source interactive training platform for the lab's EEG fellows program.
Theory Track, Module 1: Origin of the EEG signal.

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

Models are deliberately simple (point sources and dipoles in a uniform medium,
relative units). Skull smearing and referencing are left for Module 2.

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

1. In `COURSE.modules`, change the module's `status` to `"live"` and give it `sections` (id, title, kind).
2. Write a renderer for each section in `PAGES` (see `labPage(...)` and the Module 1 labs for the pattern).
3. Add the section ids to `ORDER` and to the sidebar in `renderNav`.

## License

MIT. See `LICENSE`.
