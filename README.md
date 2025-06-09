# Python Project with `uv`

This is a Python project that uses [`uv`](https://github.com/astral-sh/uv) for dependency management and virtual environment handling.

## 🚀 Getting Started

### 1. Prerequisites

Make sure you have `uv` installed. If not, you can install it via:

```bash
curl -Ls https://astral.sh/uv/install.sh | sh
```

Or refer to the official [uv installation guide](https://github.com/astral-sh/uv#installation) for your platform.

### 2. Clone the Repository

```bash
git clone https://github.com/your-username/your-project.git
cd your-project
```

### 3. Set Up the Environment

You can use `uv` to set up your Python environment in a modern and efficient way.

#### Option A: Using `requirements.txt`

```bash
uv venv
uv pip install -r requirements.txt
```

This will:

* Create a virtual environment in `.venv`.
* Activate the environment automatically.
* Install all dependencies listed in `requirements.txt`.

#### Option B: Using `pyproject.toml` and `uv sync` *(Recommended)*

If your project uses a `pyproject.toml` (recommended modern approach):

```bash
uv sync
```

This will:

* Automatically create and activate a `.venv` if one doesn't exist.
* Install dependencies declared in `pyproject.toml`.
* Use `uv.lock` if present for reproducible installs.

To update the lock file after changing dependencies:

```bash
uv pip install <new-package>
uv pip freeze > requirements.txt  # optional legacy support
uv lock
```

To activate the environment manually later:

* **Linux/macOS**:

  ```bash
  source .venv/bin/activate
  ```
* **Windows (PowerShell)**:

  ```powershell
  .venv\Scripts\Activate.ps1
  ```

### 4. Configure Environment Variables

This project uses a `.env` file to manage configuration values.

1. Copy the example file:

   ```bash
   cp .env.example .env
   ```

2. Open `.env` in a text editor and update the values as needed:

   ```env
   DEBUG=True
   DATABASE_URL=postgresql://user:password@localhost:5432/dbname
   SECRET_KEY=your-secret-key
   ```

> Make sure not to commit sensitive `.env` values to version control.

---

## ✅ Running the Project

Once the environment is set up and `.env` values are configured, you can run the project as usual:

```bash
uv pip install python-dotenv  # if not already installed
python main.py
```

---

## 🛠 Notes

* Use `uv pip install <package>` to add new dependencies.
* Use `uv lock` to generate a `uv.lock` file for reproducible installs.
* Use `uv sync` to quickly install all dependencies from `pyproject.toml` and `uv.lock`.
* Use `uv pip freeze > requirements.txt` if you need to maintain compatibility with legacy systems.
* `uv` handles both virtual environments and dependency management, replacing tools like `pip`, `venv`, and `pip-tools`.

---

## 📄 License

This project is licensed under the MIT License.
