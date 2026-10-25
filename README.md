
A lightweight, file‑system based model registry for machine‑learning artifacts.  
Store binary model files together with versioned metadata, retrieve them easily, and keep a searchable index—all without a database.

## Features
- Simple local storage (no external services)
- Automatic SHA‑256 checksum for integrity verification
- Versioned models with custom tags
- JSON index for quick look‑ups
- Minimal CLI for registration and retrieval

## Installation
```bash
git clone https://github.com/yourname/ModelVault.git
cd ModelVault
# No external dependencies beyond the Python standard library
```

## Usage

### Register a model
```bash
python model_vault.py register path/to/model.pt my_model v1.0 --tags production experimental
```

### Retrieve model info
```bash
python model_vault.py get my_model v1.0
```

The command prints the model’s metadata (name, version, checksum, tags, timestamp) and the absolute path to the stored file.

## Programmatic API
```python
from model_vault import ModelVault

vault = ModelVault()
vault.register("model.pt", "my_model", "v1.0", tags=["production"])
info = vault.get("my_model", "v1.0")
print(info["metadata"])