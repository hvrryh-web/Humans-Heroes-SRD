# Project Status and Planning

## Current goals and scope
- The repository hosts the Humans & Heroes system reference documents as static HTML and JavaScript pages for character creation, rules, and examples.
- Existing documentation is minimal: the root README only links to the published site, so project goals, setup steps, and testing guidance are not yet captured in-repo.

## Completion and documentation check
- Content pages and supporting scripts are present, but there is no documented project plan or definition of done for features, nor any instructions on how to verify pages locally.
- Testing utilities (`testCase.js`, `testTools.js`) exist, yet there is no documented workflow for running them or expectations for coverage.
- No contributor guide or installation steps are available, leaving onboarding and review criteria unspecified.

## Recommended next development stage
1. **Document project scope and objectives**: add a fuller README describing the SRD, site structure, and contribution expectations.
2. **Stabilize testing harness**: formalize how to execute the JavaScript/DOM tests (e.g., a dedicated HTML runner and npm script) and define minimal coverage for critical UI flows like character loading and advantage selection.
3. **Automate quality checks**: introduce linting (ESLint) and formatting (Prettier) to reduce review overhead across the many JavaScript files.
4. **Content validation passes**: schedule periodic review to ensure rules text in HTML stays synchronized with source materials, with a checklist for new/updated pages.

## Testing environment needs
- **Prerequisites**: Node.js ≥18, npm, and a modern browser for manual verification of the HTML pages.
- **Local serve-and-test loop**:
  1. `npm init -y` to create a package manifest.
  2. Add developer dependencies: `npm install --save-dev http-server jest jsdom @testing-library/dom`.
  3. Serve the site for manual checks: `npx http-server . -p 8080` then open `http://localhost:8080/index.html` in a browser.
  4. Create a Jest configuration that uses `jsdom` so DOM-driven utilities (e.g., `DomUtil.changeValue`) can be exercised without a real browser.
  5. Add npm scripts such as "test": "jest" and "start": "http-server . -p 8080" to standardize workflows.
- **Test coverage priorities**: data loading/saving flows in `Main`/`Loader`, advantage and power selection widgets, and error messaging collected via `Messages`.

## Migration and installation plan for art generation tools
1. **Select tooling and licensing**: choose an art generation solution (e.g., local Stable Diffusion or hosted API) that aligns with the SRD's licensing requirements and privacy expectations.
2. **Environment preparation**: document GPU/CPU needs, install guides, and required Python or Node dependencies in a dedicated `art/` subdirectory with its own README.
3. **Integration path**:
   - Define input/output contracts for generated assets (file formats, resolution, metadata).
   - Add a build step or script that can place generated assets into the site's image directories without overwriting existing content.
   - Track assets and prompts in version control where licensing allows; otherwise, store pointers and hashes.
4. **Migration steps**:
   - Inventory current artwork and map it to generation needs (new vs. replacement pieces).
   - Batch-generate assets in a staging area, review for quality/licensing, then promote to production directories.
5. **Validation and rollout**:
   - Create a checklist for visual QA (layout fit, accessibility text, file sizes) before merging new assets.
   - Add monitoring for broken links or missing images post-migration using an automated link checker.
6. **Ongoing maintenance**: schedule periodic model updates, retrain or fine-tune as style requirements evolve, and record provenance for every generated asset.
