# n8n MCP Server

[![smithery badge](https://smithery.ai/badge/@illuminaresolutions/n8n-mcp-server)](https://smithery.ai/server/@illuminaresolutions/n8n-mcp-server)

An MCP server that provides access to n8n workflows, executions, credentials, and more through the Model Context Protocol. This allows Large Language Models (LLMs) to interact with n8n instances in a secure and standardized way.

## Installation

### Installing via Smithery

To install n8n-mcp-server for Claude Desktop automatically via [Smithery](https://smithery.ai/server/@illuminaresolutions/n8n-mcp-server):

```bash
npx -y @smithery/cli install @illuminaresolutions/n8n-mcp-server --client claude
```

### Get your n8n API Key

1. Log into your n8n instance
2. Click your user icon in the bottom left
3. Go to Settings
4. Select API
5. Click "Create API Key"
6. Copy your API key (you won't be able to see it again)

### Install the MCP Server

#### Option 1: Install from npm (Recommended)

```bash
npm install -g @illuminaresolutions/n8n-mcp-server
```

#### Option 2: Install from Source

1. Clone the repository:
   ```bash
   git clone https://github.com/illuminaresolutions/n8n-mcp-server.git
   cd n8n-mcp-server
   ```

2. Install dependencies and build:
   ```bash
   npm install
   npm run build
   ```

3. Start the server in the background:
   ```bash
   nohup npm start > n8n-mcp.log 2>&1 &
   ```

   To stop the server:
   ```bash
   pkill -f "node build/index.js"
   ```

Note: When installing from npm, the server will be available as `n8n-mcp-server` in your PATH.

## Configuration

### Claude Desktop

1. Open your Claude Desktop configuration:
   ```
   ~/Library/Application Support/Claude/claude_desktop_config.json
   ```

2. Add the n8n configuration:
   ```json
   {
     "mcpServers": {
        "n8n": {
         "command": "n8n-mcp-server",
         "env": {
           "N8N_HOST": "https://your-n8n-instance.com",
           "N8N_API_KEY": "your-api-key-here"
         }
       }
     }
   }
   ```

### Cline (VS Code)

1. Install the server (follow Installation steps above)
2. Open VS Code
3. Open the Cline extension from the left sidebar
4. Click the 'MCP Servers' icon at the top of the pane
5. Scroll to bottom and click 'Configure MCP Servers'
6. Add to the opened settings file:
   ```json
   {
     "mcpServers": {
       "n8n": {
         "command": "n8n-mcp-server",
         "env": {
           "N8N_HOST": "https://your-n8n-instance.com",
           "N8N_API_KEY": "your-api-key-here"
         }
       }
     }
   }
   ```
7. Save the file
8. Ensure the MCP toggle is enabled (green) and the status indicator is green
9. Start using MCP commands in Cline

### Sage

Coming soon! The n8n MCP server will be available through:
- Smithery.ai marketplace
- Import from Claude Desktop

For now, please use Claude Desktop or Cline.

## Validation

After configuration:

1. Restart your LLM application
2. Ask: "List my n8n workflows"
3. You should see your workflows listed

If you get an error:
- Check that your n8n instance is running
- Verify your API key has correct permissions
- Ensure N8N_HOST has no trailing slash

## Features

### Core Features
- List and manage workflows
- View workflow details
- Execute workflows
- Manage credentials
- Handle tags and executions
- Generate security audits
- Manage workflow tags

### Enterprise Features
These features require an n8n Enterprise license:
- Project management
- Variable management
- Advanced user management

## Troubleshooting

### Common Issues

1. "Client not initialized"
   - Check N8N_HOST and N8N_API_KEY are set correctly
   - Ensure n8n instance is accessible
   - Verify API key permissions

2. "License required"
   - You're trying to use an Enterprise feature
   - Either upgrade to n8n Enterprise or use core features only

3. Connection Issues
   - Verify n8n instance is running
   - Check URL protocol (http/https)
   - Remove trailing slash from N8N_HOST

## Security Best Practices

1. API Key Management
   - Use minimal permissions necessary
   - Rotate keys regularly
   - Never commit keys to version control

2. Instance Access
   - Use HTTPS for production
   - Enable n8n authentication
   - Keep n8n updated

## Support

- [GitHub Issues](https://github.com/illuminaresolutions/n8n-mcp-server/issues)
- [n8n Documentation](https://docs.n8n.io)

## License

[MIT License](LICENSE)
