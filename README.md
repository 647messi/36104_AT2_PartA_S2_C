# Streamlit 2 — Multipage app

This app follows the official [Create a multipage app tutorial](https://docs.streamlit.io/get-started/tutorials/create-a-multipage-app).
Streamlit discovers the scripts in `pages/` and builds sidebar navigation automatically.

| File | View |
| --- | --- |
| `Hello.py` | Welcome page and learning resources |
| `pages/1_📈_Plotting_Demo.py` | Animated random-walk chart, progress indicator, and rerun button |
| `pages/2_🌍_Mapping_Demo.py` | San Francisco bike and BART data with four selectable map layers |
| `pages/3_📊_DataFrame_Demo.py` | UN agricultural production table and chart with country selection |

The tutorial's data URLs use HTTPS here. The map uses Pydeck's public Carto
light basemap so no Mapbox API key is required. `uber_pickups.py` (Streamlit 1)
and `star_app.py` (AppStar) remain available as separate entrypoints.

## Run locally

```sh
python3 -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
streamlit run Hello.py
```

If the macOS Python installation reports `CERTIFICATE_VERIFY_FAILED`, run:

```sh
export SSL_CERT_FILE="$(python -m certifi)"
streamlit run Hello.py
```

## Deploy and submit

1. Ensure `647messi/36104_AT2_PartA_S2_C` is public on GitHub.
2. Sign in at https://share.streamlit.io and create an app from that repository.
3. Select branch `main` and main file path `Hello.py`. Deploy the app.
   Use a separate deployment if an earlier assignment still needs its own URL.
4. Open the deployed URL in a private/incognito browser window without signing in.
   Visit all three demos using the sidebar. Confirm the plotting animation runs,
   the map renders and its layer checkboxes work, and country selection updates
   the dataframe and chart. With all layers or countries deselected, each page
   should show a helpful message rather than crash.
5. Save only the actual deployed URL in a plain text file named `submission.txt`
   and upload it to Canvas.

Community Cloud assigns the deployed URL. Submit that app URL, not the GitHub
repository URL or the official tutorial's example app.
