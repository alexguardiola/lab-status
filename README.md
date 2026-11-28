# lab-status

Status of the systems I run at home and write about on my blog. My Raspberry Pi rewrites `lab-status.json` once an hour and pushes it here. The `/lab` page on my site reads it from GitHub, so the Pi never has to accept a connection from outside.

## What is in the file

```json
{
  "generatedAt": "2026-10-25T11:28:45+00:00",
  "systems": [
    { "id": "price-watch", "status": "up", "lastRun": "2026-10-25T11:00:04+00:00", "uptime30d": 99.6 }
  ]
}
```

- `status` is `up`, `down` or `paused`. Down means the last check failed. Paused means I turned it off on purpose.
- `lastRun` is the last time it ran, when that is tracked.
- `uptime30d` is the share of hourly samples marked `up` over the last 30 days, leaving out paused hours. It only shows up after a day of samples.

All times are UTC. Those are the only fields. Hostnames, addresses, paths and internal names stay on the Pi, and the site rejects the whole file if any other field turns up.

## History

Each run amends the same commit and force-pushes it, so the branch only holds the latest snapshot.
