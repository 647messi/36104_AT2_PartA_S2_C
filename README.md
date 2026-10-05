# Streamlit 1 — Uber pickups in NYC

An interactive app following the official tutorial:
https://docs.streamlit.io/get-started/tutorials/create-an-app

The app downloads and caches 10,000 Uber pickup records from September 2014,
shows a 24-hour histogram, maps pickups for the selected hour, and provides
a checkbox to show or hide the raw data.

## Run locally

```sh
python3 -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
streamlit run uber_pickups.py
```

If the macOS Python installation reports `CERTIFICATE_VERIFY_FAILED`, run:

```sh
export SSL_CERT_FILE="$(python -m certifi)"
streamlit run uber_pickups.py
```

## Deploy and submit

1. Push the app and requirements.txt to the public GitHub repository
   `647messi/36104_AT2_PartA_S2_C` on branch `main`.
2. Sign in at https://share.streamlit.io and create an app from that repository.
3. Set the main file path to `uber_pickups.py` and deploy.
4. Open the resulting app URL in a private/incognito browser window. Confirm
   the histogram and map appear, moving the hour slider changes the map, and
   the checkbox shows and hides the raw data without requiring sign-in.
5. Save only the deployed URL in a plain text file named `submission.txt` and
   upload it to Canvas.

The deployed URL is assigned by Community Cloud; the repository URL is not
the app URL to submit.
