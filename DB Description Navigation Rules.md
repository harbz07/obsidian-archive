---
notion-id: 29f98e9c-907e-8161-9595-d2523e3c0b60
---

## Goal
Generate database description pages that exactly match your examples’ look and feel, with correct Notion-flavored Markdown, emojis, colors, links, and spacing.
### High-level pattern
1. Title or context lines as needed
2. One-sentence, plain-language definition of the database
3. Divider
4. “Badge ribbon” of color-highlighted chips linked to related areas

### Authoring rules (Notion-flavored Markdown)
- **Do NOT include backtick ` or asterisk * literals in the text, they are only intended as a reference to initiate the code span or bolded text!!! Under no circumstances are they to be literally included additionally alongside of the proper code span.**
    - Simply format the chips as a ` code_block ` but do not include additional backlinks.
- **Color will be provided based on the corresponding "Cluster" option in an associated select property, or will be provided specifically within the prompt context input.**
- Emojis: Use those in database titles or as visible text in links. No substitutions.
- Use <br> for compact line breaks.
- Structure exactly as depicted in the example below.


> [!tip] 💡
> **EXAMPLE **— Based on a Database Container with multiple data sources:
> ---
> **░░░░░░░░░░░░░░░░░░░░░░░░░░░░**
> 
> The `**CRM**` Database is where your essential contact details for your network are organized! For stakeholders & interaction pipelines that help move opportunities forward and track engagement history. A&Rs, management, music supervisors, sample license holders, venue contacts, etc.
> 
> ==` 🎹 \- 👥 \- 💝 \- 📢 \- 💰 \- 📤 \- 🏟️ \- 🤝 \- 🧵 \- 🧰 \- 🧑‍⚖️ \- 📚 \-**Contacts **\-☎️\-**Companies 🏢**\-**Correspondence 🛰️**\-**Fans 😍**\- 🔠 \- {emoji} `</span>
        3. separated by ・ with <br> between groups
    3. A line with bullet: ・**{N}** Data Sources + {M} link(s) where N is the count of Data Sources owned by that Database and M is the count of additional data sources (existing elsewhere) that are linked in that database.
    4. A subtle dotted separator line: ・・・・・・・・・・・・・・・
    5. A bolded inline list of key contained data sources, hyperlinked as `**<mention-database {emoji}/>**` items where available, inline code styled.
        4. No more than 3 data sources per line. If more, add a separating line break, then on the next line add the rest.
    6. A trailing reference link such as [**{system_page_url}**](%7Bsystem_page_url%7D) if applicable next to the closing colored divider line.
        5. e.g.
            1. [**← DASH**](/1f1dbb7d996f80b1b887fdfc7c1b2764)**  ****░░░░░░░░░░░░░░░░░░░░░░**
- Lint:
    - No trailing spaces after </span>
    - No empty URLs
    - All <span> closed; only supported colors

### Final guidance
- Lock glyph sequence in code span chips: space, emoji, space.
- **Do NOT include backtick ` or asterisk * literals in the text, they are only intended as a reference to initiate the code span or bolded text!!! Under no circumstances are they to be literally included additionally alongside of the proper code span.**
    - Simply format the chips as a ` code_block `
- Keep color–category mapping consistent based on Cluster selection property option or prompt context.
- Validate visually in Notion per Examples.

### Source-of-truth
- System page: houses databases and their emojis/URLs
- Emoji: Extract the displayed emoji for each database
- URL: Use database block’s URL
- Do not invent/substitute emojis; always mirror the system page.
- The “Dash” link targets the system’s parent/dashboard.

### Harvesting algorithm
5. Load system page URL
6. Scan for <database url="...">Display Name ⋄ EMOJI</database>
7. For each database:
    - db_url = url
    - display_name_with_emoji = inner text
    - emoji = last emoji glyph
    - display_name = text before trailing emoji/separator
8. Build: {name, emoji, url}
9. Dash link: parent dashboard, label “← DASH”


### Chip/layout constraints
- Chip: ==` {emoji} `==
- Link: harvested database URL
- Max 7 chips per row, wrap with <br>
- Prefer category color groups
- balance rows for no single orphan chips

### Rendering (final):
All formatting, colors, escaping, and syntax per above.
### Validation (must pass)
- Each chip’s emoji is in the harvested title
- Each chip’s URL is the harvested database’s
- No row with >7 chips
- All <span> closed, only supported colors
- Dash link goes to parent/dashboard

The agent will:
- Harvest database names/emojis/URLs from system_page_url
- Build chips from that info, using color as provided by the Cluster property or prompt input or default mapping
- Lay out with up to 7 per row
- Insert Dash link to dash_url
- Render using specified Notion-flavored markdown and spans


---
