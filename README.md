# Streamlit 2 — Multipage app

This app follows the official [Create a multipage app tutorial](https://docs.streamlit.io/get-started/tutorials/create-a-multipage-app).
Streamlit discovers the scripts in `streamlit2/pages/` beside `streamlit2/Hello.py`
and builds sidebar navigation automatically. This separate directory keeps
Uber pickups and AppStar single-page apps.

| File | View |
| --- | --- |
| `streamlit2/Hello.py` | Welcome page and learning resources |
| `streamlit2/pages/1_📈_Plotting_Demo.py` | Animated random-walk chart, progress indicator, and rerun button |
| `streamlit2/pages/2_🌍_Mapping_Demo.py` | San Francisco bike and BART data with four selectable map layers |
| `streamlit2/pages/3_📊_DataFrame_Demo.py` | UN agricultural production table and chart with country selection |

The tutorial's data URLs use HTTPS here. The map uses Pydeck's public Carto
light basemap so no Mapbox API key is required. `uber_pickups.py` (Streamlit 1)
and `star_app.py` (AppStar) remain available as separate entrypoints.

## Run locally

```sh
python3 -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
streamlit run streamlit2/Hello.py
```

If the macOS Python installation reports `CERTIFICATE_VERIFY_FAILED`, run:

```sh
export SSL_CERT_FILE="$(python -m certifi)"
streamlit run streamlit2/Hello.py
```

For Streamlit 1, run `streamlit run uber_pickups.py` and use `uber_pickups.py`
as its Community Cloud entrypoint. For Streamlit 2, use `streamlit2/Hello.py`.
If Streamlit 2 was deployed with the old `Hello.py` path, update its entrypoint
or redeploy it with the new path.

## Deploy and submit

1. Ensure `647messi/36104_AT2_PartA_S2_C` is public on GitHub.
2. Sign in at https://share.streamlit.io and create an app from that repository.
3. Select branch `main` and main file path `streamlit2/Hello.py`. Deploy the app.
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
