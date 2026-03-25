# Contributing to PHYS 43 Labs

Thank you for your interest in contributing to the PHYS 43 Labs repository. This project serves as a centralized, interactive dashboard for Physics for Scientists and Engineers III at Butte College. 

If you are adding a new lab calculator, uploading a new manual, or fixing a bug in an existing file, this document outlines the guidelines and technical details needed to contribute.

## Table of Contents
1. [Project Architecture](#project-architecture)
2. [Adding a New Lab](#adding-a-new-lab)
3. [Improving Existing Calculators](#improving-existing-calculators)
4. [Design and UI Guidelines](#design-and-ui-guidelines)
5. [Pull Request Process](#pull-request-process)
6. [Licensing Agreement](#licensing-agreement)

---

## Project Architecture

This repository uses a zero-build, static site architecture hosted on GitHub Pages. There is no Node.js environment, no Webpack, and no frontend framework (like React or Vue). 

The homepage (`index.html`) relies on a Jekyll bypass. It uses a Liquid templating loop (`site.static_files`) to read the directory contents at build time and passes those filenames to a Vanilla JavaScript parser. The JavaScript groups the files by lab number and dynamically generates the user interface.

Because of this architecture, **you do not need to modify `index.html` to add new labs.** The site will update itself as long as you follow the file naming conventions.

---

## Adding a New Lab

To add a new experiment to the dashboard, you simply need to upload the corresponding files to the root directory of the repository.

### File Naming Conventions
The JavaScript parser relies strictly on Regular Expressions to categorize files. You must use the following naming formats (where `X` is the lab number, which can include decimals or negative numbers):

* **Lab calculators:** `labXcalc.html` (e.g., `lab9calc.html`, `lab5.5calc.html`)
* **Lab manuals:** `Lab X manual.pdf` (e.g., `Lab 9 manual.pdf`, `Lab 5.5 manual.pdf`)

### Steps to Add:
1. Fork the repository.
2. Upload your `labXcalc.html` and/or `Lab X manual.pdf` to the root directory.
3. Commit the files and open a Pull Request.

*Note: It is perfectly fine to upload a manual without a calculator, or a calculator without a manual. The homepage will automatically disable the missing button on the UI.*

---

## Improving Existing Calculators

If you are fixing a math error, improving the code, or enhancing the user experience of an existing calculator, please keep the following technical constraints in mind:

1. **Single-File preference:** Try to keep the HTML, CSS, and JavaScript for a calculator contained within its specific `labXcalc.html` file. This maintains the modular, drop-in nature of the repository.
2. **Vanilla JavaScript:** Use standard, modern JavaScript (ES6+). Do not introduce external frameworks.
3. **External libraries:** If you need a library for data visualization or heavy computation, use a CDN link. Currently, the project utilizes `Chart.js` via CDN for graphing.
4. **Local storage:** Calculators should utilize `localStorage` to autosave student data so their work is not lost if the page refreshes. Ensure you scope your local storage keys properly (e.g., `phys43_labX_data`).

---

## Design and UI Guidelines

To maintain a consistent experience across all calculators, new files should attempt to match the dark, high-contrast visual style established in the recent labs.

If you are building a new calculator from scratch, you can copy the CSS `:root` variables from an existing recent lab (like `lab6calc.html` or `lab8calc.html`) to inherit the color palette. 

**Standard palette variables:**
* `--bg-body`: Application background (Deep dark gray/black)
* `--bg-card`: Container background (Slightly lighter gray)
* `--primary`: Main interactive elements and highlights (Cyan/Neon Blue)
* `--accent`: Secondary interactive elements
* `--text-main`: Standard reading text
* `--text-heading`: High-contrast text for titles

Ensure that your calculator is fully responsive and usable on both desktop monitors and mobile devices.

---

## Pull Request Process

1. Fork the repository and create your branch from `main`.
2. Name your branch descriptively (e.g., `add-lab-9`, `fix-lab-4-math-error`).
3. Ensure your code is clean, commented, and functional.
4. Test the calculator in your browser to ensure standard inputs yield expected physics outputs.
5. Open a Pull Request with a clear title and description of the changes or additions you have made.

---

## Licensing Agreement

By contributing to this repository, you agree that your contributions will be licensed under the project's overall license.

**For Code and Assets:**
Any source code (HTML, CSS, JS) or original assets you submit will be permanently licensed under the **Liberty-ShareAlike Public License (LSA-1.0)**. This allows anyone to use, share, and adapt the code without attribution, provided they share their adaptations under the same terms.

**For Lab Manuals:**
Lab manuals (`.pdf` files) are the intellectual property of the Butte College Department of Physics or their otherwise original authors. By uploading a PDF, you are simply providing it for educational reference. You do not claim copyright over it, and it is not covered by the LSA-1.0 license.
