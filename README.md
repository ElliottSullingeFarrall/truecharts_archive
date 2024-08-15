# TrueNAS SCALE catalog

This is a fork of the archived TrueCharts App Catalog for TrueNAS SCALE.

# Updating Charts

To update a chart start by creating a subdirectory `<chartVersion>` in the charts directory (can copy from a previous version).

In the `Chart.yaml`, update the version numbers like:
```YAML
...
apiVersion: v2
appVersion: <appVersion>
...
version: <chartVersion>
```

In `ix_values.yaml` update the `tag` to use `<appVersion>`. Next find the `app_version.json` for the chart and update the versions like:
```JSON
{
	"<chartVersion>": {
        ...
        "location": ".../<chartVersion>",
        "last_update": "...",
        ...
        "human_version": "<appVersion>_<chartVersion>",
        "version": "<chartVersion>",
        "chart_metadata": {
            ...
            "apiVersion": "v2",
            "appVersion": "<appVersion>",
            ...
            "version": "<chartVersion>"
        },
		...
	},
	...
```

Finally update the charts entry in `catalog.json` to include the new version.
```JSON
...
"latest_version": "<chartVersion>",
"latest_app_version": "<appVersion>",
"latest_human_version": "<appVersion>_<chartVersion>",
"last_update": "...",
...
```