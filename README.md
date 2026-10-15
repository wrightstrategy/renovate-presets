# Wright Strategy Renovate presets

This public repository serves the shared `default.json` Renovate preset. Public
repositories extend `github>wrightstrategy/renovate-presets`. Private
repositories extend Bridge's private preset, which adds private package
authentication and a Bridge-specific custom manager to this base.

Bridge owns the policy and publishes this repository's `default.json` and
`README.md` through its repository audit. Edit
`wrightstrategy/bridge/renovate-config/public.json` or
`wrightstrategy/bridge/renovate-config/public-README.md`, then
review the generated publication PR here. Do not edit the published copy by
hand.

The public preset contains no package credentials or Bridge-specific custom
managers. Those remain in Bridge's private overlay.
