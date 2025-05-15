[![MseeP.ai Security Assessment Badge](https://mseep.net/pr/cognitive-stack-hermes-search-mcp-badge.png)](https://mseep.ai/app/cognitive-stack-hermes-search-mcp)

# Hermes Search MCP Server 🔍

> 🔌 **Compatible with Cline, Cursor, Claude Desktop, and any other MCP Clients!**

The Model Context Protocol (MCP) is an open standard that enables AI systems to interact seamlessly with various data sources and tools, facilitating secure, two-way connections.

The Hermes Search MCP server provides:

* Full-text and semantic search capabilities over structured/unstructured data
* Document indexing and management in Azure Cognitive Search
* Efficient search operations with customizable parameters
* Type-safe operations with TypeScript

## Prerequisites 🔧

Before you begin, ensure you have:

* Azure Cognitive Search service and credentials
* Claude Desktop or Cursor
* Node.js (v20 or higher)
* Git installed (only needed if using Git installation method)

## Hermes Search MCP server installation ⚡

### Running with NPX

```bash
npx -y hermes-search-mcp@latest
```

### Installing via Smithery

To install Hermes Search MCP Server for Claude Desktop automatically via Smithery:

```bash
npx -y @smithery/cli install @hermes-search/mcp --client claude
```

## Configuring MCP Clients ⚙️

### Configuring Cline 🤖

The easiest way to set up the Hermes Search MCP server in Cline is through the marketplace with a single click:

1. Open Cline in VS Code
2. Click on the Cline icon in the sidebar
3. Navigate to the "MCP Servers" tab (4 squares)
4. Search "Hermes Search" and click "install"
5. When prompted, enter your Azure Cognitive Search credentials

Alternatively, you can manually set up the Hermes Search MCP server in Cline:

1. Open the Cline MCP settings file:
```bash
# For macOS:
code ~/Library/Application\ Support/Code/User/globalStorage/saoudrizwan.claude-dev/settings/cline_mcp_settings.json

# For Windows:
code %APPDATA%\Code\User\globalStorage\saoudrizwan.claude-dev\settings\cline_mcp_settings.json
```

2. Add the Hermes Search server configuration to the file:
```json
{
  "mcpServers": {
    "hermes-search-mcp": {
      "command": "npx",
      "args": ["-y", "hermes-search-mcp@latest"],
      "env": {
        "AZURE_SEARCH_ENDPOINT": "your-search-endpoint",
        "AZURE_SEARCH_API_KEY": "your-api-key",
        "AZURE_SEARCH_INDEX_NAME": "your-index-name"
      },
      "disabled": false,
      "autoApprove": []
    }
  }
}
```

3. Save the file and restart Cline if it's already running.

### Configuring Cursor 🖥️

> **Note**: Requires Cursor version 0.45.6 or higher

To set up the Hermes Search MCP server in Cursor:

1. Open Cursor Settings
2. Navigate to Features > MCP Servers
3. Click on the "+ Add New MCP Server" button
4. Fill out the following information:
   * **Name**: Enter a nickname for the server (e.g., "hermes-search-mcp")
   * **Type**: Select "command" as the type
   * **Command**: Enter the command to run the server:
   ```bash
   env AZURE_SEARCH_ENDPOINT=your-search-endpoint AZURE_SEARCH_API_KEY=your-api-key AZURE_SEARCH_INDEX_NAME=your-index-name npx -y hermes-search-mcp@latest
   ```
   > **Important**: Replace the environment variables with your Azure Cognitive Search credentials

### Configuring the Claude Desktop app 🖥️

#### For macOS:
```bash
# Create the config file if it doesn't exist
touch "$HOME/Library/Application Support/Claude/claude_desktop_config.json"

# Opens the config file in TextEdit
open -e "$HOME/Library/Application Support/Claude/claude_desktop_config.json"
```

#### For Windows:
```bash
code %APPDATA%\Claude\claude_desktop_config.json
```

#### Add the Hermes Search server configuration:
```json
{
  "mcpServers": {
    "hermes-search-mcp": {
      "command": "npx",
      "args": ["-y", "hermes-search-mcp@latest"],
      "env": {
        "AZURE_SEARCH_ENDPOINT": "your-search-endpoint",
        "AZURE_SEARCH_API_KEY": "your-api-key",
        "AZURE_SEARCH_INDEX_NAME": "your-index-name"
      }
    }
  }
}
```

## Usage in Claude Desktop App 🎯

Once the installation is complete, and the Claude desktop app is configured, you must completely close and re-open the Claude desktop app to see the hermes-search-mcp server. You should see a search icon in the bottom left of the app, indicating available MCP tools.

### Hermes Search Examples

1. **Search Documents**:
```
Search for documents containing "machine learning" in the Azure Cognitive Search index, returning the top 10 results.
```

2. **Index Content**:
```
Index the following documents into Azure Cognitive Search: [{"id": "1", "title": "AI Overview", "content": "Artificial Intelligence is..."}]
```

3. **Delete Index**:
```
Delete the current Azure Cognitive Search index.
```

## Troubleshooting 🛠️

### Common Issues

1. **Server Not Found**
   * Verify the npm installation by running `npm --version`
   * Check Claude Desktop configuration syntax
   * Ensure Node.js is properly installed by running `node --version`

2. **Azure Search Credentials Issues**
   * Confirm your Azure Cognitive Search credentials are valid
   * Check the credentials are correctly set in the config
   * Verify no spaces or quotes around the credentials

3. **Index Access Issues**
   * Verify the index exists in your Azure Cognitive Search service
   * Check the index permissions
   * Ensure the API key has appropriate access rights

## Acknowledgments ✨

* Model Context Protocol for the MCP specification
* Anthropic for Claude Desktop
* Microsoft Azure for Cognitive Search 