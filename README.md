# API Data Extraction with Python

Two short Jupyter notebooks that pull JSON data from public APIs using `requests`, load it into a `pandas` DataFrame, and export it as CSV.

Built as part of my Data Science & Analytics program at LuxDevHQ Academy.

## Notebooks

| Notebook | Source | Data |
|----------|--------|------|
| `Untitled3.ipynb` | [DummyJSON Users API](https://dummyjson.com/users) | Fake user profiles (name, age, contact, address, company, etc.) returned as a nested JSON object |
| `Untitled4.ipynb` | [LuxDev staff dataset](https://raw.githubusercontent.com/odhiambokevin/luxdev_staff_python_project/refs/heads/main/staff_data.json) | Staff records (name, department, salary, employee ID) returned as a JSON list |

## Workflow

1. Send a `GET` request with `requests` and check `status_code == 200`
2. Parse the response with `.json()`
3. Load the parsed data into a pandas DataFrame
4. Export to CSV with `to_csv()`

```python
import requests
import pandas as pd

response = requests.get("https://dummyjson.com/users")
data = response.json()

df = pd.json_normalize(data["users"])   # flattens nested fields
df.to_csv("users.csv", index=False)
```

For the staff dataset the JSON is already a flat list, so `pd.DataFrame(data)` works directly.

## Getting Started

```bash
git clone https://github.com/<your-username>/<repo-name>.git
cd <repo-name>
pip install requests pandas jupyter
jupyter notebook
```

## Tech Stack

Python, Requests, pandas, Jupyter Notebook

## What I Practiced

- Calling REST APIs and handling HTTP status codes
- Working with nested vs. flat JSON
- Flattening JSON into tabular form
- Exporting clean CSV files

## Author

**Stephen Omengo Owuor**
