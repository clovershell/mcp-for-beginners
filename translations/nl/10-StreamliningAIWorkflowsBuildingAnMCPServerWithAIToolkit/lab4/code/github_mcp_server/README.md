<!--
CO_OP_TRANSLATOR_METADATA:
{
  "original_hash": "a3f252a62f059360855de5331a575898",
  "translation_date": "2025-07-14T09:00:00+00:00",
  "source_file": "10-StreamliningAIWorkflowsBuildingAnMCPServerWithAIToolkit/lab4/code/github_mcp_server/README.md",
  "language_code": "nl"
}
-->
# Weather MCP Server

Dit is een voorbeeld van een MCP Server in Python die weerhulpmiddelen implementeert met gesimuleerde reacties. Het kan worden gebruikt als basis voor je eigen MCP Server. Het bevat de volgende functies:

- **Weather Tool**: Een tool die gesimuleerde weersinformatie geeft op basis van de opgegeven locatie.
- **Git Clone Tool**: Een tool die een git-repository kloont naar een opgegeven map.
- **VS Code Open Tool**: Een tool die een map opent in VS Code of VS Code Insiders.
- **Connect to Agent Builder**: Een functie waarmee je de MCP-server kunt verbinden met de Agent Builder voor testen en debuggen.
- **Debug in [MCP Inspector](https://github.com/modelcontextprotocol/inspector)**: Een functie waarmee je de MCP Server kunt debuggen met behulp van de MCP Inspector.

## Aan de slag met de Weather MCP Server template

> **Vereisten**
>
> Om de MCP Server op je lokale ontwikkelmachine te draaien, heb je het volgende nodig:
>
> - [Python](https://www.python.org/)
> - [Git](https://git-scm.com/) (vereist voor git_clone_repo tool)
> - [VS Code](https://code.visualstudio.com/) of [VS Code Insiders](https://code.visualstudio.com/insiders/) (vereist voor open_in_vscode tool)
> - (*Optioneel - als je uv prefereert*) [uv](https://github.com/astral-sh/uv)
> - [Python Debugger Extension](https://marketplace.visualstudio.com/items?itemName=ms-python.debugpy)

## Omgeving voorbereiden

Er zijn twee manieren om de omgeving voor dit project op te zetten. Je kunt er één kiezen op basis van je voorkeur.

> Opmerking: Herlaad VSCode of de terminal om zeker te zijn dat de python van de virtuele omgeving wordt gebruikt nadat je de virtuele omgeving hebt aangemaakt.

| Aanpak | Stappen |
| ------- | ------- |
| Met `uv` | 1. Maak virtuele omgeving aan: `uv venv` <br>2. Voer VSCode-commando "***Python: Select Interpreter***" uit en selecteer de python van de aangemaakte virtuele omgeving <br>3. Installeer dependencies (inclusief dev dependencies): `uv pip install -r pyproject.toml --extra dev` |
| Met `pip` | 1. Maak virtuele omgeving aan: `python -m venv .venv` <br>2. Voer VSCode-commando "***Python: Select Interpreter***" uit en selecteer de python van de aangemaakte virtuele omgeving<br>3. Installeer dependencies (inclusief dev dependencies): `pip install -e .[dev]` |

Na het opzetten van de omgeving kun je de server lokaal draaien via Agent Builder als MCP Client om te beginnen:
1. Open het Debug-paneel in VS Code. Selecteer `Debug in Agent Builder` of druk op `F5` om het debuggen van de MCP server te starten.
2. Gebruik AI Toolkit Agent Builder om de server te testen met [deze prompt](../../../../../../../../../../open_prompt_builder). De server wordt automatisch verbonden met de Agent Builder.
3. Klik op `Run` om de server met de prompt te testen.

**Gefeliciteerd**! Je hebt de Weather MCP Server succesvol lokaal draaien via Agent Builder als MCP Client.
![DebugMCP](https://raw.githubusercontent.com/microsoft/windows-ai-studio-templates/refs/heads/dev/mcpServers/mcp_debug.gif)

## Wat zit er in de template

| Map / Bestand | Inhoud                                      |
| ------------- | ------------------------------------------- |
| `.vscode`     | VSCode-bestanden voor debuggen              |
| `.aitk`       | Configuraties voor AI Toolkit                |
| `src`         | De broncode voor de weather mcp server      |

## Hoe de Weather MCP Server te debuggen

> Opmerkingen:
> - [MCP Inspector](https://github.com/modelcontextprotocol/inspector) is een visuele ontwikkelaarstool voor het testen en debuggen van MCP-servers.
> - Alle debug-modi ondersteunen breakpoints, dus je kunt breakpoints toevoegen in de tool-implementatiecode.

## Beschikbare Tools

### Weather Tool
De `get_weather` tool geeft gesimuleerde weersinformatie voor een opgegeven locatie.

| Parameter | Type | Beschrijving |
| --------- | ---- | ------------ |
| `location` | string | Locatie waarvoor het weer wordt opgevraagd (bijv. stadsnaam, staat of coördinaten) |

### Git Clone Tool
De `git_clone_repo` tool kloont een git-repository naar een opgegeven map.

| Parameter | Type | Beschrijving |
| --------- | ---- | ------------ |
| `repo_url` | string | URL van de git-repository die gekloond moet worden |
| `target_folder` | string | Pad naar de map waar de repository naartoe gekloond moet worden |

De tool retourneert een JSON-object met:
- `success`: Boolean die aangeeft of de operatie succesvol was
- `target_folder` of `error`: Het pad van de gekloonde repository of een foutmelding

### VS Code Open Tool
De `open_in_vscode` tool opent een map in de VS Code of VS Code Insiders applicatie.

| Parameter | Type | Beschrijving |
| --------- | ---- | ------------ |
| `folder_path` | string | Pad naar de map die geopend moet worden |
| `use_insiders` | boolean (optioneel) | Of VS Code Insiders gebruikt moet worden in plaats van de reguliere VS Code |

De tool retourneert een JSON-object met:
- `success`: Boolean die aangeeft of de operatie succesvol was
- `message` of `error`: Een bevestigingsbericht of een foutmelding

## Debug Mode | Beschrijving | Stappen om te debuggen |
| ---------- | ------------ | ---------------------- |
| Agent Builder | Debug de MCP server in de Agent Builder via AI Toolkit. | 1. Open het Debug-paneel in VS Code. Selecteer `Debug in Agent Builder` en druk op `F5` om het debuggen van de MCP server te starten.<br>2. Gebruik AI Toolkit Agent Builder om de server te testen met [deze prompt](../../../../../../../../../../open_prompt_builder). De server wordt automatisch verbonden met de Agent Builder.<br>3. Klik op `Run` om de server met de prompt te testen. |
| MCP Inspector | Debug de MCP server met behulp van de MCP Inspector. | 1. Installeer [Node.js](https://nodejs.org/)<br> 2. Zet Inspector op: `cd inspector` && `npm install` <br> 3. Open het Debug-paneel in VS Code. Selecteer `Debug SSE in Inspector (Edge)` of `Debug SSE in Inspector (Chrome)`. Druk op F5 om te starten met debuggen.<br> 4. Wanneer MCP Inspector in de browser opent, klik op de knop `Connect` om deze MCP server te verbinden.<br> 5. Daarna kun je `List Tools` uitvoeren, een tool selecteren, parameters invoeren en `Run Tool` gebruiken om je servercode te debuggen.<br> |

## Standaardpoorten en aanpassingen

| Debug Mode | Poorten | Definities | Aanpassingen | Opmerking |
| ---------- | ------- | ---------- | ------------ | --------- |
| Agent Builder | 3001 | [tasks.json](../../../../../../10-StreamliningAIWorkflowsBuildingAnMCPServerWithAIToolkit/lab4/code/github_mcp_server/.vscode/tasks.json) | Pas [launch.json](../../../../../../10-StreamliningAIWorkflowsBuildingAnMCPServerWithAIToolkit/lab4/code/github_mcp_server/.vscode/launch.json), [tasks.json](../../../../../../10-StreamliningAIWorkflowsBuildingAnMCPServerWithAIToolkit/lab4/code/github_mcp_server/.vscode/tasks.json), [\_\_init\_\_.py](../../../../../../10-StreamliningAIWorkflowsBuildingAnMCPServerWithAIToolkit/lab4/code/github_mcp_server/src/__init__.py), [mcp.json](../../../../../../10-StreamliningAIWorkflowsBuildingAnMCPServerWithAIToolkit/lab4/code/github_mcp_server/.aitk/mcp.json) aan om bovenstaande poorten te wijzigen. | N.v.t. |
| MCP Inspector | 3001 (Server); 5173 en 3000 (Inspector) | [tasks.json](../../../../../../10-StreamliningAIWorkflowsBuildingAnMCPServerWithAIToolkit/lab4/code/github_mcp_server/.vscode/tasks.json) | Pas [launch.json](../../../../../../10-StreamliningAIWorkflowsBuildingAnMCPServerWithAIToolkit/lab4/code/github_mcp_server/.vscode/launch.json), [tasks.json](../../../../../../10-StreamliningAIWorkflowsBuildingAnMCPServerWithAIToolkit/lab4/code/github_mcp_server/.vscode/tasks.json), [\_\_init\_\_.py](../../../../../../10-StreamliningAIWorkflowsBuildingAnMCPServerWithAIToolkit/lab4/code/github_mcp_server/src/__init__.py), [mcp.json](../../../../../../10-StreamliningAIWorkflowsBuildingAnMCPServerWithAIToolkit/lab4/code/github_mcp_server/.aitk/mcp.json) aan om bovenstaande poorten te wijzigen. | N.v.t. |

## Feedback

Als je feedback of suggesties hebt voor deze template, open dan een issue op de [AI Toolkit GitHub repository](https://github.com/microsoft/vscode-ai-toolkit/issues)

**Disclaimer**:  
Dit document is vertaald met behulp van de AI-vertalingsdienst [Co-op Translator](https://github.com/Azure/co-op-translator). Hoewel we streven naar nauwkeurigheid, dient u er rekening mee te houden dat geautomatiseerde vertalingen fouten of onnauwkeurigheden kunnen bevatten. Het originele document in de oorspronkelijke taal moet als de gezaghebbende bron worden beschouwd. Voor cruciale informatie wordt professionele menselijke vertaling aanbevolen. Wij zijn niet aansprakelijk voor eventuele misverstanden of verkeerde interpretaties die voortvloeien uit het gebruik van deze vertaling.