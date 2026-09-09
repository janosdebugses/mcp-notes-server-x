# mcp-notes-server-x

Learning MCP: tiny notes server with five tools

Started as a weekend hack, grew on me.

## How to use

```bash
# claude_desktop_config.json  (use ABSOLUTE paths: Claude does not
# run from the repo directory, so a bare "server.py" is not found)
# {
#   "mcpServers": {
#     "notes-box": {
#       "command": "python",
#       "args": ["/abs/path/to/mcp-notes-server-x/server.py"],
#       "env": {"MCP_NOTES_FILE": "/abs/path/to/notes.json"}
#     }
#   }
# }
python server.py --help
```

## Install

```bash
pip install -r requirements.txt
```

## Features

- A missing note raises instead of returning the string 'not found'
- Every tool carries a real docstring, so clients get descriptions
- Notes path set by MCP_NOTES_FILE or --notes-file
- Five tools: add / get / update / delete / list notes
- Atomic saves (temp file + os.replace) behind a write lock
- Includes a Claude Desktop config snippet with absolute paths

## Project structure

```text
├── docs/
│   ├── development.md
│   ├── roadmap.md
│   └── usage.md
├── tests/
│   └── test_notes.py
├── .gitattributes
├── .gitignore
├── CHANGELOG.md
├── SECURITY.md
├── requirements.txt
└── server.py
```

## Development

```bash
python -m venv .venv && source .venv/bin/activate
pip install -r requirements.txt
python -m pytest -q
```

## Why

Needed this for myself; figured others might too.
