### Minimal ADC Server (mADC) Documentation

#### Overview
Flask-based web application for the Minimal ADC server (mADC), adhering to a subset of the AIRR Data Commons API. This implementation allows interrogation of available repertoires and downloading specified repertoire data.
This app also scannin the projects over the server before it come up, creating metadata and moving files into the app file system.

## GitHub
  [GitHub](https://github.com/yaarilab/Minimal_ADC) repository

#### System Requirements
- Python 3.10
- Flask 2.3.3
- Flask-RESTX

#### Setting Up the Server
1. **Installation**: Ensure Python 3.10, Flask 2.3.3, and Flask-RESTX are installed.
2  **Clone repository**
   - Use the command `git clone https://github.com/yaarilab/Minimal_ADC`
3. **Setup the madc.py**
   - Navigate to `madc.py`
   - Set `STUDIES_PATH` and `STUDIES_TO_COPY_PATH`
4. **Starting the Server**:
   - Navigate to the `app` directory thats containing `app.py`.
   - Run the command `python app.py` to start the Flask server.


#### Adding new dataset
1. **update the configuration file**: locate under `/work/scripts/transfer_madc_data/` called studies_to_copy.json.
   you should add to the json file the name and the path of the new dataset like that:

```json
"name": "PRJEB26509_IGK",
"path": "/work/mADC/studies/PRJEB26509_IGK/",
```
2. navigate to `/work/scripts/transfer_madc_data/`
3. Run the script using the following command:

   ```
   python transfer_madc_studies.py
   ```

---

#### Key Components
1. **app.py**: The main Flask application file.
2. **madc.py**: Configuration settings for the application.
3. **repertoire.py**: API endpoints for repertoire-related operations.
4. **service.py**: API endpoints for service-related operations.
5. **utils.py**: Utility functions for server setup.



#### Configuration (madc.py)
- Defines settings like `DEBUG`, `HOST`, `PORT`, and file paths (`STUDIES_PATH`, `STUDIES_TO_COPY_PATH`).
- Includes API metadata (`API_VERSION`, `API_TITLE`, `API_DESCRIPTION`).

#### Main Application (app.py)
- Initializes the Flask application and configures logging.
- Loads configuration from `madc.py`.
- Sets up API namespaces and routes for service, repertoire, and rearrangement operations.
- On startup, prepares the server environment and loads study data.

---

#### API Endpoints
1. **Service Namespace (service.py)**
   - `/v1`: Returns the status of the service.
   - `/v1/info`: Provides information about the API.

2. **Repertoire Namespace (repertoire.py)**
   - `/v1/repertoire/{repertoire_id}`: Retrieves information for a specific repertoire.
   - `/v1/repertoire`: Accepts POST requests to list repertoires based on filters.

3. **Rearrangement Namespace (repertoire.py)**
   - `/v1/rearrangement`: Handles POST requests for rearrangement data, supporting counts and file retrieval in TSV format.

#### API Restrictions
- **Repertoire Endpoint**: Supports filtering by `study_id`. Other filter parameters are rejected.
- **Rearrangement Endpoint**: Requires a filter specification identifying repertoires by `repertoire_id`.

---


#### Utility Functions (utils.py)

*   **before\_server\_loads**: Prepares the server environment.
---

#### Business Logic
- The application scans the studies directory on startup, creating an in-memory map of repertoires to file paths.
- The file structure is assumed to be static during execution.
