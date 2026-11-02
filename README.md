# 🎓 SnapClass – Intelligent AI Attendance System

> Making attendance faster, smarter, and proxy-proof using **multimodal face and voice recognition**.

SnapClass is a web-based attendance system built with **Streamlit**. Teachers create classes and take attendance, students enroll using a join link or QR code, and the AI verifies identity using **face** and **voice** recognition.

---

## ✨ Features

- **Face recognition** – identify students from photos using `dlib` / `face_recognition` models
- **Voice recognition** – verify speakers using voice embeddings (`resemblyzer` + `librosa`)
- **Role-based access** – separate Teacher and Student portals
- **QR code / join-link enrollment** – students join a class via `?join-code=<code>` with auto-enroll
- **Secure authentication** – passwords hashed with `bcrypt`
- **Cloud database** – data stored and managed using Supabase
- **Simple web UI** – built entirely in Streamlit, no separate frontend needed

---

## 🛠️ Tech Stack

| Area | Technology |
|------|-----------|
| Frontend / App | [Streamlit](https://streamlit.io/) |
| Face recognition | `dlib-bin`, `face_recognition_models`, `scikit-learn` |
| Voice recognition | `resemblyzer`, `librosa` |
| Database | [Supabase](https://supabase.com/) |
| Auth | `bcrypt` |
| QR codes | `segno` |
| Image handling | `Pillow` |
| Data utilities | `numpy`, `pandas` |

---

## 📁 Project Structure

```
intelligent-ai-attendance/
├── app.py               # Streamlit entry point & screen routing
├── requirements.txt     # Python dependencies
├── .gitignore
└── src/
    ├── screens/         # home, teacher and student screens
    └── components/      # reusable UI pieces (e.g. auto-enroll dialog)
```

---

## 🚀 Getting Started

### Prerequisites

- Python **3.10+** (the app uses `match` statements)
- A [Supabase](https://supabase.com/) project
- A webcam and microphone (for face / voice capture)

### 1. Clone the repository

```bash
git clone https://github.com/sbuttam18-pja/intelligent-ai-attendance.git
cd intelligent-ai-attendance
```

### 2. Create a virtual environment

```bash
python -m venv venv

# macOS / Linux
source venv/bin/activate

# Windows
venv\Scripts\activate
```

### 3. Install dependencies

```bash
pip install -r requirements.txt
```

### 4. Configure Supabase

Add your Supabase project credentials (project URL and API key) in the location the code reads them from, for example Streamlit secrets at `.streamlit/secrets.toml`:

```toml
SUPABASE_URL = "your-supabase-project-url"
SUPABASE_KEY = "your-supabase-anon-or-service-key"
```

> ⚠️ Never commit real keys to GitHub. Keep secrets files in `.gitignore`.

### 5. Run the app

```bash
streamlit run app.py
```

Then open <http://localhost:8501> in your browser.

---

## 📖 How It Works

1. **Home screen** – choose to log in as a **Teacher** or **Student**.
2. **Teacher** – creates classes, generates a join link / QR code, and starts attendance.
3. **Student** – registers, enrolls their face and voice, and joins classes via the link or QR code.
4. **Attendance** – the system compares captured face and voice data against enrolled profiles and records attendance in the database.

---

## 🔗 Joining a Class via Link

Students can join directly using a URL like:

```
http://localhost:8501/?join-code=<CLASS_CODE>
```

After logging in as a student, the app automatically opens the enrollment dialog for that class.

---

## 🧩 Troubleshooting

- **`dlib` fails to install** – the project uses `dlib-bin` to avoid compiling; make sure you're on a supported Python version.
- **`face_recognition_models` install error** – requires `git` to be installed, since it installs from GitHub.
- **`setuptools` / `pkg_resources` errors** – `setuptools<70.0.0` is pinned for this reason; don't upgrade it.
- **Camera / mic not working** – allow browser permissions for the site.

---

## 🤝 Contributing

Contributions are welcome!

1. Fork the repository
2. Create a feature branch: `git checkout -b feature/your-feature`
3. Commit your changes: `git commit -m "Add your feature"`
4. Push the branch: `git push origin feature/your-feature`
5. Open a Pull Request

---

## 📄 License

No license has been specified yet. Add a `LICENSE` file (e.g. MIT) to define how others may use this project.

---

## 👤 Author

**sbuttam18-pja** – [GitHub Profile](https://github.com/sbuttam18-pja)

If you find this project useful, please consider giving it a ⭐!
