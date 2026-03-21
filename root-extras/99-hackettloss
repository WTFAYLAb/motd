#!/usr/bin/env bash

printf "\nLatest 'Hacketloss' entries:\n"

HackettLogs=$(
	tail -5 /usr/local/src/Hackettloss/output.log \
	| awk '{ if (match($0, /\[([0-9]{10})\]/, m)) { cmd="date -d @" m[1] " \"+%Y-%m-%d %H:%M:%S\""; cmd | getline human; close(cmd); sub(/\[[0-9]{10}\]/, human) } print }' \
	| sed 's/^/  /'
)

printf "%s\n" "$HackettLogs"