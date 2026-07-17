# Claude Code Startup Instructions

This file contains startup instructions that Claude should follow at the beginning of each session.

## PAL MCP Server Setup

The PAL MCP server provides access to multiple AI models (GPT-5.6-Sol, Gemini-3.5-Flash, etc.) for multi-model consultation, consensus building, and advanced workflows.

### Check PAL MCP Availability

At session start, verify PAL MCP tools are available by checking if these tools exist:
- `mcp__pal__chat`
- `mcp__pal__consensus`

If these tools are NOT available, inform the user:

```
PAL MCP server is not connected. To enable multi-model consultation:

1. Run the PAL MCP setup script:
   cd /home/espenale/src/pal-mcp-server && ./run-server.sh

2. The script will configure Claude Code's MCP settings automatically.

3. Restart Claude Code to connect to PAL MCP.
```

### Manual PAL MCP Configuration

If automatic setup fails, add this to Claude Code's MCP configuration:

```json
{
  "mcpServers": {
    "pal": {
      "command": "/home/espenale/src/pal-mcp-server/.pal_venv/bin/python",
      "args": ["/home/espenale/src/pal-mcp-server/server.py"]
    }
  }
}
```

### PAL MCP Tools Available

Once connected, these tools become available:
- `mcp__pal__chat` - Chat with any AI model (GPT-5.6-Sol, Gemini-3.5-Flash, etc.)
- `mcp__pal__consensus` - Get consensus from multiple models
- `mcp__pal__codereview` - Multi-model code review
- `mcp__pal__debug` - Systematic debugging with AI assistance
- `mcp__pal__analyze` - Deep code analysis
- `mcp__pal__planner` - Planning and architecture design
- `mcp__pal__thinkdeep` - Extended reasoning and analysis
- `mcp__pal__precommit` - Pre-commit validation
- `mcp__pal__clink` - CLI-to-CLI bridge for spawning subagents

### Consult Oracles Skill

The `/consult-oracles` skill uses PAL MCP to consult GPT-5.6-Sol and Gemini-3.5-Flash in PARALLEL for unbiased expert analysis. Use it for:
- Complex architectural decisions
- Debugging difficult problems
- Performance optimization strategies
- Research pre-studies for state-of-the-art algorithms
- When the user says "consult oracles", "ask the experts", or wants a second opinion

## Environment Activation

For Python projects, remember to activate the appropriate mamba environment:

```bash
eval "$(mamba shell hook --shell bash)" && mamba activate <env_name>
```

Available environments:
- `sam3d-golf` - SAM-3D golf swing analysis
- `sam3d-objects-cu128` - SAM-3D object detection (CUDA 12.8)
- `kosmos` - Kosmos multimodal models
- `mmpose` - MMPose pose estimation
- `pal` - PAL MCP server development

## Project Locations

| Project | Path | Description |
|---------|------|-------------|
| PAL MCP Server | `/home/espenale/src/pal-mcp-server` | Multi-model AI orchestration |
| SAM-3D Golf | `/home/espenale/src/sam-3d-golf` | Golf swing 3D mesh reconstruction |
| SAM-3D Objects | `/home/espenale/src/sam-3d-objects` | 3D object detection |
| Kosmos | `/home/espenale/src/Kosmos` | Multimodal AI experiments |
| ML Models | `/home/espenale/src/ml-models` | Machine learning models |
| ML Pipelines | `/home/espenale/src/ml-pipelines` | ML pipeline infrastructure |

