Regex used to capture params

find (regex): `~(.+) \(.+, default: (.+)\)\n`
replace: : `#$1: $2 # Default: $2 `
