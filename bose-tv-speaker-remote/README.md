# Bose TV Speaker Remote (IR)

This blueprint sends Bose TV Speaker IR commands through an IR blaster's text entity. It ships with hardcoded base-64 IR payloads for eight commands — On/Off, Volume Up, Volume Down, Mute, Bluetooth, Bass, Dialogue, and TV — but every code can be overridden per-instance if your unit uses a different IR set.

Each command is wired to its own fully custom trigger selector, so you can fire any command from any source: a Zigbee or Z-Wave remote button, a dashboard tap, a voice assistant intent, a state change, a schedule, an incoming webhook, etc. Leave a trigger empty to disable that command.
