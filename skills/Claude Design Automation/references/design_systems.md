# Design Systems in Claude Design

A design system is the foundation for consistent brand-aligned outputs in Claude Design. It contains all reusable components, styles, and guidelines that define your brand's visual identity.

## Key Components
1. **Brand Colors**: Primary and secondary color palettes with HEX codes
2. **Typography**: Font families, sizes, and hierarchy (e.g., H1: 32px, Body: 16px)
3. **UI Components**: Buttons, cards, forms with defined states (hover, active)
4. **Assets**: Logos in multiple formats (PNG, SVG), icons, illustrations
5. **Spacing System**: Padding/margin standards (e.g., 8px base unit)

## Implementation Steps
1. Gather existing brand materials (style guides, websites, marketing collateral)
2. Use the Design System Creator skill to automatically extract components
3. Manually verify and supplement any missing elements
4. Upload to Claude via the Design System tab

## Maintenance
- Update seasonally or when rebranding occurs
- Store source files in version control
- Document changes in a changelog.md file

Example structure for a tech company:
```markdown
# Acme Corp Design System
## Colors
- Primary: #3A86FF (Azure)
- Secondary: #8338EC (Purple)
## Typography
- Headings: Inter Bold
- Body: Inter Regular
## Components
- Primary Button: 12px radius, 8px padding
```