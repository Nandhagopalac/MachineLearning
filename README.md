# Machine_Learning — Project Setup & Quick Start ✅

This document describes how to create the repository, set up a virtual environment, use Poetry with an existing venv, and configure VS Code workspace settings to disable automatic inline autocompletions while keeping import suggestions available when triggered.

---

## 1) Create a new repo on GitHub
1. Go to github.com and create a new repository named `Machine_Learning`.
2. Add a short description and choose **Public** or **Private** as you prefer.

## 2) Clone the repo in VS Code
- In VS Code: Ctrl+Shift+P → **Git: Clone** → paste the repo URL → choose folder and open the cloned folder.

Or from a terminal:
```bash
git clone https://github.com/<your-username>/Machine_Learning.git
cd Machine_Learning
```

## 3) Create a new virtual environment
Run (from project root):
```bash
python -m venv venvml
```
Activate (Windows PowerShell):
```powershell
.\venvml\Scripts\Activate.ps1
```
Or (Windows cmd):
```cmd
venvml\Scripts\activate.bat
```
Or (macOS / Linux):
```bash
source venvml/bin/activate
```

## 4) Install Poetry using pip
With the venv activated, run:
```bash
pip install poetry
```
If you want to inspect the installed package (what was installed):
```bash
pip show poetry
```

## 5) Check `poetry` and `python` paths (run inside project folder)
- On macOS/Linux (or Git Bash):
```bash
which poetry
which python
```
- On Windows PowerShell / cmd use `where`:
```powershell
where poetry
where python
```
These should show locations inside your environment/project context (so you know you're using the project venv's executables).

## 6) Configure Poetry to reuse your existing venv
Tell Poetry not to create its own virtualenvs (we'll use the `venvml` you created):
```bash
poetry config virtualenvs.create false --local
```
(`--local` stores it in `poetry.toml` in the project so it's specific to this repo)

## 7) Initialize Poetry for the project
```bash
poetry init --no-interaction
```
(Use `--no-interaction` to accept defaults; omit it if you want to pick options interactively.)

## 8) Add needed packages
```bash
poetry add ipykernel pandas numpy scikit-learn
```
(Add more packages as needed.)

## 9) VS Code workspace settings: disable auto-population but keep manual/import suggestions
Open VS Code → Ctrl+Shift+P → **Preferences: Open Workspace Settings (JSON)** and paste the following:

```json
{
  "editor.quickSuggestions": false,
  "editor.suggestOnTriggerCharacters": false,
  "editor.inlineSuggest.enabled": false,
  "editor.tabCompletion": "off",
  "editor.acceptSuggestionOnEnter": "off",
  "editor.acceptSuggestionOnCommitCharacter": false
}
```

> Tip: If you want import suggestions to appear when you type language characters (like `from sklearn import`), change `"editor.suggestOnTriggerCharacters"` to `true` in the workspace settings instead of `false`.

---

## Quick test
1. Activate `venvml`. 2. In the project root run `python -c "import pandas; print(pandas.__version__)"` — it should succeed. 3. Open a Python file and type: `from sklearn import` — suggestions should appear (or use Ctrl+Space).

## Optional: Commit and push README
```bash
git add README.md
git commit -m "Add project setup instructions"
git push origin main
```

---

If you'd like, I can also:
- add this README.md to the repo and push it for you, or
- make a shorter checklist version as `README-short.md`, or
- include a small `setup.sh` / `setup.ps1` script to automate these steps.

Let me know which of those you'd like me to do next. 🔧