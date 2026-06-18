# 🖥️ 03 — R Environment and Workspace

> **Author:** RP &nbsp;|&nbsp; [@priyasaivasan](https://github.com/priyasaivasan)

---

## 🗺️ The RStudio Layout — 4 Panes

When you open RStudio you'll see four panels. Each has a specific job:

```
┌─────────────────────┬──────────────────────┐
│   SOURCE (top-left) │  ENVIRONMENT (top-right) │
│   Write your scripts│  See your variables   │
├─────────────────────┼──────────────────────┤
│  CONSOLE (bot-left) │  FILES/PLOTS (bot-right) │
│  Run code & see     │  Browse files, view   │
│  output here        │  plots, get help      │
└─────────────────────┴──────────────────────┘
```

| Pane | Purpose |
|------|---------|
| **Source** (top-left) | Write and save `.R` scripts here |
| **Console** (bottom-left) | Where code runs and output appears |
| **Environment/History** (top-right) | See all variables currently in memory |
| **Files/Plots/Help** (bottom-right) | File browser, your graphs, package help |

---

## ⌨️ Essential Keyboard Shortcuts

| Action | Windows | Mac |
|--------|---------|-----|
| Run current line | `Ctrl + Enter` | `Cmd + Enter` |
| Run entire script | `Ctrl + Shift + Enter` | `Cmd + Shift + Enter` |
| Insert `<-` | `Alt + -` | `Option + -` |
| New script | `Ctrl + Shift + N` | `Cmd + Shift + N` |
| Save | `Ctrl + S` | `Cmd + S` |
| Comment line | `Ctrl + Shift + C` | `Cmd + Shift + C` |
| Clear console | `Ctrl + L` | `Cmd + L` |
| Autocomplete | `Tab` | `Tab` |
| Restart R | `Ctrl + Shift + F10` | `Cmd + Shift + F10` |

---

## 🗂️ The Workspace

The **workspace** is R's memory — it holds every variable and object you've created during your session.

```r
# See everything in your workspace
ls()

# Remove one variable
rm(x)

# Clear the entire workspace
rm(list = ls())

# Save your workspace to a file
save.image("mysession.RData")

# Load it back later
load("mysession.RData")
```

> ⚠️ **Good habit:** Don't rely on saving your workspace. Instead, save your *script* — that way you can always recreate your results from scratch, which is the foundation of reproducible analysis.

---

## 📁 Working Directory

R needs to know which folder to look in for files. This is called the **working directory**.

```r
# See your current working directory
getwd()

# Change it
setwd("/Users/priya/Documents/my-r-project")

# List files in working directory
list.files()
```

> 💡 **Tip:** In RStudio, go to **Session → Set Working Directory → To Source File Location** to automatically set it to wherever your script is saved.

---

## ⬅️ [Back: Installation](02_installation.md) &nbsp;|&nbsp; [➡️ Next: Syntax & Data Types](04_syntax_datatypes.md)
