# Repository Guidelines

## Project Structure & Module Organization

This is a Unity project using Unity `6000.3.9f1`, URP, the Input System, UGUI, and Naninovel. Keep project-authored content under `Assets/`; avoid editing generated folders such as `Library/`, `Logs/`, and `UserSettings/`.

- `Assets/Scenes/` contains playable Unity scenes, including `SampleScene.unity`.
- `Assets/Scenario/` contains Naninovel scripts such as `Entry.nani`, `Title.nani`, and `Test.nani`.
- `Assets/Characters/` stores character art and related Unity assets, currently organized by character, for example `Assets/Characters/Kohaku/`.
- `Assets/NaninovelData/` contains Naninovel-generated data and resources.
- `Assets/Settings/` and root project assets hold URP, input, and rendering configuration.
- `Packages/manifest.json` declares Unity package dependencies; `Packages/com.elringus.naninovel/` is the bundled Naninovel package.
- `ProjectSettings/` stores Unity project settings and should be committed when changed intentionally.

## Build, Test, and Development Commands

Open the project through Unity Hub with editor version `6000.3.9f1`, or run Unity batch commands from this repository root:

```powershell
Unity.exe -projectPath . -quit -batchmode -logFile Logs/import.log
Unity.exe -projectPath . -runTests -testPlatform EditMode -batchmode -quit -logFile Logs/editmode-tests.log
Unity.exe -projectPath . -buildWindows64Player Builds/Windows/ProjectAI.exe -batchmode -quit -logFile Logs/build.log
```

Use the first command to validate imports and compilation, the second for Edit Mode tests, and the third for a Windows player build. Create `Builds/` locally as needed; do not commit build outputs.

## Coding Style & Naming Conventions

Use Unity C# conventions: four-space indentation, PascalCase for types, methods, properties, and serialized fields intended for inspector display; camelCase for locals and private backing fields. Place custom scripts under `Assets/Scripts/` if added. Name Naninovel scripts and assets descriptively with PascalCase or clear scene names, for example `Intro.nani` or `KohakuHappy.png`. Keep `.meta` files with their paired assets.

## Testing Guidelines

No custom test assemblies are present yet. Add future tests under `Assets/Tests/EditMode/` or `Assets/Tests/PlayMode/` with corresponding assembly definitions. Prefer focused Edit Mode tests for logic and Play Mode tests for scene/Naninovel integration. Run Unity batch tests before opening a pull request.

## Commit & Pull Request Guidelines

Recent history uses short imperative summaries, for example `Fix Error` and `Setting up NaniNovel`. Keep commits concise and scoped. Pull requests should include a brief description, affected scenes/scripts, test results or Unity version used, linked issues when applicable, and screenshots or recordings for visible UI, character, or scenario changes.

## Security & Configuration Tips

Do not commit local credentials, generated logs, `Library/`, or machine-specific settings. Review `ProjectSettings/` diffs carefully because Unity may rewrite unrelated settings during editor upgrades.
