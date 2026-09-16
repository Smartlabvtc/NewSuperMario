# Memory

- The original repository contained only one `index.html` with a basic canvas prototype and no package manager or build tool.
- The implementation therefore stays dependency-free and is intentionally easy to run with `python3 -m http.server` or any static host.
- Generated assets are kept small in number and used in the runtime: the art-direction reference appears on the start card, and the transparent princess appears in the victory card.
- Procedural WebAudio is preferable to bundled music files here: it keeps the repository lightweight and still provides feedback while respecting browser audio unlock rules.
- The stage is designed to be solvable with the default movement speed and jump arc. The `?demo` mode is a visual QA helper, not a competitive gameplay mode.
- Copyright-safe art direction uses original silhouettes and a new neon arcade identity rather than copying a specific branded character design.
- Mobile controls use pointer events with pointer capture, so holding left or right continues movement and releasing, cancelling, leaving, or losing capture always stops it. The control dock is fixed above the safe-area inset and remains usable in portrait and landscape layouts.
