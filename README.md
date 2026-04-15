# DSO grid model

Consumed by the [ieee9-bus](https://github.com/Begonia-UC3/ieee9-bus)
DSO simulator. The `dso` service clones this repo via a `git-sync`
sidecar and hot-reloads `model.json` whenever the file's mtime changes.

## Editing

1. Edit `model.json` (4-bus distribution feeder by default).
2. Push to `main`.
3. Within `modelSyncIntervalSeconds` (default 30s), the running DSO
   pod re-reads the model and rebuilds its Y-bus in place — no pod
   restart, WebSocket clients survive.

Live dashboard (when the cluster is running): https://dso.cozystack-demo.org

## Schema

Documented at the top of [`dso/main.py`](https://github.com/Begonia-UC3/ieee9-bus/blob/dso/dso/main.py).
Minimum shape: `s_base`, `buses[]`, `branches[]`, `external_tie`.
