# LaTeX setup for VSCode with pixi

1. Install
[VS Code](https://code.visualstudio.com)
and
[pixi](https://pixi.sh/).

2. Download (or clone) and open this repository with VS Code.
It will suggest to install the **LaTeX Workshop extension** from James Wu.
Install it.

3. Open `article.tex` from the file explorer (left side panel).
The PDF is (re)compiled each time `article.tex` is saved.

4. Click on the `Open Preview` icon (top right)
or open the LaTeX workshop extension ($\TeX$ icon, left side panel)
and click on `View LaTeX PDF`.
A tab with the compiled PDF should open.

## How does it work?

The `.vscode/extensions.json` file is there to trigger a recomendation
to install the LaTeX Workshop extension.
It can be removed.

The `.vscode/settings.json` file defines a recipe to compile a LaTeX project.
It uses [tectonic](https://tectonic-typesetting.github.io),
a modernized, complete, self-contained TeX/LaTeX engine.
To run `tectonic`,
it uses `pixi run tectonic`.

The file `pixi.toml` defines a dependency on the package
[tectonic](https://tectonic-typesetting.github.io),
which will be installed on the `.pixi` directory.
If it hasn't been installed yet,
it is done automatically by calling `pixi run tectonic`.

After the first run,
the `.pixi` directory will be created,
which contains a `conda` environment with the `tectonic` binary.
Also, a `pixi.lock` file will be created,
which contains a description of everything installed in the environment.

## Caveats

For each new LaTeX package added to `article.tex`,
`tectonic` requires internet access
since it downloads required LaTeX packages on demand.
They are cached for subsequent runs.
