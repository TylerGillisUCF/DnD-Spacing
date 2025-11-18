# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

**DnD-Spacing** - A repository for "The Shadowspire Campaign", a family-friendly D&D adventure.

The repository currently contains the master campaign script document (`MASTER SCRIPT DND NIGHT.docx`), which is a complete 9-part D&D campaign designed for a family game night. The campaign features:
- Three separate player paths (Crimson/Warrior, Golden/Treasure Hunter, Silver/Diplomat)
- 36 unique cameo encounters across all paths
- A simplified rule system focused on fun over death/failure
- Character progression through skill points rather than traditional leveling
- Approximately 4-6 hours of gameplay

## Project Status

This is an early-stage repository. No code implementation exists yet. The project may evolve into:
- A digital campaign management tool
- A web-based interactive story platform
- A campaign tracker with character progression
- A print-ready campaign formatter

## Working with the Campaign Document

The master script is stored as a Microsoft Word document (`.docx` format). To extract text content:

```bash
# Extract docx contents (docx files are zip archives)
unzip -q -o "MASTER SCRIPT DND NIGHT.docx" -d /tmp/docx_extract

# Parse document.xml to read text content
python3 -c "
import xml.etree.ElementTree as ET
tree = ET.parse('/tmp/docx_extract/word/document.xml')
ns = {'w': 'http://schemas.openxmlformats.org/wordprocessingml/2006/main'}
text_elements = tree.getroot().findall('.//w:t', ns)
text = ''.join([elem.text for elem in text_elements if elem.text])
print(text)
"
```

## Git Workflow

Currently on branch: `claude/init-project-setup-01CGFDNwxWgdR7ZF3XeTTwbo`

When making changes:
```bash
# Stage and commit
git add .
git commit -m "Descriptive message"

# Push to current branch
git push -u origin claude/init-project-setup-01CGFDNwxWgdR7ZF3XeTTwbo
```

## Development Setup (When Code is Added)

This section will be updated once the project type is determined. Potential tech stacks might include:
- **Web app**: Node.js + React/Vue, Python + Flask/Django
- **Desktop app**: Electron, Python + PyQt/Tkinter
- **CLI tool**: Python, Node.js, or Go
- **Documentation site**: Jekyll, Hugo, or Markdown → PDF tools

## Campaign Structure Reference

The campaign follows this structure:
1. Opening Scene - Howling Moon Tavern (all players together)
2. The Taking - Leader captured by Void Tyrant
3. Path Selection - Players split into three paths
4. Separate Adventures - 12 encounters per path (36 total)
5. Midway Reunion - Max & Luna's Talent Show
6. Final Encounters - Last challenges before reunion
7. The Reunion - Heroes unite with their mystical keys
8. Boss Fight - Void Tyrant confrontation
9. Victory - Campaign conclusion

Each player path collects a different mystical key:
- **Nick (Warrior/Crimson Path)** → Key of Power
- **Christopher (Treasure Hunter/Golden Path)** → Key of Fortune
- **Lena (Diplomat/Silver Path)** → Key of Knowledge

## Core Campaign Mechanics

- **No Death System**: Low rolls result in funny/embarrassing outcomes, never death
- **Guaranteed Progression**: Story always moves forward
- **Skill Point System**: Characters earn skill points instead of traditional XP
- **Economy**: Balanced gold/item system rewards smart play
- **Time**: ~4-6 hours total playtime

## Future Considerations

When implementing features, consider:
- Preserving the three-path structure of the campaign
- Supporting the simplified, family-friendly rule system
- Tracking skill point progression per character
- Managing the 36 unique cameo encounters
- Handling the midway reunion and final boss mechanics
