# 💻 02 — Installing R and RStudio

> **Author:** RP &nbsp;|&nbsp; [@priyasaivasan](https://github.com/priyasaivasan)

---

## 🧠 Before You Start — Understand the Two Pieces

You need to install **two separate things**:

| Software | What it is | Download from |
|----------|-----------|---------------|
| **R** | The engine — the actual language that runs your code | [cran.r-project.org](https://cran.r-project.org) |
| **RStudio** | The cockpit — a friendly interface to write and run R code | [posit.co/download/rstudio-desktop](https://posit.co/download/rstudio-desktop) |

> 💡 **Analogy:** R is the car engine. RStudio is the dashboard and steering wheel. You need both — but you always install R *first*.

---

## 🪟 Installing on Windows

### Step 1 — Install R
1. Go to [cran.r-project.org](https://cran.r-project.org)
2. Click **"Download R for Windows"**
3. Click **"base"**
4. Click **"Download R-4.x.x for Windows"**
5. Run the `.exe` file → click **Next** through all prompts → **Finish**

### Step 2 — Install RStudio
1. Go to [posit.co/download/rstudio-desktop](https://posit.co/download/rstudio-desktop)
2. Click **"Download RStudio Desktop"** (free version)
3. Run the `.exe` → follow the installer → **Finish**
4. Open RStudio — you're ready!

---

## 🍎 Installing on Mac

### Step 1 — Install R
1. Go to [cran.r-project.org](https://cran.r-project.org)
2. Click **"Download R for macOS"**
3. Choose the right version:
   - **Apple Silicon (M1/M2/M3 chip)** → download the `arm64` `.pkg`
   - **Intel Mac** → download the `x86_64` `.pkg`
4. Open the `.pkg` → follow installer steps

> 💡 Not sure which Mac you have? Click  → **About This Mac** → look for "Apple M1/M2/M3" (Silicon) or "Intel Core" (Intel)

### Step 2 — Install RStudio
1. Go to [posit.co/download/rstudio-desktop](https://posit.co/download/rstudio-desktop)
2. Download the **macOS** `.dmg` file
3. Drag RStudio to your **Applications** folder
4. Open RStudio from Applications

---

## ✅ Checking Your Installation

Open RStudio and type this in the Console:

```r
R.version.string
```

You should see something like:
```
[1] "R version 4.3.2 (2023-10-31)"
```

If you see that — you're all set! 🎉

---

## ⬅️ [Back: Overview](01_overview.md) &nbsp;|&nbsp; [➡️ Next: R Environment](03_environment.md)
