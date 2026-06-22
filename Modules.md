---
notion-id: 2ae98e9c-907e-8076-ba49-eb91d649e596
---
Here’s a curated list of recommended PowerShell and WSL (Ubuntu) modules/packages to enhance your quality of life (QoL) and support AI, ML, and deep learning workflows:

---
### **PowerShell Modules**
### **AI/ML/Deep Learning Use Cases**
1. **AzureML (Azure Machine Learning)**
Useful if you work with Azure services for AI/ML experiments and pipelines.
    - Module: `AzureML`
    - Install: `Install-Module -Name AzureML -Scope CurrentUser`
2. **AWS.Tools.MachineLearning**
AWS PowerShell tools for managing AI/ML workloads on AWS frameworks like SageMaker.
    - Install: `Install-Module -Name AWS.Tools.MachineLearning -Scope CurrentUser`
3. **PSOpenAI**
Integrates OpenAI (e.g., GPT) with PowerShell for language model operations.
    - Install: `Install-Module -Name PSOpenAI -Scope CurrentUser`
4. **Invoke-RestMethod / Invoke-WebRequest (Built-In)**
Combine these cmdlets with APIs like OpenAI, Hugging Face, or other ML services.

### **General QoL Enhancements**
5. **Terminal-Icons**
Adds pretty icons to files and directories to improve the visual experience in PowerShell.
    - Install: `Install-Module -Name Terminal-Icons -Scope CurrentUser`
6. **PSReadLine**
Adds better command-line editing, syntax highlighting, and autocompletion (great for productivity).
    - Install: `Install-Module -Name PSReadLine -Force`
7. **Oh-My-Posh**
Enhances the appearance of your terminal with custom themes.
    - Install: `Install-Module -Name oh-my-posh -Scope CurrentUser`
8. **posh-git**
Enhances Git in your terminal with status tracking and autocompletions.
    - Install: `Install-Module -Name posh-git -Scope CurrentUser`
9. **PowerShellGet**
For managing modules and packages seamlessly.
    - Install: `Install-Module -Name PowerShellGet -Force -AllowClobber`
10. **Az**
Full Azure management functionality.
    - Install: `Install-Module -Name Az -Scope CurrentUser`

---
### **WSL (Ubuntu)**
### **AI/ML/Deep Learning Frameworks**
11. **Python and Pip**
    - Install: `sudo apt install python3 python3-pip`
12. **PyTorch**
    - Install:
```bash
pip install torch torchvision torchaudio

```
13. **TensorFlow**
    - Install:
```bash
pip install tensorflow

```
14. **scikit-learn**
    - Install:
```bash
pip install scikit-learn

```
15. **Hugging Face Transformers & Datasets**
Hugging Face libraries for large language models and NLP tasks.
    - Install:
```bash
pip install transformers datasets

```
16. **OpenCV**
    - Install:
```bash
pip install opencv-python opencv-python-headless

```
17. **Jupyter Notebook**
    - Install:
```bash
pip install notebook

```
Run with: `jupyter-notebook`
18. **CUDA (For NVIDIA GPUs)**
Install NVIDIA GPU drivers and CUDA for efficient GPU-accelerated training.
    - Install:
```bash
sudo apt update
sudo apt install nvidia-cuda-toolkit

```
19. **Docker**
Run containerized solutions for easy AI/ML setup.
    - Install:
```bash
sudo apt install docker.io
sudo usermod -aG docker $USER

```

### **General QoL Enhancements**
20. **Starship Prompt**
Similar to Oh-My-Posh, adds a fast and minimal prompt.
    - Install:
```bash
curl -fsSL <https://starship.rs/install.sh> | bash

```
21. **tmux**
Terminal multiplexer for managing multiple sessions.
    - Install:
```bash
sudo apt install tmux

```
22. **zsh and Oh My Zsh**
Zsh shell with autocompletions, themes, and plugins.
    - Install:
```bash
sudo apt install zsh
sh -c "$(curl -fsSL <https://raw.github.com/ohmyzsh/ohmyzsh/master/tools/install.sh>)"

```
23. **neofetch**
Displays your system information in a clean way.
    - Install:
```bash
sudo apt install neofetch

```
Run with: `neofetch`
24. **fzf**
Command-line fuzzy finder for fast navigation and searching.
    - Install:
```bash
sudo apt install fzf

```
25. **ripgrep**
Super-fast file searching.
    - Install:
```bash
sudo apt install ripgrep

```
26. **htop**
Interactive system resource viewer and process manager.
    - Install:
```bash
sudo apt install htop

```
27. **exa** *(Alternative to *`*ls*`*)*
    - Install:
```bash
sudo apt install exa

```

---
### Additional Tips:
- **Vim/NeoVim**
Great text/code editor options.
    - Install: `sudo apt install vim` or `sudo apt install neovim`
- Ensure WSL has access to GPU (if applicable) for AI/ML frameworks:
    - Follow NVIDIA’s [WSL support guide](https://developer.nvidia.com/cuda/wsl).

---
Would you like a step-by-step guide for setting up any specific module or package on PowerShell or WSL?