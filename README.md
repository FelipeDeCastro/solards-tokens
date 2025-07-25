# SolarDS Tokens

This repository serves as the **design-focused** token storage for the Solar Design System, acting as the bridge between design tokens created in [Tokens Studio](https://tokens.studio/) and their transformation for Figma workflows. [Supernova](https://supernova.io/) integrates directly with Tokens Studio for development pipeline distribution.

> **⚠️ Temporary Solution**: This GitHub repository serves as a temporary token storage solution and will be replaced by [app.tokens.studio](https://app.tokens.studio) in the future, which will provide native cloud storage and enhanced collaboration features.

## Overview

This repository acts as the **design source of truth** for design tokens, with the following workflow:

- 🎨 **Token Creation**: Main design tokens are created and maintained using Tokens Studio
- 🔄 **Figma Synchronization**: Tokens Studio transforms and syncs tokens to match your Figma file structure needs
- � **Supernova Integration**: Supernova connects directly to Tokens Studio for token consumption
- ⚡ **Multi-Platform Output**: Supernova generates Tailwind and MUI code outputs for developers

## How It Works

1. **Token Creation**: Design tokens are created and maintained in Tokens Studio as the primary authoring tool
2. **Token Transformation**: Tokens Studio processes and transforms tokens to match your specific Figma file structure requirements
3. **GitHub Sync**: Tokens are synced from Tokens Studio to this repository for storage purpose
4. **Supernova Integration**: Supernova integrates directly with Tokens Studio to access the source tokens
5. **Development Pipelines**: Supernova generates code outputs for two pipelines:
   - **Tailwind CSS** pipeline for utility-first styling
   - **Material-UI (MUI)** pipeline for React component systems
6. **Developer Consumption**: Development teams consume tokens through Supernova's generated outputs

## Repository Structure

```
solards-tokens/
├── tokens/                 # Figma-ready design token JSON files
│   ├── core.json          # Core design tokens (colors, typography, spacing)
│   ├── semantic.json      # Semantic tokens (primary, secondary, etc.)
│   ├── component.json     # Component-specific tokens
│   └── themes/            # Theme-specific token variations
├── $themes.json           # Theme configuration file (Tokens Studio)
├── $metadata.json         # Token metadata and aliases (Tokens Studio)
└── README.md             # This file
```

> **Note**: The structure above represents tokens optimized for Figma consumption. This repository serves as the design-focused storage, while Supernova integrates directly with Tokens Studio for development pipeline generation.

## Token Organization

### Core Tokens
Foundation tokens that define the basic design properties:
- Colors (primitives)
- Typography scales
- Spacing units
- Border radius values
- Shadow definitions

### Semantic Tokens  
Contextual tokens that reference core tokens:
- Primary/secondary colors
- Success/warning/error states
- Text hierarchy tokens
- Layout spacing tokens

### Component Tokens
Component-specific tokens for consistent UI elements:
- Button variants
- Form elements
- Card components
- Navigation elements

### Themes
Multiple theme variations (light/dark, brand variations) stored as separate configurations, optimized for Figma usage and Supernova transformation.

## Design Workflow

### Token Authoring (Tokens Studio)
1. **Primary Tool**: Use Tokens Studio as your main token creation and management interface
2. **Token Organization**: Create and organize tokens following design system principles
3. **Figma Optimization**: Configure token transformations to match your Figma file requirements
4. **Theme Management**: Set up theme variations and token relationships

### Figma Integration
1. **Optimized Structure**: Tokens are structured specifically for seamless Figma consumption
2. **Theme Switching**: Easy theme switching within Figma design files
3. **Component Mapping**: Tokens are mapped to match Figma component needs
4. **Design Consistency**: Ensures consistent design implementation across Figma files

## Setup Instructions

### For Design Team

1. **Install Tokens Studio**: Set up [Tokens Studio](https://tokens.studio/) as your primary token authoring tool
2. **Configure GitHub Sync**: 
   - Navigate to Tokens Studio Settings → Sync providers → Add new → GitHub
   - Use repository: `weareplanet/solards-tokens`
   - Set branch: `main`
   - Set token storage location: `tokens` (folder)
3. **Figma Plugin Setup**: Install the [Tokens Studio Figma plugin](https://www.figma.com/community/plugin/843461159747178946)
4. **Initial Sync**: Configure token transformations for your Figma file structure and perform initial sync

### For Supernova Integration

1. **Tokens Studio Connection**: Connect Supernova directly to your Tokens Studio workspace/account
2. **Pipeline Configuration**: Set up two code generation pipelines:
   - **Tailwind Pipeline**: Configure for utility-first CSS output
   - **MUI Pipeline**: Configure for React Material-UI component system
3. **Token Mapping**: Map design tokens to appropriate development token formats
4. **Output Distribution**: Configure how generated tokens are distributed to development teams

## Sync Workflow

### Design Token Updates (Tokens Studio → GitHub)
- Make token changes in Tokens Studio interface
- Configure transformations for Figma compatibility
- Use the **Push** function to sync changes to this repository
- Changes are automatically optimized for both Figma consumption and Supernova processing

### Figma Synchronization (GitHub → Figma)  
- Use the Tokens Studio Figma plugin to **Pull** latest token updates
- Tokens are applied to Figma with the pre-configured structure
- Themes and variations are immediately available in Figma
- Perfect for collaborative design work across multiple Figma files

### Supernova Pipeline Triggers
- Supernova monitors changes directly in your Tokens Studio workspace
- Automatically triggers regeneration of Tailwind and MUI code outputs when tokens are updated
- Development teams receive updated tokens through Supernova's distribution system

## File Formats

All design tokens are stored as JSON files following the [Design Tokens Community Group](https://design-tokens.github.io/community-group/format/) specification, optimized for:
- **Figma consumption** through Tokens Studio plugin
- **Supernova processing** via direct Tokens Studio integration
- **Cross-platform compatibility** across design and development tools

Example token structure:
```json
{
  "color": {
    "primary": {
      "50": {
        "value": "#eff6ff",
        "type": "color",
        "description": "Primary color - lightest shade"
      },
      "500": {
        "value": "#3b82f6", 
        "type": "color",
        "description": "Primary color - base shade"
      }
    }
  },
  "spacing": {
    "sm": {
      "value": "8px",
      "type": "spacing"
    }
  }
}
```

## Contributing

### Design Team Workflow
- **Token Authoring**: Use Tokens Studio as the primary interface for creating and editing tokens
- **Figma Optimization**: Configure token transformations to match Figma file requirements
- **Sync Management**: Use Tokens Studio sync features to push/pull changes
- **Testing**: Test token changes in Figma before finalizing
- **Documentation**: Follow established naming conventions and document token purposes
- **Collaboration**: Coordinate with other designers when making structural changes

### Integration Teams
- **Supernova Configuration**: Maintain and update Supernova integration with Tokens Studio
- **Pipeline Monitoring**: Ensure Tailwind and MUI outputs are generating correctly
- **Token Mapping**: Update token transformations for development consumption
- **Quality Assurance**: Verify that tokens flow correctly from Tokens Studio to development outputs

## Architecture Overview

```
┌─────────────────┐    ┌──────────────────┐    
│   Tokens Studio │────│  GitHub Repo     │    
│   (Authoring)   │    │  (Design Storage)│    
└─────────┬───────┘    └──────────────────┘    
          │                                     
          │              ┌─────────────────┐    
          └──────────────│      Figma      │    
          │              │   (Design Files)│    
          │              └─────────────────┘    
          │                                     
          │              ┌─────────────────┐    
          └──────────────│    Supernova    │    
                         │   (Transform)   │    
                         └─────────┬───────┘    
                                   │            
                        ┌─────────▼─────────┐   
                        │   Development     │   
                        │    Pipelines      │   
                        │                   │   
                        │ • Tailwind CSS    │   
                        │ • Material-UI     │   
                        └───────────────────┘   
```

## Support & Resources

### Design Tools
- 📖 [Tokens Studio Documentation](https://docs.tokens.studio/)
- 🎨 [Tokens Studio Figma Plugin](https://www.figma.com/community/plugin/843461159747178946)
- 💬 [Tokens Studio Community Slack](https://tokens.studio/slack)

### Development Pipeline
- � [Supernova Platform](https://supernova.io/)
- 🎨 [Tailwind CSS Documentation](https://tailwindcss.com/)
- ⚛️ [Material-UI Documentation](https://mui.com/)

### Token Standards
- � [Design Tokens Community Group](https://design-tokens.github.io/community-group/format/)
- 🔧 [Style Dictionary](https://styledictionary.com/) (for reference)

## License

This project is part of the Solar Design System. Please refer to the main design system documentation for licensing information.

---

**Important Notes**: 
- This repository is optimized for **design workflows** and **Supernova integration**
- Developers should consume tokens through **Supernova's generated outputs**, not directly from this repository
- Requires Tokens Studio Pro license for multi-file sync functionality and theme support
- Free Tokens Studio users will have read-only access to tokens created by Pro users
