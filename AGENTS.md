# AGENTS.md — Shopify BYD Initial Homepage Development

## 1. Objective

Develop an initial, full-page Shopify Online Store 2.0 homepage based on the supplied BYD Indonesia reference.

- Reference URL: https://www.byd.com/id
- Primary source materials: supplied HTML, HAR, and screenshots.
- Initial goal: implement the complete page structure and achieve strong overall visual similarity.
- This is a first-pass implementation, not the final pixel-perfect stage.
- Detailed section-by-section refinement will be performed later.
- Keep the implementation responsive, modular, maintainable, and compatible with the existing Shopify theme.

## 2. Reference Materials

The reference materials are stored outside the Shopify theme in:

`C:\Raihan Working Folder\Shopify\BYD Development\Referensi`

Use this folder as the source for reference HTML, HAR, screenshots, and any related reference notes.

- Inspect only the files relevant to the target page.
- Use HTML to understand page structure, text, classes, and section order.
- Use HAR to identify potentially relevant images, fonts, CSS, JavaScript, and other network resources.
- Use screenshots as the primary visual comparison target.
- Do not assume every HAR entry is needed or that every request has a retrievable response body.
- Do not copy analytics, tracking pixels, session identifiers, or unrelated third-party scripts into Shopify.
- If the reference folder or a required file cannot be accessed from the current workspace, report the specific blocker instead of assuming its contents.
- Do not put reference HTML or HAR files inside Shopify's `assets/` directory.

## 3. Initial Development Workflow and Time Limit

1. Inspect the existing Shopify theme structure before editing.
2. Check for existing templates, sections, snippets, CSS, and assets that can be reused.
3. Review the supplied reference files and identify the main page sections, design patterns, assets, and visible interactions.
4. Create a concise implementation plan, then begin coding once enough evidence is available.
5. Implement the complete initial homepage, including all major sections in the correct order.
6. Run the available basic QA checks and report remaining issues.

Time and scope rules:

- Target approximately 8–10 minutes for the initial implementation pass.
- Prioritize complete page structure, major layout, imagery, typography, colors, and responsive behavior.
- Do not spend excessive time perfecting individual sections at this stage.
- Do not perform long browser/DOM crawling loops or repeatedly inspect the same files.
- Do not conduct broad investigations or web searches unless explicitly requested.
- Do not refactor unrelated parts of the theme.
- Do not publish changes or overwrite the live storefront. Work only in the current development/local theme.
- If the time target is insufficient to finish everything, implement the highest-impact elements first and clearly report what remains.

## 4. Initial Fidelity and Later Refinement

For the first pass:

- Recreate the whole page at a structural and visual level.
- Match the reference's major section order, layout, imagery, typography, colors, spacing, and proportions as closely as the available evidence allows.
- Implement the main visible interactions where practical.
- Keep the code modular enough to refine individual sections later.
- Prefer a complete, coherent first pass over pixel-perfect treatment of one section while other major sections are missing.
- Do not introduce arbitrary design improvements or new sections absent from the reference.

Detailed refinement will be a separate phase. During the initial pass, avoid spending time on minor pixel-level differences, subtle hover states, or premature optimization unless they materially affect the overall result.

## 5. Responsive Behavior and Width Rules

- Treat **990px as the project breakpoint** where the layout switches to the mobile/tablet layout.
- At viewport widths **990px and below**, use the mobile/tablet layout.
- Above **990px**, use the desktop layout.
- Do not impose a fixed maximum width on the desktop page or its main content container. The desktop layout should naturally follow the available laptop/desktop viewport width.
- Use `width: 100%` where appropriate and responsive horizontal padding to prevent content from touching the viewport edges.
- Do not add a global `min-width` that forces the whole page wider than the viewport.
- Use `min-width` only for individual components when the source reference clearly requires it.
- Prevent horizontal overflow, especially at widths below 990px.
- Use responsive images and flexible grids/flex layouts so content adapts to the available screen width.
- Apply the breakpoint consistently in relevant page styles:

```css
/* Desktop */
@media (min-width: 991px) {
  /* desktop styles */
}

/* Mobile/tablet */
@media (max-width: 990px) {
  /* mobile/tablet styles */
}
```

- If the supplied source CSS proves that a specific component uses a different breakpoint, preserve the 990px project rule by default and report the evidence before deviating.

## 6. Typography

Use this font-family stack throughout the BYD page:

```css
font-family: Montserrat, Arial, "Helvetica Neue", Helvetica, sans-serif;
```

