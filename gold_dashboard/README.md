# Gold stock-transfer monitor

Who holds the stock, and which way it is moving. Phone-first Streamlit
dashboard; two tabs (Declared / Inferred); five sources; one derived thesis
series (the reported-vs-estimated gap).

## Run

    pip install -r requirements.txt
    python ingest.py --synthetic      # sample data, runs immediately
    streamlit run app.py

## Layout

Desktop-first as of this build: `layout="wide"`, capped at 1180 px, side-by-side
rows where continuity is not lost. The phone-first single-column rationale is
recorded in notebook §7 and in the HTML mockup.

## Live data

    python ingest.py --all

`price` (COMEX futures + FRED real yield) works out of the box. `etf`,
`declared`, `gap`, `swiss` raise NotImplementedError with the exact endpoint
and schema to fill in — issuer URLs and the IMF SDMX call are the two pieces
that drift, so they are isolated in `ingest.py` and nowhere else. The app
only ever reads `data/*.csv`; every pull also lands a timestamped vintage in
`data/vintages/` because customs and IMF sources revise silently.

## Files

    app.py                          the dashboard
    design.py                       entity hues, epistemic grammar, events, mine constants
    ingest.py                       one function per source; --synthetic sample generator
    how_the_dashboard_is_built.ipynb  the reasoning: sources, derived series, gestalt, layout
    data/                           CSVs the app reads

Design contract: solid = reported, dashed = estimated; one colour per country
on every panel; the same event rules on every time axis; one bordered region
(the KPI strip); one dominant chart per tab. The notebook records why.

## Student adaptation: Compare countries

The new **Compare countries** tab asks who bought more and when. Select countries
and a month range to compare period totals beside grouped monthly bars. The
controls affect this tab only; the original Declared ranking still shows the
latest 12 months. Empty selection shows guidance, and selected rows can be
downloaded as CSV. Stable country colours are shared across all tabs.

The supplied CSV values are synthetic teaching data produced by `ingest.py`,
not live observations. A prominent sample-data notice applies to all views.

### Hosting

From this repository, set the Streamlit Community Cloud main file to
`gold_dashboard/app.py`. Keep its adjacent `requirements.txt` and `data/`
folder. Alternatively, upload the contents of `gold_dashboard/` to a separate
public repository and select `app.py`. After deployment, open the public URL
in a private browser window and check country selection, month range, empty
selection and CSV download. Submit the actual deployed URL as a plain text
file through Canvas.
