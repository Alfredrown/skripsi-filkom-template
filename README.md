# Template Skripsi FILKOM UB

Template LaTeX skripsi Fakultas Ilmu Komputer, Universitas Brawijaya.  
Menggunakan referencing style **Harvard Anglia** dengan XeLaTeX.

## Prasyarat

- **MacTeX** (macOS) atau **TeX Live** (Linux/Windows WSL)
- **VS Code** + ekstensi [LaTeX Workshop](https://marketplace.visualstudio.com/items?itemName=James-Yu.latex-workshop)
- Font **Calibri** dan **Courier New** terinstall di sistem

## notice

read accordingly that the template was made with AI THERE might be some error but i expect you guys to know this and fix it by yourself, thanks.
### Install MacTeX (macOS)

```bash
brew install --cask mactex
```

### Install font Calibri

Calibri adalah font bawaan Microsoft Office. Jika belum ada, unduh dan install ke `~/Library/Fonts/`.

## Struktur File

```
.
├── skripsi.tex          ← File utama, isi data diri di sini
├── skripsi.cls          ← Class dokumen (jangan diubah)
├── hangilastyle.tex     ← Konfigurasi Harvard Anglia (jangan diubah)
├── daftar-pustaka.bib   ← Referensi BibTeX
├── bab1.tex             ← BAB 1: Pendahuluan
├── bab2.tex             ← BAB 2: Landasan Teori
├── bab3.tex             ← BAB 3: Metodologi
└── img/
    └── logo-ub.jpg      ← Logo UB (ganti dengan yang resmi)
```

## Cara Penggunaan

### 1. Isi data diri di `skripsi.tex`

```latex
\titleskripsi{Judul Skripsi Anda}
\fullname{Nama Lengkap}
\idnum{NIM}
\yearsubmit{2025}
\firstsupervisor{Nama Dosen Pembimbing I, S.T., M.T., Ph.D}
...
```

### 2. Sesuaikan path font

Ganti `GANTI-DENGAN-USERNAME` dengan username Mac Anda:

```latex
\setmainfont[Path=/Users/GANTI-DENGAN-USERNAME/Library/Fonts/,
    ...]{Calibri.ttf}
```

Atau cari lokasi font dengan:
```bash
find ~/Library/Fonts /Library/Fonts -name "Calibri.ttf"
```

### 3. Tulis konten bab

Edit `bab1.tex`, `bab2.tex`, `bab3.tex`, dst.  
Tambahkan bab baru dengan uncomment `\include{bab4}` di `skripsi.tex`.

### 4. Tambahkan referensi

Edit `daftar-pustaka.bib`:

```bibtex
@article{key,
  author  = {Last, First},
  title   = {Judul},
  journal = {Nama Jurnal},
  year    = {2024},
}
```

Sitasi dalam teks:
```latex
\parencite{key}      % → (Last, 2024)
\textcite{key}       % → Last (2024)
\parencite{a,b,c}    % → (A, 2024; B, 2023; C, 2022)
```

### 5. Build PDF

```bash
latexmk -xelatex skripsi.tex
```

Atau tekan **Ctrl+Alt+B** di VS Code dengan LaTeX Workshop.

## Konfigurasi VS Code (settings.json)

```json
{
  "latex-workshop.latex.tools": [{
    "name": "latexmk",
    "command": "/Library/TeX/texbin/latexmk",
    "args": ["-synctex=1", "-interaction=nonstopmode",
             "-file-line-error", "-xelatex",
             "-outdir=%OUTDIR%", "%DOC%"]
  }],
  "latex-workshop.latex.recipes": [{
    "name": "latexmk",
    "tools": ["latexmk"]
  }],
  "latex-workshop.latex.autoBuild.run": "onFileChange"
}
```

## Lisensi

Lihat file [LICENSE](LICENSE).


