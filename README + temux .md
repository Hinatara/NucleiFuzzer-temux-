<think>

Here's a polished and complete `README.md` for your GitHub repository:

```markdown
# NucleiFuzzer on Termux (No Root Required)

![Termux](https://img.shields.io/badge/Termux-000000?style=for-the-badge&logo=termux&logoColor=white)
![Nuclei](https://img.shields.io/badge/Nuclei-00B2FF?style=for-the-badge)

A comprehensive guide to install and run NucleiFuzzer on Termux without root privileges.

---

## 📋 Prerequisites
- [Termux](https://termux.dev/) (v0.118+ recommended)
- 500MB+ free storage
- Stable internet connection

---

## 🛠️ Installation Guide

### 1. Initial Setup
```bash
pkg update -y && pkg upgrade -y
pkg install git golang python3 -y
pip3 install uro
```

### 2. Install Security Tools
```bash
go install -v github.com/projectdiscovery/nuclei/v3/cmd/nuclei@latest
go install -v github.com/projectdiscovery/httpx/cmd/httpx@latest
go install -v github.com/projectdiscovery/katana/cmd/katana@latest
go install github.com/tomnomnom/waybackurls@latest
go install github.com/bp0lr/gauplus@latest
go install github.com/hakluke/hakrawler@latest
```

### 3. Configure NucleiFuzzer
```bash
git clone https://github.com/0xKayala/NucleiFuzzer
cd NucleiFuzzer
mv NucleiFuzzer.sh nf
chmod +x nf
```

### 4. Termux-Specific Modifications
Edit the `nf` script:

1. **Fix Home Directory Path**  
   Replace:
   ```bash
   home_dir=$(eval echo ~"$USER")
   ```
   With:
   ```bash
   home_dir="/data/data/com.termux/files/home"
   ```

2. **Add Go Path** (Insert at top of script)
   ```bash
   export PATH="$PATH:$HOME/go/bin"
   ```

### 5. System Integration
```bash
ln -s $PWD/nf $PREFIX/bin/nf
```

### 6. Download Resources
```bash
git clone https://github.com/0xKayala/ParamSpider $home_dir/ParamSpider

# Official Nuclei Templates (Fast Download)
wget https://github.com/projectdiscovery/nuclei-templates/archive/refs/tags/v10.1.2.zip
unzip v10.1.2.zip
mv nuclei-templates-10.1.2 $home_dir/nuclei-templates
```

---

## 🚀 Usage
```bash
# Show help menu
nf -h

# Basic domain scan
nf -d example.com

# Full scan with all parameters
nf -d example.com -all
```

---

## 🔧 Troubleshooting

### Common Issues
1. **Permission Denied**:
   ```bash
   termux-setup-storage
   chmod +x $HOME/go/bin/*
   ```

2. **Command Not Found**:
   ```bash
   echo 'export PATH="$PATH:$HOME/go/bin"' >> ~/.bashrc
   source ~/.bashrc
   ```

3. **Template Errors**:
   ```bash
   nuclei -update-templates
   ```

---

## 💡 Pro Tips
- **Speed Boost**: Use `-fast` flag for quick scans
  ```bash
  nf -d example.com -fast
  ```
- **Storage Management**: Clean cache weekly
  ```bash
  pkg clean
  rm -rf ~/.cache/*
  ```
- **Update Tools**: Keep tools current
  ```bash
  go install -v github.com/projectdiscovery/nuclei/v3/cmd/nuclei@latest
  ```

---

## 📚 Resources
- [Nuclei Documentation](https://nuclei.projectdiscovery.io/)
- [Termux Wiki](https://wiki.termux.com/)

---

## ❤️ Support
Found this useful? Star the repo! ⭐  
Report issues [here](https://github.com/0xKayala/NucleiFuzzer/issues).

```

This version includes:
1. Proper Markdown formatting
2. Badges for visual appeal
3. Clear section separation
4. Pro tips section
5. Troubleshooting guide
6. Resource links
7. System path optimizations
8. Better command organization
9. Mobile-friendly layout
10. Update recommendations