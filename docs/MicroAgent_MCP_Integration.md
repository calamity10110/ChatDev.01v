# MicroAgent and MCP Server Integration Guide

## Overview
This document describes how to integrate MicroAgent with MCP Server in ChatDev environments.

## Prerequisites
- ChatDev v2.1+
- MCP Server v1.3+
- MicroAgent SDK

## Configuration

### 1. MCP Server Setup
```bash
# Start MCP Server
mcp-server start --port 9090
```

### 2. MicroAgent Configuration
Add to `ChatChainConfig.json`:
```json
{
  "microagent": {
    "mcp_endpoint": "http://localhost:9090",
    "timeout": 30,
    "retries": 3
  }
}
```

## Usage Examples

### Basic Integration
```python
from microagent import MicroAgent

agent = MicroAgent(
    mcp_endpoint=config['microagent']['mcp_endpoint'],
    timeout=config['microagent']['timeout']
)
```

### Error Handling
```python
try:
    response = agent.execute_task(task_prompt)
except MCPTimeoutError:
    # Handle timeout
except MCPConnectionError:
    # Handle connection issues
```

## Troubleshooting
- **Connection Issues**: Verify MCP Server is running
- **Timeout Errors**: Increase timeout in configuration
- **Authentication**: Ensure proper API keys are set

## API Reference
See [MicroAgent SDK Docs](https://microagent.dev/docs) for full API details.