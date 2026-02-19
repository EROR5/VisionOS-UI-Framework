https://github.com/EROR5/VisionOS-UI-Framework/releases

[![Releases](https://img.shields.io/badge/Releases-View%20Release%20Page-blue?style=for-the-badge&logo=github)](https://github.com/EROR5/VisionOS-UI-Framework/releases)

# VisionOS UI Framework: 3D UI, Spatial Patterns, SwiftUI, Accessible Core

![VisionOS UI Framework hero](https://images.unsplash.com/photo-1523411978144-2c6f9b1d5f3c?auto=format&fit=crop&w=1400&q=80)

A complete UI framework for VisionOS. It brings spatial computing patterns and 3D interface components to your apps. The design emphasizes clean architecture, performance, accessibility, and developer happiness. Build immersive apps with 3D controls, spatial gestures, and scalable UI that fits the VisionOS paradigm.

- Theme: spatial UI, RealityKit integration, and SwiftUI-friendly APIs.
- Audience: iOS/macOS developers shipping apps for VisionOS and AR experiences.
- Goal: reduce boilerplate, improve consistency, and enable fast iteration in spatial interfaces.

Table of contents
- Overview
- Core concepts
- Getting started
- Architecture and modules
- Components library
- Patterns and best practices
- Accessibility
- Performance and testing
- RealityKit and rendering
- Examples and tutorials
- Build, CI, and release process
- Localization and internationalization
- Theming and customization
- Contributing
- License
- FAQ
- Release notes

Overview
VisionOS UI Framework provides a modular set of 3D UI components designed for spatial interfaces. It targets VisionOS users who want a cohesive, accessible, and high-performance UI layer that fits naturally into spatial apps. The framework ships with a clean architecture, testable modules, and a robust set of patterns for spatial gestures, anchors, and interactions.

Key goals
- Consistency: a uniform look and interaction model across apps.
- Clarity: components with clear state, behavior, and life cycle.
- Accessibility: inclusive experiences with voiceover, high-contrast options, and scalable UI.
- Performance: lean rendering paths, batched updates, and minimal CPU usage.
- Extensibility: a modular API that lets you swap themes, components, or rendering backends.

Core concepts
- Spatial UI components: 3D controls, panels, HUDs, and modals designed to live in a 3D space.
- Spatial gestures: native support for gesture patterns typical to VisionOS, including air gestures and controller interactions.
- RealityKit integration: components render and interact within RealityKit scenes, with clean boundaries from SwiftUI where appropriate.
- Clean architecture: separation of concerns, testable modules, and explicit dependencies.

Getting started
Prerequisites
- macOS with the latest Xcode version that supports VisionOS development.
- Swift package manager for dependency resolution.
- A VisionOS-capable device or simulator for testing and preview.

Install and integrate
- The framework is distributed via Swift Package Manager. Add the package as a dependency to your VisionOS project.
- Example (SwiftPM):
  - In your Xcode project, go to File > Swift Packages > Add Package Dependency.
  - Enter the repository URL: https://github.com/EROR5/VisionOS-UI-Framework.git
  - Choose the supported version range and add the framework modules you need.

- The Releases page contains downloadable assets for convenience. From this page you can download assets and run installers if you prefer a packaged approach. For example, an asset named VisionOS-UI-Framework-1.0.0.zip may be provided for quick setup. After downloading, extract or run the installer as appropriate for your environment. This is the recommended path if you want a quick start in a standalone environment.

Downloads and release assets
The releases page hosts packaged assets and update notes. You can download a ready-to-run asset if you prefer, and then follow the on-screen instructions to install or integrate it into your project. For reference, the assets are available at the releases URL:
https://github.com/EROR5/VisionOS-UI-Framework/releases

If you need a direct path idea, you might look for a file like VisionOS-UI-Framework-1.0.0.zip and run the installer or unzip it, then follow the included README for integration steps. The exact asset names may vary by version. You can always visit the Releases section for the latest files.

Architecture and modules
- Core: foundational utilities, type safety, and shared helpers.
- UIKit3D: the 3D UI components such as buttons, sliders, toggles, menus, cards, panels, and HUDs.
- SpatialPatterns: gestures, anchors, and interaction models for spatial work.
- RealityKitBridge: glue code to render and interact with RealityKit scenes.
- Accessibility: features that enable VoiceOver support, dynamic type, and high-contrast visuals.
- DesignTokens: color, typography, shadows, and material definitions that ensure a cohesive look.
- Testing: unit tests, UI tests, and performance tests.
- Examples: example apps and sample scenes to illustrate usage.

Component library
- 3D Button: pressable, tactile-looking button rendered in 3D space.
- Spatial Slider: a handle that users can drag in 3D space to adjust values.
- Spatial Toggle: a switch that provides a discrete state in three dimensions.
- 3D Card: a floating card with interactive content and actions.
- Spatial Panel: a panel that hosts content in a 3D region with scroll support.
- HUD Elements: heads-up display for context, status, or quick actions.
- Menus and Toolbars: contextual menus that adapt to space and perspective.
- Overlay and Modal: layered UI that respects depth and occlusion.
- Accessibility-friendly controls: larger hit areas, clear focus indicators, and text scaling.

Usage example
Code samples illustrate how to compose 3D UI within a VisionOS scene. The framework favors a SwiftUI-like approach where appropriate, with a RealityKit-backed rendering path for actual 3D content.

- Basic 3D button in a scene:
  - Import the framework modules.
  - Create a SpatialButton and attach actions for onTap or onHover.
  - Add the button to your 3D scene graph with proper anchoring so it remains stable in the user’s space.

- Spatial slider usage:
  - Bind a value to a Swift property.
  - Add velocity and snapping behavior to provide tactile feedback.
  - Ensure accessibility semantics reflect the current value.

- View composition:
  - Combine 3D UI components with RealityKit entities to produce rich experiences.
  - Use the DesignTokens to stay consistent with color, typography, and elevation across components.

Example (pseudo-code)
import VisionOSUIFramework
import RealityKit
import SwiftUI

struct SpatialDemoView: View {
  @State private var volume: Float = 0.5

  var body: some View {
    ZStack {
      RealityKitSceneView(scene: .constant(makeScene(volume: volume)))
      VStack {
        SpatialSlider(value: $volume, min: 0, max: 1)
          .frame(width: 0.2)
        SpatialButton(title: "Play") { /* trigger play */ }
      }
    }
  }
}

This is a simplified sketch. Real usage shows you how to compose components in a 3D space with anchors, gestures, and event handling. The framework includes sample apps you can run to see concrete patterns in action. It also provides tooling for debugging spatial layouts, measuring performance, and validating accessibility compliance.

Patterns and best practices
- Spatial anchoring: anchor your UI to fixed or dynamic spatial references to maintain stable interaction zones. Anchors help keep controls aligned with the user’s environment, even as the user moves.
- Depth and occlusion: manage depth consistently so elements appear at the right distance. Use shadows and occlusion hints to give a natural sense of space.
- Interaction models: design UI with predictable gesture patterns. Provide alternative input methods so scenarios work with controllers, hands, and gaze.
- State management: keep UI state explicit. The framework provides observable properties and a clear lifecycle for components.
- Accessibility-first design: scale text where appropriate, expose accessible names, and ensure focus indicators are visible in all states.

Accessibility
- VoiceOver support: all interactive controls expose accessible labels and traits.
- Dynamic type: text scales in response to user preferences.
- High contrast: themes provide high-contrast options for readability.
- Inclusive hit areas: touches and pointer targets stay comfortably sized in 3D space.
- Keyboard and controller navigation: while VisionOS emphasizes spatial interactions, there are patterns to support broader input devices for accessibility and testing.

Performance and testing
- Rendering performance: components minimize redraws by using a clear separation of state and presentation.
- Memory usage: components are designed to allocate minimally and reuse resources when possible.
- Responsiveness: interactions are short and snappy; visual feedback appears quickly to confirm user actions.
- Testing strategy: unit tests target business logic, while UI tests validate interaction flows in VR/AR space where possible.

RealityKit and rendering
- RealityKitBridge provides a clean boundary between SwiftUI-style declarations and RealityKit rendering. You can build a scene in RealityKit and layer VisionOS UI elements on top, or render 3D UI components directly.
- Scene management: scenes are modular, with explicit life cycles. Scenes load assets on demand to reduce startup time.
- Lighting and materials: use design tokens to apply consistent lighting, color, and surface materials.

Tutorials and guides
- Getting started tutorials: step-by-step guides to create a simple VisionOS app with a 3D button and a panel.
- Advanced patterns: how to implement spatial gestures, fluid layouts, and dynamic content.
- Accessibility tutorials: adding VoiceOver labels, adjustable text sizes, and high-contrast themes.
- Performance checks: how to profile frame times, memory, and surface quality in a VisionOS scene.

Demos and examples
- The repository ships with demo apps that show common patterns: a 3D menu, a dashboard panel, and an in-scene control set.
- Each demo includes a readme with instructions to run on device or in a simulator, plus notes on how to adapt to your own project.

Build, CI, and release process
- Continuous integration: automated builds on main and PRs, with tests for core modules.
- Code quality: linting and static analysis run as part of the pipeline.
- Release workflow: on merging to main, a release is generated with updated assets and changelog entries. The Releases page hosts the downloadable assets and release notes.

Localization and internationalization
- Localizable strings: components adopt a localization workflow with .strings files.
- Right-to-left support: UI layout adapts to RTL languages where applicable.
- Font scaling: dynamic type and accessibility features extend to all localized strings and controls.

Theming and customization
- Design tokens: a single source of truth for color, elevation, typography, and spacing.
- Theme switching: switch themes at runtime or per scene to support branding needs.
- Custom components: you can build your own 3D components on top of the framework, using the same patterns and lifecycles.

Usage patterns and migration
- If you come from a UIKit or SwiftUI background, you’ll find a familiar feel in the API surface, with adjustments for 3D space and spatial interactions.
- Migration guidance includes mapping common UI patterns to their VisionOS 3D counterparts, with notes on accessibility and performance trade-offs.

Testing and quality assurance
- Unit tests cover business logic and state management.
- UI tests simulate user interactions in a limited 3D context, with recommendations for manual testing in the VisionOS simulator.
- End-to-end tests validate critical flows such as opening a panel, adjusting a slider, and confirming an action.

Documentation and API references
- The project ships with a comprehensive API reference, inline documentation, and practical usage examples.
- Each module includes developer notes about design decisions, edge cases, and extension points.
- You’ll also find a design guide that explains typography, color usage, and spacing across components.

Continuous improvement and roadmap
- The roadmap includes expanding the components library, improving accessibility features, and refining performance for complex scenes.
- Community feedback and contributed patterns shape the future of the framework.
- Regular updates align with VisionOS SDK releases and new RealityKit features.

Code organization and contribution model
- Each module is a standalone Swift package with clear dependencies.
- Public APIs are stable and versioned; breaking changes are documented in release notes.
- Contributions follow a straightforward flow: open a pull request with tests, review, and merge after approval.

Contributing
- We welcome contributions from developers who want to improve spatial UI on VisionOS.
- Follow these guidelines:
  - Start with an issue or feature request to align with project goals.
  - Create small, testable commits that describe the change.
  - Include unit tests for new functionality.
  - Update documentation and add examples if needed.
  - Keep code style consistent with the project’s conventions.
- If you want to discuss ideas or ask questions, open an issue or join the project discussions.

License
- The project uses a permissive license suitable for open-source collaboration. See LICENSE for details.

FAQ
- Is this framework tied to a specific VisionOS SDK version? It’s designed to align with current VisionOS SDKs, with updates to support newer versions as they’re released.
- Can I use this with a SwiftUI view? Yes. The framework integrates with SwiftUI where it makes sense, and RealityKit paths are provided for 3D rendering.
- How do I test accessibility features? Use the built-in accessibility utilities in macOS and VisionOS, verify VoiceOver labeling, and test dynamic type across 3D components.
- Where can I find additional examples? The Examples module includes sample projects and tutorials. Look for the README in the Examples directory for more guidance.

Release notes
- Release notes live on the Releases page. They document new features, fixes, and breaking changes with version numbers. Always review the latest notes before upgrading dependencies or adopting new patterns.

Changelog
- The changelog tracks significant changes from one release to the next. It helps teams plan migrations and communicate improvements to stakeholders.

Roadmap
- Expand the components library with new controls tailored to VisionOS interactions.
- Improve cross-device consistency for interactions and gestures.
- Enhance accessibility tooling and automated checks.
- Provide more comprehensive sample apps that demonstrate end-to-end workflows.
- Improve performance profiling tools and diagnostics in the IDE.

Additional considerations
- Platform compatibility: VisionOS, RealityKit, and SwiftUI are central to the framework. Always verify compatibility with your target OS version.
- Project structure: keep your app’s code modular to simplify upgrades and testing.
- Dependency management: Swift Package Manager simplifies integration, but it’s important to pin versions to avoid unexpected API changes.

Releases and assets
- The Releases page is where you’ll find the latest bundles, example apps, and assets needed for quick start. If you’re starting fresh, check the latest release assets and follow the included setup instructions.
- The link to the releases page is provided again here for quick access: https://github.com/EROR5/VisionOS-UI-Framework/releases

Appendix: quick-start checklist
- Ensure you have the latest Xcode and VisionOS SDK installed.
- Add the VisionOS UI Framework as a Swift Package dependency.
- Import the framework modules into your VisionOS project.
- Add a sample 3D UI to your scene and verify it renders correctly in space.
- Test accessible labeling and dynamic type scaling on different devices.
- Run performance tests to ensure smooth frame rates in your scenes.
- Review the Releases page for any asset downloads and installer instructions.

Appendix: glossary
- VisionOS: Apple’s platform for spatial computing and immersive experiences.
- RealityKit: A framework for rendering and interacting with AR/VR content in 3D space.
- SwiftUI: A modern UI framework that emphasizes declarative UI and simple state management.
- Spatial gestures: Gestures that occur in 3D space, including air gestures and controller inputs.
- Design tokens: Centralized definitions for color, typography, spacing, and elevation.

Note on the releases link
- The specific URL for releases is provided above and also appears again in the Downloads section. For quick access, visit the releases page to download assets and review release notes: https://github.com/EROR5/VisionOS-UI-Framework/releases

End of document