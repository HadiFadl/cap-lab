# CAP Lab — Interactive Distributed Database Simulator (v6)

CAP Lab is a standalone, browser-based teaching simulator for CAP theorem and replicated database operations. It includes 3–5 geographically distributed replicas, network partitions, replica failures, delayed multi-hop synchronization, yellow lag flags, leader/follower roles, and INSERT / UPDATE / DELETE / READ operations.

## New in v6

- **Guided scenarios in Presentation Mode:** the same five experiments offered in Exploration Mode are now selectable and runnable from the presentation toolbar.
- **On-map guided instruction panel:** when an experiment is active, its current instruction, explanatory hint, and step progress appear in the lower-left corner of the world map **in both modes**. It advances automatically as the student completes actions and can be collapsed or exited.
- **Compact presentation provider selector:** clickable database icons and short labels appear directly in Presentation Mode, filtered by CA, CP, or AP. The same provider architecture profiles are shared with Exploration Mode (including SQL Server under CA and CP). Descriptions and documentation remain in Exploration Mode.
- **Guided scenarios and provider selection work together:** starting a scenario preserves a previously selected provider if it supports that scenario's CAP mode. Changing a provider while a matching scenario is in progress restarts that scenario at step 1 so instructions remain consistent.
- **View changes preserve state:** switching between Exploration and Presentation preserves current scenario progress, network failures, database values, and asynchronous replication progress.

## Run locally

Open `index.html` in a modern browser. No setup, database server, or build process is required. All simulation logic and map imagery are embedded. External provider logos may load from a CDN when online, with built-in illustrated icon fallbacks for offline use.

## Publish to GitHub Pages

1. Create a **public** GitHub repository such as `cap-lab`.
2. Upload `index.html`, `README.md`, and `.nojekyll` from this package into the repository root, not the ZIP file.
3. Navigate to **Settings → Pages**. Under Build and deployment choose **Deploy from a branch**, branch `main`, folder `/ (root)`, then save.
4. When deployment is complete, visit `https://YOUR-USERNAME.github.io/cap-lab/`.

If an earlier CAP Lab version is already published, simply replace the existing `index.html` and commit the update. Its public URL stays the same.

## Testing

The app's **17 built-in simulation checks** passed, together with browser interaction tests for guided scenario controls in both display modes, map instruction progression/collapse/expand, presentation provider selection across CAP families, scenario/provider compatibility, and mobile presentation controls.

You can run the built-in checks with `?selftest=1` after the website URL, or call `CAPLab.runSelfTests()` in developer tools. Opening this test mode resets its local simulation state afterward.

## Educational note

Database provider selections are **teaching approximations**, not exact production emulations. CAP properties depend on deployment, consistency settings, network conditions, and workload. SQL Server Always On failover depends on WSFC and AG configuration beyond this simplified lab's model. CA's fixed-primary example can serve reachable clients during a partition but does not provide CAP availability for clients isolated from that primary.
