# 🧠 Ollama Model Installer  
A beginner‑friendly PowerShell tool for installing custom GGUF models into Ollama on Windows.

This script was built to solve a simple problem:  
**Installing custom GGUF models into Ollama is confusing for new users.**

This installer removes all the guesswork by guiding the user step‑by‑step through the entire process — no file moving, no path confusion, no manual Modelfile creation, and no PowerShell experience required.

---

## ⚠️ If PowerShell says “running scripts is disabled” — here’s how to fix it

When running this installer for the first time, Windows may block it with an error like:

```
.\ollama-model-installer.ps1 : File cannot be loaded because running scripts is disabled on this system.
```

This happens because Windows defaults to a **locked‑down PowerShell mode** that prevents *all* scripts from running — even safe ones you wrote yourself.

### ✅ How to fix it (safe and recommended)

Run this command **once** in PowerShell:

```
Set-ExecutionPolicy -Scope CurrentUser RemoteSigned
```

Then press **Y** to confirm.

### 🧠 What this command actually does

- It **only** changes the execution policy for *your user account*  
- It does **not** affect the whole system  
- It allows you to run **your own scripts**  
- It still blocks scripts downloaded from the internet unless they are signed  
- It does **not** reduce system security in any meaningful way  

This is the standard, safe way to enable PowerShell scripts on Windows.

### 🎉 After running the command

You can now run the installer normally:

```
.\ollama-model-installer.ps1
```

If you ever want to revert the change, you can run:

```
Set-ExecutionPolicy -Scope CurrentUser Restricted
```

But most users leave it enabled without issues.

---

## ✨ Features

### ✔ Script can run from ANY folder  
You can keep the script in **Documents**, **Desktop**, or anywhere else.  
It automatically handles all model‑folder creation and file placement.

### ✔ Automatic model folder creation  
Just type the name you want (e.g., `pentest_ai`) and the script creates:

```
C:\Users\<YourName>\.ollama\models\<your_model_name>
```

### ✔ GGUF auto‑detection  
Once you place your `.gguf` file into the new folder, the script finds it automatically — even long filenames.

### ✔ Automatic Modelfile generation  
The script creates a valid Modelfile inside the model folder:

```
FROM ./yourfile.gguf
TEMPLATE """{{ .Prompt }}"""
```

### ✔ Registers the model with Ollama  
Runs:

```
ollama create <model_name> -f Modelfile
```

### ✔ Optional: run the model immediately  
After installation, the script can launch the model for you.

### ✔ Clean, color‑coded interface  
- **Magenta** → Step titles  
- **Green** → Instructions  
- **Yellow** → User prompts  
- **Cyan** → Success messages  
- **Red** → Errors  
- Clears the console between steps for a clean guided experience.

### ✔ 100% ASCII‑safe  
No smart quotes, no Unicode characters — fully PowerShell‑compatible.

---

## 🚀 How to Use

1. Download `ollama-model-installer.ps1`
2. Open PowerShell
3. Run:

```
Set-ExecutionPolicy -Scope CurrentUser RemoteSigned
```

(Only needed once.)

4. Navigate to the folder where the script is:

```
cd "C:\Users\<YourName>\Documents"
```

5. Run the installer:

```
.\ollama-model-installer.ps1
```

6. Follow the on‑screen steps:
   - Choose a model folder name  
   - Place your GGUF file inside the folder  
   - Name your model  
   - Let the script build and register it  

---

## 🎯 Why This Exists

Ollama is powerful — but installing custom models manually can be intimidating for beginners:

- Hidden folders  
- Modelfile syntax  
- Path confusion  
- GGUF naming issues  
- PowerShell quirks  

This installer solves all of that with a **guided, fool‑proof workflow** that anyone can follow.

---

## 🛠 Requirements

- Windows 10 or 11  
- PowerShell  
- Ollama installed  
- A `.gguf` model file  

---

## 📄 License

MIT License — free to use, modify, and share.

---

## ❤️ Contributions

Pull requests are welcome!  
If you have ideas for improvements — auto‑download from HuggingFace, GUI version, uninstall mode, etc. — feel free to open an issue.
