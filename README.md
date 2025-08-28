# pdf-extract-flow
# PDF‑Table‑Marker – Flowchart

```mermaid
flowchart TD
    %% ==== 1️⃣ Entry point ==================================================
    Start["Start:\npython pdf_table_marker.py &lt;PDF&gt; [page]"]

    %% ==== 1️⃣ Load PDF & render page =========================================
    subgraph LoadAndRender["1️⃣ Load PDF & render page"]
        A1["Validate PDF path"] --> A2["Open with pdfplumber"]
        A2 --> A3{"Is page number valid?\n(1‑len(pages))"}
        A3 -- Yes --> A4["Select page (0‑based)"]
        A3 -- No --> A5["Raise ValueError & exit"]
        A4 --> A6["Render page → Pillow image (150 dpi)"]
        A6 --> A7["Return (pdfplumber.Page, PIL.Image)"]
    end

    %% ==== 2️⃣ Interactive line‑drawing UI ====================================
    subgraph UI["2️⃣ Interactive line‑drawing UI"]
        B1["Create Matplotlib Figure/Axes"] --> B2["Show image as background"]
        B2 --> B3["Instantiate LineDrawer(ax, img_w, img_h)"]
        B3 --> B4["Attach callbacks:\n • press → on_key\n • mouse ↓ → on_press\n • drag → on_move\n • release → on_release"]
        B4 --> B5["Display instruction overlay"]
        B5 --> B6["User draws lines:\n • ‘v’ → vertical mode\n • ‘h’ → horizontal mode\n • click‑drag → temp line\n • release → commit line\n • ‘c’ → clear all\n • ‘q’ → quit"]
        B6 --> B7["Lines stored in:\n • vert_lines (x‑coords)\n • horiz_lines (y‑coords)"]
        B7 --> B8["Press <Enter> → close figure → exit UI loop"]
    end

    %% ==== 3️⃣ Build grid from separators =====================================
    subgraph BuildGrid["3️⃣ Build grid from separators"]
        C1["Add page borders (0 & width/height) to the line lists"]
        C2["Sort vertical & horizontal coordinate arrays"]
        C3["Create rectangular cells from adjacent pairs"]
        C4["Store cell bounds (x0,x1,y0,y1) in a list (row‑major)"]
        C1 --> C2 --> C3 --> C4
    end

    %% ==== 4️⃣ Extract cell contents ==========================================
    subgraph Extract["4️⃣ Extract cell contents"]
        D1["Iterate over each cell"]
        D2["Crop region from pdfplumber.Page"]
        D3["Call .extract_text() (or .within_bbox) → string"]
        D4["Append string to current row list"]
        D5["When row complete → add row to table list"]
        D1 --> D2 --> D3 --> D4 --> D5
    end

    %% ==== 5️⃣ Output JSON =====================================================
    subgraph Output["5️⃣ Output JSON"]
        E1["Convert 2‑D list → dict {\table\: [...]}"]
        E2["json.dump(..., indent=2)"]
        E3["Write to <pdf_stem>_pageN.json (or stdout)"]
        E1 --> E2 --> E3
    end

    %% ==== Error handling ======================================================
    subgraph Errors["Error handling"]
        Err1["FileNotFoundError (PDF missing)"]
        Err2["ValueError (invalid page)"]
        Err1 --> End
        Err2 --> End
    end

    %% ==== Flow connections ====================================================
    Start --> LoadAndRender --> UI --> BuildGrid --> Extract --> Output --> End([End])

    %% ==== Early‑exit paths (quit / clear) =====================================
    B6 -->|press ‘q’| End
    B6 -->|press ‘c’| B4   %% clears lines, returns to drawing mode
