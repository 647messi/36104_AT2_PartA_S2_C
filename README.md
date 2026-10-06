# Streamlit Applications

36104 Assignment 2, Part A, Session 2-C.

This repository contains two Streamlit tutorial apps and an AppStar visualization.
Each app has its own entrypoint and can be run or deployed separately.

## Applications

### Streamlit 1: Uber pickups in NYC

Based on the official [Create an app tutorial](https://docs.streamlit.io/get-started/tutorials/create-an-app).

- Downloads and caches 10,000 Uber pickup records from September 2014.
- Displays a histogram of pickups by hour.
- Maps pickup locations for the hour selected with a slider.
- Shows or hides the raw dataset with a checkbox.

Entrypoint: `uber_pickups.py`.

### Streamlit 2: Multipage demo

Based on the official [Create a multipage app tutorial](https://docs.streamlit.io/get-started/tutorials/create-a-multipage-app).

- **Hello:** Welcome page and links to learning resources.
- **Plotting Demo:** Animated random-walk chart with progress and a rerun button.
- **Mapping Demo:** San Francisco bike and BART data with four selectable map layers.
- **DataFrame Demo:** UN agricultural production table and chart with country selection.

Entrypoint: `streamlit2/Hello.py`.

Streamlit automatically builds sidebar navigation from the adjacent `pages/`
folder. Keeping this folder inside `streamlit2/` prevents the multipage navigation
from appearing in Uber pickups or AppStar.

The tutorial data URLs use HTTPS. The mapping demo uses a public Carto light
basemap and does not require a Mapbox API key.

### AppStar

An interactive stellar-evolution visualization with mass and age controls,
a star portrait, and a Hertzsprung–Russell diagram.

Entrypoint: `star_app.py`.

## Project structure

```text
.
├── README.md
├── requirements.txt
├── uber_pickups.py
├── star_app.py
└── streamlit2/
    ├── Hello.py
    └── pages/
        ├── 1_📈_Plotting_Demo.py
        ├── 2_🌍_Mapping_Demo.py
        └── 3_📊_DataFrame_Demo.py
```

## Run locally

Run these commands from the repository root:

```sh
python3 -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
```

Start the app you want to use:

```sh
# Streamlit 1
streamlit run uber_pickups.py

# Streamlit 2
streamlit run streamlit2/Hello.py

# AppStar
streamlit run star_app.py
```

The tutorial apps need internet access to download their datasets and display
map tiles. Dataset downloads are cached using `st.cache_data`.

If a macOS Python installation reports `CERTIFICATE_VERIFY_FAILED`, configure
its trusted certificate bundle before starting the app:

```sh
export SSL_CERT_FILE="$(python -m certifi)"
```

## Deploy with Streamlit Community Cloud

1. Make sure this GitHub repository is public.
2. Sign in to [Streamlit Community Cloud](https://share.streamlit.io).
3. Create an app using repository `647messi/36104_AT2_PartA_S2_C` and branch `main`.
4. Choose the main file path from the table below, then deploy.

| Application | Main file path |
| --- | --- |
| Streamlit 1 | `uber_pickups.py` |
| Streamlit 2 | `streamlit2/Hello.py` |
| AppStar | `star_app.py` |

Create separate deployments when each assignment needs its own URL.
If an existing Streamlit 2 deployment uses `Hello.py`, update its entrypoint
or redeploy with `streamlit2/Hello.py`.

## Verify and submit

Open each deployed tutorial app in a private/incognito browser window to check
that visitors can use it without signing in.

- **Streamlit 1:** Confirm the histogram and map load, the hour slider updates
  the map, and the checkbox shows and hides the raw data.
- **Streamlit 2:** Visit all pages through the sidebar. Confirm the plotting
  animation runs, map layer checkboxes update the map, and country selection
  updates the table and chart. Deselecting all layers or countries should show
  a helpful message without crashing.

For each assignment, save its deployed app URL alone in a plain text file
such as `submission.txt`, then upload that file to Canvas. Use the actual
Community Cloud app URL, rather than the GitHub repository or tutorial demo URL.
