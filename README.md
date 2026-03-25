# PHYS 43 Labs

**Live Site:** [https://shorttimenosee.github.io/phys43labs/](https://shorttimenosee.github.io/phys43labs/)

This repository hosts a collection of student-made, interactive lab calculators and reference manuals for **PHYS 43: Physics for Scientists and Engineers III** (Calculus-based) at Butte College, based on the Spring 2026 curriculum taught by Patrick McDougall.

Please note that this is an unofficial resource. It is not affiliated with, maintained by, or endorsed by Butte College or the Department of Physics. The calculators are built to assist with data processing and visualization but are not guaranteed to be perfectly accurate.

## For Students

This site provides a centralized dashboard for the lab experiments in the course. For available labs, you can:
* **View manuals:** Read the official lab instructions.
* **Launch calculators:** Use the interactive HTML tools to input your raw data, calculate derivations, and generate necessary graphs or tables for your lab reports.

The calculators are designed to run entirely in your web browser. No software installation is required, and no data is sent to external servers.

## Technical Details

This site is hosted via GitHub Pages and uses a zero-build, single-file architecture. It does not use Node.js, Webpack, or standard static site generators like Hugo or Next.js.

### Architecture
The root `index.html` file is the centralized dashboard. It uses an empty YAML front matter block (`---`) at the top of the file to force GitHub Pages to process the file using its built-in Jekyll engine before serving it to the browser.

The file uses Jekyll's Liquid templating language (`site.static_files`) to dynamically read the repository's directory structure at build time. The resulting file list is passed into a vanilla JavaScript array. Client-side JavaScript then uses Regular Expressions to parse the file names, extract the experiment numbers, pair the manuals with their respective calculators, and render the CSS Grid UI in numerical order.

### Adding New Labs
To add new materials to the site, no code modification to `index.html` is necessary. Simply upload the files to the root of the repository adhering strictly to the following naming conventions:

* **Calculators:** `labXcalc.html` (e.g., `lab9calc.html`)
* **Manuals:** `Lab X manual.pdf` (e.g., `Lab 9 manual.pdf`)

Committing these files to the `main` branch will automatically trigger a GitHub Pages rebuild. The new files will be detected and a new card will be generated on the live site automatically.

## License and Copyright Notice

This repository contains two distinct categories of intellectual property, which are licensed differently:

**1. The Source Code and Site Assets**

All original HTML, CSS, JavaScript, and Markdown files (including this `README.md`), as well as any original site assets (such as favicons), are licensed under the **Liberty-ShareAlike Public License (LSA-1.0)**.
* You may use, share, and adapt this material for any purpose.
* If you distribute adaptations, you must license them under LSA-1.0 and include the full license text or a stable link to it. No attribution is required. No additional restrictions or DRM may be applied.
* See the `LICENSE` file for the full text of the LSA-1.0 license.

**2. The Lab Manuals (PDFs)**

The `Lab X manual.pdf` files are the intellectual property of Patrick McDougall and the Butte College Department of Physics (Last updated: January 30, 2026). They are not covered by the LSA-1.0 license. They are provided here strictly for educational reference. All rights to the text, formulas, and images within those documents belong to their original authors.
