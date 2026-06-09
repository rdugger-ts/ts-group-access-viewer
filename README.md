# ThoughtSpot Group Access Viewer

A single-page web app that generates a report of group permissions, sharing status, and discoverability for Liveboards, Answers, and Models across your ThoughtSpot instance.

## Features

- **Group permissions** — lists every non-system group with its members and the Liveboards, Answers, and Models each group can access
- **Org-wide share report** — shows which Liveboards and Answers are explicitly shared vs. owner-only
- **Discoverability badges** — flags Answers that have lenient discoverability enabled
- **Org support** — auto-detects whether your cluster supports Orgs; if so, lets you scope the report to a specific Org
- **Paged metadata fetch** — pulls all objects in pages to avoid 504 gateway timeouts on large instances

## Running the app

```bash
python3 -m http.server 8000
```

Then open [http://localhost:8000/userAccess.html](http://localhost:8000/userAccess.html) in your browser.

## Authentication

This app uses the ThoughtSpot REST API v2 [`/auth/token/custom`](https://developers.thoughtspot.com/docs/restV2-playground?apiResourceId=http/api-endpoints/authentication/get-custom-access-token) endpoint with a **secret key** (Trusted Authentication).

To get a secret key:
1. In ThoughtSpot, go to **Develop > Customizations > Security Settings**
2. Enable **Trusted Authentication**
3. Copy the generated secret key

## Usage

1. Enter your **ThoughtSpot Host URL**
2. Enter the **Admin Username** to generate the token for
3. Enter the **Secret Key** from Trusted Authentication settings
4. (Optional) Click **Load Orgs** to populate the org selector, then choose an org
5. Click **Run Report**
