---
title: "About Darko Labs"
subtitle: "Tech Notes"
version: "v0"
date: 2024-08-31
author: "John Benson"
authorUrl: "https://john-benson.com"
license: "CC-BY-4.0"
---


## Design Philosophy
DarkoLabs embraces the constraints of monospace typography to create a unique, retro-futuristic aesthetic. Our design philosophy is built on the following principles:

1. Embrace the Grid: Every character occupies the same space, creating a natural grid that guides our layouts.
2. Simplicity in Complexity: Use basic elements to create complex designs.
3. Function Informs Form: Let the content drive the design choices.
4. Digital Nostalgia: Evoke the feeling of early computer interfaces while pushing the boundaries of modern web design.

## General Principles
1. Adhere to an 80-character line width maximum.
2. Use ASCII art and box-drawing characters for visual elements.
3. Prioritize semantic HTML with minimal custom classes.
4. Maintain consistent spacing and alignment across all elements.

## Text Formatting

### Headings
- Use Markdown headings (# for h1, ## for h2, etc.)
- Keep headings concise and under 80 characters
- Use Title Case for main headings, Sentence case for subheadings

Example:
```markdown
# Main Page Title
## Section Subtitle
### Subsection heading
```

### Paragraphs
- Wrap at 80 characters
- Use single line breaks between paragraphs
- Avoid indentation

Good example:
```
This is a paragraph that respects the 80-character limit. It wraps
naturally and maintains readability.

This is a second paragraph, separated by a single line break.
```

Bad example:
```
This paragraph ignores the 80-character limit and extends far beyond what is considered readable in our monospace design. It doesn't wrap and creates a horizontal scrollbar.

   This paragraph is indented, which breaks the left alignment and disrupts the overall grid-based layout.
```

### Lists
- Use Markdown syntax for unordered (-) and ordered (1.) lists
- Indent nested lists with 2 spaces

Example:
```markdown
- Main item 1
  - Subitem 1.1
  - Subitem 1.2
- Main item 2
  1. Ordered subitem 2.1
  2. Ordered subitem 2.2
```

### Code
- Use backticks for inline code: `code`
- Use triple backticks for code blocks with language specification:

```python
def hello_world():
	print("Hello, DarkoLabs!")
```

### Links
- Use Markdown syntax: [Link Text](URL)
- For internal links, use relative paths: [About](/about/)

## Advanced Formatting

### Tables
- Use Markdown tables
- Add class="width-min" or class="width-auto" to control column widths

Example:
```markdown
| Header 1 | Header 2 | Header 3 |
|:---------|:--------:|---------:|
| Left     | Center   | Right    |
{.width-auto}
```

Rendered result:
| Header 1 | Header 2 | Header 3 |
|:---------|:--------:|---------:|
| Left     | Center   | Right    |

### Grid Layouts
- Wrap elements in <div class="grid"> for grid layouts
- Use flexbox properties for fine-tuning

Example:
```html
<div class="grid">
  <div style="flex: 1;">Column 1 (flexible)</div>
  <div style="flex: 0 0 20ch;">Column 2 (fixed width)</div>
  <div style="flex: 2;">Column 3 (double width of Column 1)</div>
</div>
```

### Tree Structures
- Use HTML with the "tree" class

Example:
```html
<ul class="tree">
  <li>Root
	<ul>
	  <li>Branch 1
		<ul>
		  <li>Leaf 1.1</li>
		  <li>Leaf 1.2</li>
		</ul>
	  </li>
	  <li>Branch 2</li>
	</ul>
  </li>
</ul>
```

Rendered result:
<ul class="tree">
  <li>Root
	<ul>
	  <li>Branch 1
		<ul>
		  <li>Leaf 1.1</li>
		  <li>Leaf 1.2</li>
		</ul>
	  </li>
	  <li>Branch 2</li>
	</ul>
  </li>
</ul>

### ASCII Art and Diagrams
- Use <pre> tags for ASCII art and diagrams
- Use HTML entities for box-drawing characters

Example:
```html
<pre>
┌───────────────────┐
│   DarkoLabs Box   │
├───────────────────┤
│ Content goes here │
└───────────────────┘
</pre>
```

Rendered result:
<pre>
┌───────────────────┐
│   DarkoLabs Box   │
├───────────────────┤
│ Content goes here │
└───────────────────┘
</pre>

### Graphs with Gradients
- Use ASCII characters for gradient levels: ░ ▒ ▓ █
- Wrap in <pre class="ascii-graph"> tags

Example:
```html
<pre class="ascii-graph">
DarkoLabs Growth
│                    
│               ▓▓▓  
│          ▓▓▓  ▒▒▒  
│     ▓▓▓  ▒▒▒  ░░░  
│▓▓▓  ▒▒▒  ░░░  ░░░  
└─────────────────▶
 2021 2022 2023 2024
</pre>
```

### Expandable Sections
- Use HTML details/summary tags

Example:
```html
<details>
<summary>Click to expand</summary>
This content is hidden until the user clicks to expand it.
</details>
```

## Creating Cohesive Designs

To maintain a consistent look and feel across your DarkoLabs project:

1. Use a consistent header and footer structure on all pages.
2. Create a set of reusable ASCII art components for icons and decorations.
3. Maintain a consistent rhythm with your use of headings, paragraphs, and whitespace.
4. Develop a color scheme using ASCII shading characters and apply it consistently.

Example of a consistent page structure:

```
┌────────────────────────────────────────────────────────────────────────────┐
│ DarkoLabs                                                                  │
├────────────────────────────────────────────────────────────────────────────┤
│ [Home] [About] [Projects] [Contact]                                        │
├────────────────────────────────────────────────────────────────────────────┤
│                                                                            │
│ # Page Title                                                               │
│                                                                            │
│ Main content goes here...                                                  │
│                                                                            │
│ ## Section Heading                                                         │
│                                                                            │
│ More content...                                                            │
│                                                                            │
├────────────────────────────────────────────────────────────────────────────┤
│ © 2024 DarkoLabs | Privacy Policy | Terms of Service                       │
└────────────────────────────────────────────────────────────────────────────┘
```


## Accessibility Considerations

While the monospace aesthetic is core to DarkoLabs design, it's important to ensure our content remains accessible:

1. Provide text alternatives for ASCII art and diagrams.
2. Ensure sufficient color contrast for readability.
3. Use semantic HTML to improve screen reader compatibility.
4. Test navigation and interaction using only a keyboard.
5. Consider providing a 'readability mode' that uses a proportional font for long-form content.

## Adapting for Different Content

The DarkoLabs monospace design can be adapted for various content types:

- Long-form articles: Use clear heading hierarchy and generous white space to improve readability.
- Data-heavy content: Leverage ASCII tables and graphs for clear data presentation.
- Portfolio sites: Use ASCII art frames to showcase images or project thumbnails.
- Documentation: Combine expandable sections with tree structures for easy navigation.

## Future Considerations

As web technologies evolve, consider how the DarkoLabs design might adapt:

1. Explore using CSS Grid for more complex layouts while maintaining the monospace aesthetic.
2. Investigate WebGL or Canvas for creating more dynamic ASCII art experiences.
3. Consider developing custom web fonts for more consistent rendering across devices.
4. Explore ways to incorporate responsive design principles without breaking the monospace grid.

## Polishing Checklist
1. Ensure all text fits within 80 characters width
2. Convert any complex layouts to appropriate HTML with correct classes
3. Replace standard dashes/lines with box-drawing characters in diagrams
4. Verify all ASCII art and diagrams use consistent characters
5. Check that all expandable sections use details/summary tags
6. Ensure all tables have appropriate width classes
7. Verify that all code blocks specify the language for syntax highlighting
8. Check that all links are functional and use relative paths for internal links
9. Ensure front matter is complete and accurate
10. Verify that any images have descriptive alt text
11. Run the content through a Markdown linter to catch any syntax issues
12. Review the overall layout for consistency with the monospace grid
13. Check that all custom classes (e.g., 'tree', 'grid') are used appropriately
14. Ensure all ASCII graphs use the correct gradient characters
15. Verify that no standard HTML elements break the monospace layout
16. Check for consistent use of ASCII art components across pages
17. Verify that the page structure follows the established template
18. Ensure consistent use of whitespace and line breaks for readability
19. Review headings for proper hierarchy and consistent styling
20. Check that all interactive elements (e.g., expandable sections) are working correctly