- Apply the stack consistently to headings, body text, navigation, buttons, labels, and captions unless the reference clearly shows a justified exception.
- Inspect the supplied HTML/CSS/HAR and existing theme for available Montserrat font files and actual font weights.
- Use existing font assets if available and permitted for this project.
- Do not invent font files or claim Montserrat is loaded if only fallback fonts are available.
- Match the reference typography as closely as the available evidence allows, including font size, weight, line height, letter spacing, text transform, and alignment.
- Prefer reusable CSS variables/design tokens for repeated typography values.
- Use responsive typography where needed, such as `clamp()`, while preserving the reference's visual hierarchy.

## 7. Design Tokens and CSS

- Extract source values from the supplied files where practical before styling.
- Establish reusable CSS custom properties for repeated values, including font family/weights, typography scale, line heights, spacing, colors, backgrounds, button dimensions, border radius, and breakpoint values.
- Do not guess values when they can reasonably be extracted from the supplied materials.
- If a value cannot be determined, use a reasonable visual approximation and identify it as estimated in the final report.
- Avoid repeating the same hardcoded values unnecessarily.
- Keep CSS scoped to the BYD page and its components to avoid affecting unrelated Shopify pages.
- Do not introduce a CSS framework.

## 8. Shopify Architecture

- Follow Shopify Online Store 2.0 conventions.
- Use Liquid sections and a JSON template for page composition.
- Use modular sections and snippets where useful, but do not over-engineer the first pass.
- Reuse the existing header, footer, and theme components where appropriate.
- Avoid duplicate global components if equivalent components already exist.
- Keep section schemas valid JSON and Liquid syntax valid.
- Use semantic HTML and accessible labels/alt text.
- Keep CTA destinations configurable in the Shopify theme editor where practical.
- Make routine text, image, and CTA changes manageable through the theme editor when practical.
- Preserve existing working functionality and avoid changes outside the homepage and its required dependencies.

## 9. Assets and Source Fidelity

- Use the supplied HTML, HAR, and screenshots as reference evidence.
- Check whether relevant assets already exist in the theme before adding duplicates.
- Reuse suitable source images and font files when available and authorized for this project.
- Verify that referenced assets actually exist or are accessible before using them.
- Do not assume every HAR request contains a retrievable response body.
- Do not copy analytics, tracking pixels, session identifiers, or unrelated third-party scripts.
- Preserve image proportions and use appropriate `object-fit` and responsive sizing.
- Do not use generic placeholders when suitable source assets are available.
- If an important asset is unavailable, use a clearly identifiable temporary placeholder only if needed to complete the layout, and report it.

## 10. Functional Requirements

- Implement the main visible interactions present in the reference where practical.
- Ensure links and CTAs have appropriate destinations; do not invent destinations when the intended URL is unknown.
- Use Shopify-compatible implementation for store functionality.
- Do not create decorative buttons that appear functional but do nothing.
- Do not claim an interaction works unless it has been tested.
- Prioritize the core visible behavior in this first pass; fine interaction details can be refined later.

## 11. Initial QA Checklist

Before finishing, check what is feasible in the current environment:

- [ ] The full homepage structure is present and major sections follow the reference order.
- [ ] The overall layout and major imagery resemble the reference.
- [ ] The font-family stack is `Montserrat, Arial, "Helvetica Neue", Helvetica, sans-serif`.
- [ ] The layout switches to mobile/tablet at 990px and below.
- [ ] The desktop layout follows the available viewport width without a fixed page-level `max-width`.
- [ ] No global `min-width` causes horizontal scrolling.
- [ ] Images and columns resize appropriately across screen sizes.
- [ ] No unintended horizontal overflow is visible at mobile widths.
- [ ] Main links and visible interactions have been checked where possible.
- [ ] Liquid and JSON schemas are valid.
- [ ] Existing unrelated theme pages and components remain unaffected.
- [ ] Changes have not been published to the live storefront.
- [ ] Any checks not performed are explicitly identified as not tested.

## 12. Final Report

Provide a concise report listing:

1. Files created and modified.
2. Major sections/components implemented.
3. Responsive behavior and breakpoint used.
4. Typography/font loading status.
5. Whether the reference assets were found and reused.
6. QA actually performed and its results.
7. Important visual differences, estimates, blockers, or unfinished work.
8. The highest-priority items for the later section-by-section refinement phase.

Do not claim a check was completed unless it was actually performed.
