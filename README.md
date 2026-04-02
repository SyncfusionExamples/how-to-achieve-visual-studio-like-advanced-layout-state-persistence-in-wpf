# Visual Studio-like Advanced Layout State Persistence in WPF

This sample shows how to build a Visual Studio-style WPF workspace using the Syncfusion DockingManager and persist the full layout between sessions. It demonstrates docked tool windows, tabbed documents, floating panes, auto-hidden panels, and reliable save/load of layout state so users return to their preferred arrangement every time.

## Features
- Dock, float, document, and auto-hidden window states
- Drag-and-drop docking with dock hints and live preview
- Tabbed document interface with horizontal/vertical tab groups
- Per-pane size preferences in docked mode (DesiredWidthInDockedMode, DesiredHeightInDockedMode)
- Optional native float windows for unrestricted sizing
- Pin/unpin, close/restore, and disable floating for specific panes
- Layout persistence: save and load docking state between sessions
- Theming support (e.g., VS2010 style) and styling extensibility

## Getting Started
1. Create a new WPF project in Visual Studio (e.g., Docking-StatePersistence).
2. Install NuGet package: Syncfusion.Tools.WPF.
3. Add the Syncfusion XML namespace in XAML: `xmlns:syncfusion="http://schemas.syncfusion.com/wpf"`.
4. Place a `DockingManager` in your Window/Page to host panes.
5. Add child content (e.g., ContentControl/UserControl) and set attached properties:
   - `syncfusion:DockingManager.Header` for pane titles
   - `syncfusion:DockingManager.State` (Dock, Document, AutoHidden, Float)
   - `syncfusion:DockingManager.SideInDockedMode` and `TargetNameInDockedMode` to position panes
   - `DesiredWidthInDockedMode` and `DesiredHeightInDockedMode` for sizing
6. Apply a theme using `syncfusion:SkinStorage.VisualStyle` (e.g., `VS2010`).

## Layout Persistence
Persisting layout allows users to resume where they left off.

- Save layout: call `DockingManager.SaveDockState(...)` or enable `PersistState`.
- Load layout: call `DockingManager.LoadDockState(...)` at startup.
- Choose storage: file, stream, or custom settings store.
- Handle versioning: provide defaults when schema changes between app versions.
- Optional: hook persistence events to validate or skip panes that are no longer available.

### Typical flow
- On app close: serialize the current docking layout to a file in AppData.
- On app start: if a saved file exists, load it; otherwise, create the default layout in XAML/code.

## Usage Tips
- Group documents programmatically with `CreateHorizontalTabGroup` and `CreateVerticalTabGroup`.
- Enable familiar drag behavior with `IsVS2010DraggingEnabled`.
- Allow double-click to float documents using `EnableDocumentToFloatOnDoubleClick`.
- Use `UseNativeFloatWindow` for desktop-like floating windows across monitors.
- Disable floating per pane when needed (e.g., critical tool windows).
- Always wrap load operations with error handling and fall back to a safe default layout.

## About the sample
This README accompanies a sample that demonstrates a familiar Visual Studio-like workspace where users can dock, pin, unpin, float, tab, and restore panes effortlessly, with robust layout persistence for a consistent, personalized experience.
