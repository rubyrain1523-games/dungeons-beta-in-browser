# Minecraft Dungeons Narration Build in a Browser

This project experiments with running the February 2017 Windows build in a
browser using [Boxedwine](https://github.com/danoon2/Boxedwine) and GitHub
Pages. Boxedwine emulates the 32-bit Windows executable; this is not a native
port of the game.

## Requirements

- Permission to redistribute the build and its assets publicly.
- The narration build at
  `dungeons-legends/narration-build-2017/Narration_NoGeneratedLevel_20170216/`.
  The folder must contain `Minecraft.Win32.OGL.exe`, `fmod.dll`, and the
  accompanying `data` and `games` folders.
- GitHub Pages enabled for the repository with **Build and deployment** set to
  **GitHub Actions**.

The workflow packages that build, downloads the pinned Boxedwine web
filesystem, builds Boxedwine's single-threaded WebAssembly JIT runtime, and
deploys the result. It excludes only the `.pdb` and `.ilk` debug files from the
game package. The resulting Pages site is a public redistribution of the game
files; do not publish it unless you have the required rights.

## Deploy

Commit the required narration-build folder and this project to the `main`
branch, then push. The workflow at
`.github/workflows/pages.yml` also supports a manual run from the Actions tab.
Once deployment succeeds, open the Pages URL. The first launch downloads the
runtime files and initializes Wine in browser storage, so it may take a while.

## Compatibility

This is an experimental compatibility attempt, not a confirmed working port.
The executable is a 32-bit Windows OpenGL game, which fits Boxedwine's target,
but Boxedwine documents limited success with games released after 2010. The
2017 build may fail to start or render correctly even if the runtime builds and
deploys. The browser build is single-threaded and may run very slowly.

Boxedwine is GPL-2.0. The deployment workflow builds the runtime from the
pinned upstream revision
[`ef9b162`](https://github.com/danoon2/Boxedwine/tree/ef9b162114007d25ded8eed1784dac043ba65016);
its source and license are available there.
