---
tags:
  - note
---
To test building and serving this site locally, use the following:

```bash
python -m venv venv
# On Windows
.\venv\Scripts\activate
# On Linux/Mac
source ./venv/bin/activate

pip install -r requirements

mkdocs serve
```

View the served site at http://localhost:8000/