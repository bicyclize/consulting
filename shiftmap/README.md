# shiftmap (published copy)

This directory is a **generated copy** of the [`bicyclize/shiftmap`](https://github.com/bicyclize/shiftmap)
site, published at <https://bicyclize.com/shiftmap/>.

Source commit: `0ca233f` (force https on Mapbox tile requests)

Do **not** edit files here — edit and rebuild in `bicyclize/shiftmap`, then refresh this copy:

```sh
SRC=$(mktemp -d)/shiftmap
git clone --depth 1 --single-branch https://github.com/bicyclize/shiftmap.git "$SRC"
cd ~/bicyclize-consulting/shiftmap
cp "$SRC"/{index.html,style.json,summary.json,*.parquet} .
mkdir -p vendor && cp "$SRC"/vendor/* vendor/
# then: git add -A shiftmap && git commit -m "Refresh shiftmap copy" && git push
```

Published files (all loaded with relative paths, so the subdirectory works as-is):

- `index.html`, `style.json`, `summary.json`
- `vendor/` (MapLibre GL JS/CSS, hyparquet + decompressors)
- `alt_routes.parquet`, `alt_stations.parquet`, `alt_summary.parquet`, `rail_mode.parquet`,
  `route_len.parquet`, `routed_edges.parquet`, `routed_geom.parquet`, `trips_attrs.parquet`
  (fetched over HTTP range requests, so visitors only download the byte ranges they need)

The parquet files are ~93 MB in total, which is why this is a copy rather than the
source of truth. Keep an eye on the GitHub Pages site size limit (1 GB).
