# Windhawk

Windhawk **1.7.3** · All mods enabled · Updated **2026-10-01**.

**Import:** Install the mod → **Advanced → Mod settings** → paste JSON → **Save**.

## Installed mods

| Mod | Version | Settings |
| --- | --- | --- |
| [Windows 11 Start Menu Styler](#windows-11-start-menu-styler) | 1.7 | Below |
| [Windows 11 Taskbar Styler](#windows-11-taskbar-styler) | 1.10 | Below |
| [Taskbar height and icon size](#taskbar-height-and-icon-size) | 1.3.10 | Below |
| [Taskbar Labels for Windows 11](#taskbar-labels-for-windows-11) | 1.5 | Below |
| [Remove Taskbar Window Suffixes](#remove-taskbar-window-suffixes) | 1.1.1 | Below |
| [Win32 UI Modernizer](#win32-ui-modernizer) | 1.0.2 | Below |
| [Invisible Window Borders](#invisible-window-borders) | 1.0.0 | Below |
| [Modernize Folder Picker Dialog](https://windhawk.net/mods/modernize-folder-picker-dialog) | 1.0.0 | None |
| [Custom Desktop Watermark](#custom-desktop-watermark) | 1.2.0 | Below |
| [Turn off change file extension warning](https://windhawk.net/mods/extension-change-no-warning) | 1.0.1 | None |

## Windows 11 Start Menu Styler

[Mod](https://windhawk.net/mods/windows-11-start-menu-styler) · **v1.7** — Glass borders, rounded search boxes, subtle hover effects, and smooth transitions.

<details>
<summary>Configuration</summary>

```json
{
  "controlStyles[0].target": "Border#ContentBorder@CommonStates > Grid > Border#BackgroundBorder",
  "controlStyles[0].styles[0]": "BorderThickness=0.3,1,0.3,0.3",
  "controlStyles[0].styles[1]": "BorderBrush@PointerOver:=$elementGlassyBorder",
  "controlStyles[0].styles[2]": "BorderBrush@Pressed:=$elementGlassyBorder",
  "controlStyles[1].target": "Button > Grid@CommonStates > Border#BackgroundBorder",
  "controlStyles[1].styles[0]": "BorderThickness=0.3,1,0.3,0.3",
  "controlStyles[1].styles[1]": "BorderBrush@PointerOver:=$elementGlassyBorder",
  "controlStyles[1].styles[2]": "BorderBrush@Pressed:=$elementGlassyBorder",
  "controlStyles[1].styles[3]": "BackgroundSizing=InnerBorderEdge",
  "controlStyles[2].target": "StartMenu.CategoryControl > Grid > Border",
  "controlStyles[2].styles[0]": "BorderThickness=0.3,1,0.3,0.3",
  "controlStyles[2].styles[1]": "BorderBrush:=$glassyBorder",
  "controlStyles[2].styles[2]": "BackgroundSizing=InnerBorderEdge",
  "controlStyles[2].styles[3]": "Background:=<SolidColorBrush Color=\"{ThemeResource ControlFillColorDefault}\" />",
  "controlStyles[2].styles[4]": "Opacity=0.8",
  "controlStyles[3].target": "Grid#LayoutRoot",
  "controlStyles[3].styles[0]": "BackgroundTransition:=<BrushTransition Duration=\"0:0:0.100\" />",
  "controlStyles[4].target": "Border#BackgroundBorder",
  "controlStyles[4].styles[0]": "BackgroundTransition:=<BrushTransition Duration=\"0:0:0.100\" />",
  "controlStyles[5].target": "Button#Header > Border@CommonStates",
  "controlStyles[5].styles[0]": "BorderThickness=0.3,1,0.3,0.3",
  "controlStyles[5].styles[1]": "BorderBrush@PointerOver:=$elementGlassyBorder",
  "controlStyles[5].styles[2]": "BorderBrush@Pressed:=$elementGlassyBorder",
  "controlStyles[5].styles[3]": "BackgroundSizing=InnerBorderEdge",
  "controlStyles[6].target": "ListViewItem > Grid@CommonStates > Border#BorderBackground",
  "controlStyles[6].styles[0]": "BorderThickness=0.3,1,0.3,0.3",
  "controlStyles[6].styles[1]": "BorderBrush@PointerOver:=$elementGlassyBorder",
  "controlStyles[6].styles[2]": "BorderBrush@Pressed:=$elementGlassyBorder",
  "controlStyles[6].styles[3]": "BackgroundSizing=InnerBorderEdge",
  "controlStyles[7].target": "StartMenu.SearchBoxToggleButton > Grid@CommonStates > Border#BorderElement",
  "controlStyles[7].styles[0]": "CornerRadius=16",
  "controlStyles[7].styles[1]": "BorderThickness=1",
  "controlStyles[7].styles[2]": "BorderBrush:=$borderColor",
  "controlStyles[7].styles[3]": "Background@Checked:=$backgroundNormal",
  "controlStyles[7].styles[4]": "Background@CheckedPointerOver:=$backgroundHover",
  "controlStyles[7].styles[5]": "Background@CheckedPressed:=$backgroundPressed",
  "controlStyles[7].styles[6]": "BackgroundTransition:=<BrushTransition Duration=\"0:0:0.100\" />",
  "controlStyles[7].styles[7]": "Background@Pressed:=$backgroundPressed",
  "controlStyles[7].styles[8]": "Background@Normal:=$backgroundNormal",
  "controlStyles[7].styles[9]": "Background@PointerOver:=$backgroundHover",
  "controlStyles[8].target": "Button#HideMoreSuggestionsButton > Grid@CommonStates > Border#BackgroundBorder",
  "controlStyles[8].styles[0]": "Background@Normal:=$backgroundNormal",
  "controlStyles[8].styles[1]": "BorderBrush@Normal:=$elementGlassyBorder",
  "controlStyles[8].styles[2]": "BorderBrush@PointerOver:=$elementGlassyBorder",
  "controlStyles[8].styles[3]": "BorderBrush@Pressed:=$elementGlassyBorder",
  "controlStyles[8].styles[4]": "Background@PointerOver:=$backgroundHover",
  "controlStyles[8].styles[5]": "Background@Pressed:=$backgroundPressed",
  "controlStyles[8].styles[6]": "BorderThickness=0.3,1,0.3,0.3",
  "controlStyles[8].styles[7]": "Margin=2",
  "controlStyles[9].target": "Button#ShowMoreSuggestionsButton > Grid@CommonStates > Border#BackgroundBorder",
  "controlStyles[9].styles[0]": "Background@Normal:=$backgroundNormal",
  "controlStyles[9].styles[1]": "BorderBrush@Normal:=$elementGlassyBorder",
  "controlStyles[9].styles[2]": "BorderBrush@PointerOver:=$elementGlassyBorder",
  "controlStyles[9].styles[3]": "BorderBrush@Pressed:=$elementGlassyBorder",
  "controlStyles[9].styles[4]": "Background@PointerOver:=$backgroundHover",
  "controlStyles[9].styles[5]": "Background@Pressed:=$backgroundPressed",
  "controlStyles[9].styles[6]": "BorderThickness=0.3,1,0.3,0.3",
  "controlStyles[9].styles[7]": "Margin=2",
  "controlStyles[10].target": "StartMenu.FolderModal > Grid#Root > Border",
  "controlStyles[10].styles[0]": "BorderThickness=0.3,1,0.3,0.3",
  "controlStyles[10].styles[1]": "BorderBrush:=$glassyBorder",
  "controlStyles[11].target": "MenuFlyoutPresenter > Border",
  "controlStyles[11].styles[0]": "BorderThickness=1",
  "controlStyles[11].styles[1]": "BorderBrush:=$borderColor",
  "controlStyles[12].target": "Border#ContentBorder@CommonStates > Grid#DroppedFlickerWorkaroundWrapper > ContentPresenter#ContentPresenter > ContentControl > Grid#RootGrid > Border#LogoBackgroundPlate > Image#AllAppsItemLogo",
  "controlStyles[12].styles[0]": "RenderTransform@Pressed:=<ScaleTransform ScaleX=\"0.8\" ScaleY=\"0.8\" />",
  "controlStyles[12].styles[1]": "RenderTransformOrigin=0.5,0.5",
  "controlStyles[13].target": "StartDocked.NavigationPaneButton > Grid@CommonStates > Border#BackgroundBorder",
  "controlStyles[13].styles[0]": "BorderThickness=0.3,1,0.3,0.3",
  "controlStyles[13].styles[1]": "BorderBrush@PointerOver:=$elementGlassyBorder",
  "controlStyles[13].styles[2]": "BorderBrush@Pressed:=$elementGlassyBorder",
  "controlStyles[13].styles[3]": "BackgroundSizing=InnerBorderEdge",
  "controlStyles[14].target": "StartDocked.AppListViewItem > Grid@CommonStates > Border#BackgroundBorder",
  "controlStyles[14].styles[0]": "BorderThickness=0.3,1,0.3,0.3",
  "controlStyles[14].styles[1]": "BorderBrush@PointerOver:=$elementGlassyBorder",
  "controlStyles[14].styles[2]": "BorderBrush@Pressed:=$elementGlassyBorder",
  "controlStyles[14].styles[3]": "BackgroundSizing=InnerBorderEdge",
  "controlStyles[15].target": "Microsoft.UI.Xaml.Controls.DropDownButton > Grid@CommonStates",
  "controlStyles[15].styles[0]": "Background@PointerOver:=$backgroundHover",
  "controlStyles[15].styles[1]": "Background@Pressed:=$backgroundPressed",
  "controlStyles[15].styles[2]": "BorderBrush@PointerOver:=$elementGlassyBorder",
  "controlStyles[15].styles[3]": "BorderBrush@Pressed:=$elementGlassyBorder",
  "controlStyles[15].styles[4]": "BackgroundSizing=InnerBorderEdge",
  "controlStyles[15].styles[5]": "Background@Normal:=$backgroundNormal",
  "controlStyles[15].styles[6]": "BorderBrush@Normal:=$elementGlassyBorder",
  "controlStyles[15].styles[7]": "Padding=9,3,7,4",
  "controlStyles[16].target": "Border#ContentBorder@CommonStates > Grid#DroppedFlickerWorkaroundWrapper > ContentPresenter#ContentPresenter > ContentControl > Grid#RootGrid > Grid#LogoContainer > Image#AllAppsTileLogo",
  "controlStyles[16].styles[0]": "RenderTransform@Pressed:=<ScaleTransform ScaleX=\"0.8\" ScaleY=\"0.8\" />",
  "controlStyles[16].styles[1]": "RenderTransformOrigin=0.5,0.5",
  "controlStyles[17].target": "Border#ContentBorder@CommonStates > Grid#DroppedFlickerWorkaroundWrapper > ContentPresenter > Grid > Grid#LogoContainer > Grid",
  "controlStyles[17].styles[0]": "RenderTransform@Pressed:=<ScaleTransform ScaleX=\"0.8\" ScaleY=\"0.8\" />",
  "controlStyles[17].styles[1]": "RenderTransformOrigin=0.5,0.5",
  "controlStyles[18].target": "Grid#ContentBorder@CommonStates > Grid#DroppedFlickerWorkaroundWrapper > ContentPresenter > Grid > Grid#LogoContainer > Grid",
  "controlStyles[18].styles[0]": "RenderTransform@Pressed:=<ScaleTransform ScaleX=\"0.8\" ScaleY=\"0.8\" />",
  "controlStyles[18].styles[1]": "RenderTransformOrigin=0.5,0.5",
  "controlStyles[19].target": "ScrollViewer#MenuFlyoutPresenterScrollViewer > Border > Grid > ScrollContentPresenter > ItemsPresenter > StackPanel",
  "controlStyles[19].styles[0]": "ChildrenTransitions:=$AnimationSettings",
  "controlStyles[20].target": "FlyoutPresenter > Border > ScrollViewer > Border > Grid > ScrollContentPresenter > ContentPresenter > Border",
  "controlStyles[20].styles[0]": "BorderBrush:=$borderColor",
  "controlStyles[20].styles[1]": "BorderThickness=1",
  "controlStyles[21].target": "Button > ContentPresenter#ContentPresenter@CommonStates",
  "controlStyles[21].styles[0]": "Background@PointerOver:=$backgroundHover",
  "controlStyles[21].styles[1]": "Background@Pressed:=$backgroundPressed",
  "controlStyles[21].styles[2]": "BorderBrush@PointerOver:=$elementGlassyBorder",
  "controlStyles[21].styles[3]": "BorderBrush@Pressed:=$elementGlassyBorder",
  "controlStyles[21].styles[4]": "BorderThickness=0.3,1,0.3,0.3",
  "controlStyles[21].styles[5]": "Background@Normal=Transparent",
  "controlStyles[22].target": "Grid@SearchBoxInputStates > Border#TaskbarSearchBackground",
  "controlStyles[22].styles[0]": "CornerRadius=16",
  "controlStyles[22].styles[1]": "Background@ActiveInput:=$backgroundNormal",
  "controlStyles[22].styles[2]": "BorderBrush:=$borderColor",
  "controlStyles[22].styles[3]": "BorderThickness=1",
  "controlStyles[22].styles[4]": "Background@SearchBoxHover:=$backgroundHover",
  "controlStyles[22].styles[5]": "Background@NoFocus:=$backgroundNormal",
  "controlStyles[22].styles[6]": "BackgroundTransition:=<BrushTransition Duration=\"0:0:0.100\" />",
  "controlStyles[23].target": "Border@CommonStates > Grid#DroppedFlickerWorkaroundWrapper > ContentPresenter > Grid > Grid#LogoContainer > Image",
  "controlStyles[23].styles[0]": "RenderTransform@Pressed:=<ScaleTransform ScaleX=\"0.8\" ScaleY=\"0.8\" />",
  "controlStyles[23].styles[1]": "RenderTransformOrigin=0.5,0.5",
  "controlStyles[24].target": "Grid#ContentBorder@CommonStates > ContentPresenter > Grid > Grid#LogoContainer > Grid",
  "controlStyles[24].styles[0]": "RenderTransform@Pressed:=<ScaleTransform ScaleX=\"0.8\" ScaleY=\"0.8\" />",
  "controlStyles[24].styles[1]": "RenderTransformOrigin=0.5,0.5",
  "controlStyles[25].target": "Border#StartDropShadow",
  "controlStyles[25].styles[0]": "Visibility=Collapsed",
  "webContentStyles[0].target": "*",
  "webContentStyles[0].styles[0]": "transition: background-color 0.100s ease-in-out !important",
  "styleConstants[0]": "borderColor=<LinearGradientBrush x:Key=\"ShellTaskbarItemGradientStrokeColorSecondaryBrush\" MappingMode=\"Absolute\" StartPoint=\"0,0\" EndPoint=\"0,3\"><LinearGradientBrush.GradientStops><GradientStop Offset=\"0.33\" Color=\"#1AFFFFFF\" /><GradientStop Offset=\"1\" Color=\"#0FFFFFFF\" /></LinearGradientBrush.GradientStops></LinearGradientBrush>",
  "styleConstants[1]": "backgroundNormal=<SolidColorBrush Color=\"{ThemeResource ControlFillColorDefault}\" />",
  "styleConstants[2]": "backgroundHover=<SolidColorBrush Color=\"{ThemeResource ControlFillColorSecondary}\" />",
  "styleConstants[3]": "backgroundPressed=<SolidColorBrush Color=\"{ThemeResource ControlFillColorTertiary}\" />",
  "styleConstants[4]": "AnimationSettings=<TransitionCollection><EntranceThemeTransition IsStaggeringEnabled=\"True\" FromHorizontalOffset=\"0\" FromVerticalOffset=\"100\" /></TransitionCollection>",
  "styleConstants[5]": "glassyBorder=<LinearGradientBrush StartPoint=\"0,0\" EndPoint=\"0,1\"><GradientStop Color=\"#50808080\" Offset=\"0.0\" /><GradientStop Color=\"#50404040\" Offset=\"0.25\" /><GradientStop Color=\"#50808080\" Offset=\"1\" /></LinearGradientBrush>",
  "styleConstants[6]": "elementGlassyBorder=<LinearGradientBrush StartPoint=\"0,0\" EndPoint=\"0,1\"><GradientStop Color=\"#50808080\" Offset=\"0.0\" /><GradientStop Color=\"#50404040\" Offset=\"0.85\" /></LinearGradientBrush>"
}
```

</details>

## Windows 11 Taskbar Styler

[Mod](https://windhawk.net/mods/windows-11-taskbar-styler) · **v1.10** — Acrylic flyouts and menus, thin borders, reduced shadows, and a time-only clock.

<details>
<summary>Configuration</summary>

```json
{
  "theme": "",
  "styleConstants[0]": "mbg=<AcrylicBrush TintColor=\"{ThemeResource CardStrokeColorDefaultSolid}\" FallbackColor=\"{ThemeResource CardStrokeColorDefaultSolid}\" TintOpacity=\"0.5\" TintLuminosityOpacity=\"0.8\" Opacity=\"1\"/>",
  "styleConstants[1]": "t=Transparent",
  "styleConstants[2]": "bb=#20FFFFFF",
  "styleConstants[3]": "bt=1",
  "styleConstants[4]": "TaskbarFrameWidth=1340",
  "styleConstants[5]": "AnimationSettings=<TransitionCollection><EntranceThemeTransition IsStaggeringEnabled=\"True\" FromHorizontalOffset=\"0\" FromVerticalOffset=\"20\" /></TransitionCollection>",
  "controlStyles[0].target": "SystemTray.ChevronIconView",
  "controlStyles[0].styles[0]": "Margin=0,0,2,0",
  "controlStyles[1].target": "SystemTray.NotifyIconView > Windows.UI.Xaml.Controls.Grid#ContainerGrid > Windows.UI.Xaml.Controls.Border#BackgroundBorder",
  "controlStyles[1].styles[0]": "Margin=2,4,2,4",
  "controlStyles[2].target": "SystemTray.IconView#SystemTrayIcon > Windows.UI.Xaml.Controls.Grid#ContainerGrid > Windows.UI.Xaml.Controls.Border#BackgroundBorder",
  "controlStyles[2].styles[0]": "Margin=2,4,2,4",
  "controlStyles[3].target": "SystemTray.OmniButton#ControlCenterButton > Windows.UI.Xaml.Controls.Grid > Windows.UI.Xaml.Controls.Border#BackgroundBorder",
  "controlStyles[3].styles[0]": "Margin=2,4,2,4",
  "controlStyles[4].target": "SystemTray.OmniButton#NotificationCenterButton > Windows.UI.Xaml.Controls.Grid > Windows.UI.Xaml.Controls.Border#BackgroundBorder",
  "controlStyles[4].styles[0]": "Margin=2,4,2,4",
  "controlStyles[5].target": "Border#OverflowFlyoutBackgroundBorder",
  "controlStyles[5].styles[0]": "Background:=$mbg",
  "controlStyles[5].styles[1]": "BorderThickness=$bt",
  "controlStyles[5].styles[2]": "BorderBrush=$bb",
  "controlStyles[5].styles[3]": "Shadow:=",
  "controlStyles[6].target": "Windows.UI.Xaml.Controls.Grid#ConfirmatorMainGrid",
  "controlStyles[6].styles[0]": "Background:=$mbg",
  "controlStyles[6].styles[1]": "BorderThickness=$bt",
  "controlStyles[6].styles[2]": "BorderBrush=$bb",
  "controlStyles[6].styles[3]": "Shadow:=",
  "controlStyles[7].target": "Windows.UI.Xaml.Shapes.Rectangle#HorizontalTrackRect",
  "controlStyles[7].styles[0]": "Fill:=#10FFFFFF",
  "controlStyles[8].target": "Taskbar.TaskbarBackground#HoverFlyoutBackgroundControl > Grid > Rectangle#BackgroundFill",
  "controlStyles[8].styles[0]": "Fill:=$t",
  "controlStyles[9].target": "Windows.UI.Xaml.Controls.Grid#HoverFlyoutGrid > Windows.UI.Xaml.Controls.Border#HoverFlyoutBackground",
  "controlStyles[9].styles[0]": "Background:=$mbg",
  "controlStyles[9].styles[1]": "BorderThickness=$bt",
  "controlStyles[9].styles[2]": "BorderBrush=$bb",
  "controlStyles[9].styles[3]": "Shadow:=",
  "controlStyles[10].target": "Taskbar.TaskItemThumbnailView > Grid@CommonStates > Border#BackgroundBorder",
  "controlStyles[10].styles[0]": "Background=$t",
  "controlStyles[10].styles[1]": "BorderThickness@Normal=0",
  "controlStyles[10].styles[2]": "BorderBrush@Normal=$t",
  "controlStyles[10].styles[3]": "BorderThickness@PointerOver=0.05,0,0.05,2",
  "controlStyles[10].styles[4]": "BorderBrush@PointerOver:=<SolidColorBrush Color=\"{StaticResource SystemAccentColor}\" Opacity=\"0.8\" />",
  "controlStyles[11].target": "Windows.UI.Xaml.Controls.ContentPresenter#BorderElement",
  "controlStyles[11].styles[0]": "CornerRadius=5",
  "controlStyles[11].styles[1]": "Margin=-1,-1,-1,-1",
  "controlStyles[12].target": "Windows.UI.Xaml.Controls.Grid#ModalRootGrid > Windows.UI.Xaml.Controls.Border#BackgroundElement",
  "controlStyles[12].styles[0]": "Background:=$mbg",
  "controlStyles[12].styles[1]": "BorderThickness=$bt",
  "controlStyles[12].styles[2]": "BorderBrush=$bb",
  "controlStyles[12].styles[3]": "Shadow:=",
  "controlStyles[13].target": "Windows.UI.Xaml.Controls.Border#BackgroundDimmingLayer",
  "controlStyles[13].styles[0]": "Background:=<WindhawkBlur BlurAmount=\"0\" TintColor=\"#00000000\" />",
  "controlStyles[14].target": "WindowsInternal.ComposableShell.Experiences.Switcher.VirtualDesktopBarElement#VirtualDesktopBar > Grid > Border",
  "controlStyles[14].styles[0]": "Background:=$mbg",
  "controlStyles[14].styles[1]": "BorderThickness=$bt",
  "controlStyles[14].styles[2]": "BorderBrush=$bb",
  "controlStyles[15].target": "WindowsInternal.ComposableShell.Experiences.Switcher.VirtualDesktopBarElement#VirtualDesktopBar",
  "controlStyles[15].styles[0]": "MaxWidth:=900",
  "controlStyles[15].styles[1]": "Shadow:=",
  "controlStyles[16].target": "Windows.UI.Xaml.Controls.Grid#MainGrid",
  "controlStyles[16].styles[0]": "CornerRadius=$mcr",
  "controlStyles[16].styles[1]": "BorderThickness=$bt",
  "controlStyles[16].styles[2]": "BorderBrush=$bb",
  "controlStyles[17].target": "Windows.UI.Xaml.Controls.Button#VirtualDesktopElementCloseButton",
  "controlStyles[17].styles[0]": "CornerRadius=$bcr",
  "controlStyles[18].target": "Windows.UI.Xaml.Controls.Border#SnapBarBorder",
  "controlStyles[18].styles[0]": "Background:=$mbg",
  "controlStyles[18].styles[1]": "RenderTransform:=<TranslateTransform X=\"0\" Y=\"-20\" />",
  "controlStyles[18].styles[2]": "Margin=0,0,0,-10",
  "controlStyles[18].styles[3]": "Shadow:=",
  "controlStyles[19].target": "Windows.UI.Xaml.Controls.Border#SnapPickerBorder",
  "controlStyles[19].styles[0]": "Background:=$mbg",
  "controlStyles[19].styles[1]": "CornerRadius=$mcr",
  "controlStyles[19].styles[2]": "BorderThickness=$bt",
  "controlStyles[19].styles[3]": "BorderBrush=$bb",
  "controlStyles[20].target": "Windows.UI.Xaml.Controls.FlyoutPresenter > Border",
  "controlStyles[20].styles[0]": "Shadow:=",
  "controlStyles[21].target": "MenuFlyoutPresenter",
  "controlStyles[21].styles[0]": "CornerRadius=$mcr",
  "controlStyles[21].styles[1]": "Shadow:=",
  "controlStyles[22].target": "Windows.UI.Xaml.Controls.ToolTip > Windows.UI.Xaml.Controls.ContentPresenter#LayoutRoot",
  "controlStyles[22].styles[0]": "Background:=$mbg",
  "controlStyles[22].styles[1]": "CornerRadius=$mcr",
  "controlStyles[22].styles[2]": "BorderThickness=$bt",
  "controlStyles[22].styles[3]": "BorderBrush=$bb",
  "controlStyles[22].styles[4]": "Shadow:=",
  "controlStyles[23].target": "ScrollViewer#MenuFlyoutPresenterScrollViewer > Border > Grid > ScrollContentPresenter > ItemsPresenter > StackPanel",
  "controlStyles[23].styles[0]": "ChildrenTransitions:=$AnimationSettings",
  "controlStyles[24].target": "Grid#LayoutRoot",
  "controlStyles[24].styles[0]": "BackgroundTransition:=<BrushTransition Duration=\"0:0:0.100\" />",
  "controlStyles[25].target": "Border#BackgroundBorder",
  "controlStyles[25].styles[0]": "BackgroundTransition:=<BrushTransition Duration=\"0:0:0.100\" />",
  "controlStyles[26].target": "TextBlock#TimeInnerTextBlock",
  "controlStyles[26].styles[0]": "FontSize=13",
  "controlStyles[27].target": "TextBlock#DateInnerTextBlock",
  "controlStyles[27].styles[0]": "Visibility=Collapsed",
  "controlStyles[28].target": "TextBlock#LabelControl",
  "controlStyles[28].styles[0]": "Margin=0,0,-2,0",
  "themeResourceVariables[0]": "",
  "xamlDiagnosticsHandling": "",
  "controlStyles[29].target": "SystemTray.SystemTrayFrame",
  "controlStyles[29].styles[0]": "Height=40"
}
```

</details>

## Taskbar height and icon size

[Mod](https://windhawk.net/mods/taskbar-icon-size) · **v1.3.10** — 42 px taskbar height, 24 px icons, and 38 px buttons; small icons use 16 px and 32 px buttons.

<details>
<summary>Configuration</summary>

```json
{
  "TaskbarHeight": 42,
  "IconSize": 24,
  "TaskbarButtonWidth": 38,
  "IconSizeSmall": 16,
  "TaskbarButtonWidthSmall": 32
}
```

</details>

## Taskbar Labels for Windows 11

[Mod](https://windhawk.net/mods/taskbar-labels) · **v1.5** — Uncombined buttons with 12 px labels, ellipsis, and dynamic running indicators.

<details>
<summary>Configuration</summary>

```json
{
  "mode": "labelsWithoutCombining",
  "taskbarItemWidth": 0,
  "runningIndicatorStyle": "centerDynamic",
  "progressIndicatorStyle": "fullWidth",
  "excludedPrograms[0]": "excluded1.exe",
  "minimumTaskbarItemWidth": 50,
  "maximumTaskbarItemWidth": 176,
  "fontSize": 12,
  "fontFamily": "",
  "textTrimming": "characterEllipsis",
  "leftAndRightPaddingSize": 5,
  "spaceBetweenIconAndLabel": 8,
  "runningIndicatorHeight": 3,
  "runningIndicatorVerticalOffset": 1,
  "alwaysShowThumbnailLabels": 0,
  "labelForSingleItem": "%name%",
  "labelForMultipleItems": "[%amount%] %name%"
}
```

</details>

## Remove Taskbar Window Suffixes

[Mod](https://windhawk.net/mods/file-explorer-remove-suffixes) · **v1.1.1** — Removes app suffixes and leading number/em-dash prefixes from taskbar labels.

<details>
<summary>Configuration</summary>

```json
{
  "suffixRemovalMode": "universal",
  "suffixRules[0].processIdentifier": "",
  "suffixRules[0].search": "^\\d+\\s*— \\s*",
  "suffixRules[0].replace": ""
}
```

</details>

## Win32 UI Modernizer

[Mod](https://windhawk.net/mods/win32-ui-modernizer) · **v1.0.2** — Dark mode, rounded legacy controls, modern menus, Explorer accents, and Mica in About Windows.

<details>
<summary>Configuration</summary>

```json
{
  "TreeViewSection.Enabled": 1,
  "TreeViewSection.ModernInsertMark": 1,
  "TreeViewSection.InsertMarkColor": "accent",
  "TreeViewSection.RemoveTreeLines": 1,
  "TreeViewSection.AnimatedArrows": 1,
  "GeneralSection.Enabled": 1,
  "GeneralSection.CustomAccentColor": "",
  "GeneralSection.TransparencyCompat": 0,
  "GeneralSection.ModernTooltips": 1,
  "GeneralSection.ModernLightScrollbars": 0,
  "GeneralSection.DisableTextPipeline": 0,
  "GeneralSection.EnableDarkMode": 1,
  "GeneralSection.ModernContextMenus": 1,
  "GeneralSection.MenuCornerStyle": "round",
  "GeneralSection.MenuHoverRadius": 4,
  "GeneralSection.RoundedButtons": 1,
  "GeneralSection.CheckBoxAnim": 1,
  "GeneralSection.AccentRadioButtons": 1,
  "GeneralSection.EditFocusLine": 1,
  "GeneralSection.ModernGroupBox": 1,
  "GeneralSection.ModernSeparators": 1,
  "GeneralSection.ModernFocusRect": "modern",
  "GeneralSection.ProgressBars": 1,
  "GeneralSection.RoundedTabPane": 1,
  "GeneralSection.NormalizeDragDrop": 1,
  "ExplorerSection.Enabled": 1,
  "ExplorerSection.AccentColorize": 1,
  "ExplorerSection.AccentMarquee": 1,
  "ExplorerSection.RoundedSelection": 1,
  "ExplorerSection.NavPaneHoverFade": 1,
  "ExplorerSection.NeutralSelection": 1,
  "ExplorerSection.RemoveNavDivider": 0,
  "ExplorerSection.RemoveNavDividerTW": 0,
  "ExplorerSection.NavDividerHoverReveal": 1,
  "ExplorerSection.NavPaneWinUIMetrics": 1,
  "ExplorerSection.LegacyRebarControls": 1,
  "ExplorerSection.RebarMicaTint": 1,
  "ExplorerSection.NavPanePill": 1,
  "ExplorerSection.NavPillStyle": "winui_top",
  "ExplorerSection.NavPillGradient": 0,
  "ExplorerSection.AccentButtonGradient": 0,
  "ExplorerSection.EditFocusGradient": 0,
  "ExplorerSection.NavPillNoClip": 1,
  "ExplorerSection.ListViewPill": 0,
  "ExplorerSection.RoundedGroupHeaders": 0,
  "ExplorerSection.FluentPinIcon": 1,
  "ExplorerSection.PinIconStyle": "outline",
  "ExplorerSection.PinIconColor": "accent",
  "ExplorerSection.PinMarginRight": 0,
  "ExplorerSection.GlyphIcons": "static",
  "ExplorerSection.ModernizeShellIcons": 1,
  "ExplorerSection.GlyphColor": "",
  "ExplorerSection.DiskChartAccentColor": 1,
  "ExplorerSection.AutoPlayReplacement": 1,
  "RegeditSection.Enabled": 1,
  "RegeditSection.TransparentBg": 0,
  "RegeditSection.GlyphIcons": 1,
  "WinverSection.Enabled": 1,
  "WinverSection.Background": "mica",
  "ComboBoxDWMSection.Enabled": 1,
  "ComboBoxDWMSection.CornerStyle": "small",
  "DarkModeExcludeList[0].target": ""
}
```

</details>

## Invisible Window Borders

[Mod](https://windhawk.net/mods/invisible-borders) · **v1.0.0** — Invisible borders with rounded corners, including dialogs.

<details>
<summary>Configuration</summary>

```json
{
  "SpecialWindows": 1
}
```

</details>

## Custom Desktop Watermark

[Mod](https://windhawk.net/mods/custom-desktop-watermark) · **v1.2.0** — Empty watermark text.

<details>
<summary>Configuration</summary>

```json
{
  "lines[0].text": "",
  "lines[0].title": 0,
  "lines[0].bold": 0,
  "lines[0].align": "right",
  "classic": 0
}
```

</details>
