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

### Basic Rules
- **No Death System**: Low rolls result in funny/embarrassing outcomes, never death
- **Guaranteed Progression**: Story always moves forward
- **Skill Point System**: Characters earn 1 skill point per encounter (start with 12, end with ~29-30)
- **Time**: ~4-6 hours total playtime

### Skill Points & Modifiers
Players distribute points across six stats (STR, DEX, CON, INT, WIS, CHA). Points determine modifiers added to rolls:
- 1-2 points = -2 modifier
- 3-4 points = -1 modifier
- 5-6 points = +0 modifier
- 7-8 points = +1 modifier
- 9-10 points = +2 modifier
- 11-12 points = +3 modifier
- 13-14 points = +4 modifier
- 15-16 points = +5 modifier
- 17+ points = +6 modifier

### Dice System
Different dice for different difficulty levels:
- **d4**: Simple decisions, minor tasks
- **d6**: Standard checks, moderate difficulty
- **d8**: Skilled checks, moderate-to-hard
- **d10**: Challenging checks, important moments
- **d12**: Major checks, high-stakes moments
- **d20**: Epic checks, boss encounters, critical moments

### Critical Rolls
- **Natural 20**: Automatic success + bonus effects + earn 1 coin
- **Natural 1**: Automatic failure + funny consequence + lose 1 coin (except in combat)

### Economy System (240 Total Coins)
**Income:**
- Starting coins: 12 per player
- Per encounter: 5 coins (guaranteed)
- Natural 20 bonus: +1 coin each
- Various challenges: +2-10 coins

**Mandatory Expenses:**
- 3 paid meals @ 5 coins each = 15 coins minimum per player

**Optional Purchases:**
- Vendor items: 3-15 coins (magic items, bonuses, rerolls)
- Gambling/information: 2-10 coins
- High-risk opportunities: Variable

**Penalties:**
- Natural 1 (non-combat): -1 coin
- Failed risky attempts: -3 coins

### Roll Modifiers & Special Mechanics
**Temporary Bonuses/Penalties:**
- +1 to +3 bonuses to specific rolls or all rolls (duration varies)
- -1 to -3 penalties from curses, failed attempts
- Duration: "next roll," "next encounter," "for 2 encounters"

**Advantage/Disadvantage:**
- Roll twice, take higher (advantage) or lower (disadvantage)
- Commonly awarded for success on earlier challenges

**Special Items (Examples):**
- Amulet of Clarity (crucial for final boss)
- Phoenix Tear (15 coins - legendary item, game-changer)
- Ring of Truth-Seeing
- Lucky Coin (from gambling)
- Blessing Tokens (various effects)
- Divine Protection (reroll one failed check)

**Limited Mechanics:**
- Rerolls: Mentioned but rarely implemented
- Auto-success items: Only Natural 20s provide this
- Saving throws: Not implemented

### Encounter Structure
Most cameo encounters follow this pattern:
1. **Challenge 1**: Tests specific stat (often with roleplay/choice element)
   - Success grants advantage or bonus to Challenge 2
   - Natural 20/1 effects apply
2. **Challenge 2**: Often builds on Challenge 1 results
   - May use bonuses/advantage from Challenge 1
   - Success grants bonus to Challenge 3
3. **Challenge 3**: Usually combat or climactic test
   - Accumulates bonuses from previous challenges
   - Determines encounter outcome quality

**Difficulty Classes (DC):**
- Easy: DC 6-8
- Medium: DC 9-11
- Hard: DC 12-14
- Very Hard: DC 15-17
- Nearly Impossible: DC 18+

### Combat Mechanics
- Opposed rolls (Hero vs Enemy)
- Best-of-X format (e.g., best of 3, best of 5)
- First to win X exchanges wins the combat
- **No coin loss on Natural 1 in combat** (unique exception)
- Losing combat results in funny/narrative setbacks, never death

## Future Considerations

When implementing features, consider:
- Preserving the three-path structure of the campaign
- Supporting the simplified, family-friendly rule system
- Tracking skill point progression per character
- Managing the 36 unique cameo encounters
- Handling the midway reunion and final boss mechanics
