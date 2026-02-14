# AI Email Assistant - Cloudflare Tunnel Setup

This guide explains how to set up a Cloudflare tunnel to connect the chat interface to your local AI agent.

## What is a Cloudflare Tunnel?

Cloudflare Tunnels (formerly Cloudflare Tunnel) allow you to expose a local web server to the internet without opening ports on your router. It provides:
- **Public URL**: A secure HTTPS URL to access your local server
- **No port forwarding**: No need to configure router or firewall
- **Automatic SSL**: HTTPS provided by Cloudflare

## Architecture

```
┌─────────────────┐
│   Browser     │  https://your-tunnel.trycloudflare.com
└────────┬────────┘
         │
         │ HTTPS
         ▼
┌─────────────────┐
│   Cloudflare    │  Cloudflare Tunnel
│   Tunnel       │
└────────┬────────┘
         │
         │ Local Network
         ▼
┌─────────────────┐
│   Local Server  │  http://localhost:3000
│   (Node.js)    │  └──> AI Agent (Email Processing)
└─────────────────┘
```

## Setup Instructions

### 1. Install Cloudflare Tunnel

**macOS:**
```bash
brew install cloudflared
```

**Linux:**
```bash
# Download from https://developers.cloudflare.com/cloudflare-one/connections
wget https://github.com/cloudflare/cloudflared/releases/latest/download/cloudflared-linux-amd64
chmod +x cloudflared-linux-amd64
sudo mv cloudflared-linux-amd64 /usr/local/bin/cloudflared
```

**Windows:**
```powershell
# Download from https://developers.cloudflare.com/cloudflare-one/connections
# Run the installer
```

### 2. Create a Simple Local Server

Create a file `server.js`:

```javascript
const http = require('http');
const { exec } = require('child_process');

const port = 3000;

const server = http.createServer((req, res) => {
    // Enable CORS for chat interface
    res.setHeader('Access-Control-Allow-Origin', '*');
    res.setHeader('Access-Control-Allow-Methods', 'GET, POST, OPTIONS');
    res.setHeader('Access-Control-Allow-Headers', 'Content-Type');

    if (req.method === 'OPTIONS') {
        res.writeHead(200);
        res.end();
        return;
    }

    let body = '';
    req.on('data', chunk => { body += chunk.toString(); });
    req.on('end', () => {
        try {
            const data = JSON.parse(body);
            
            if (req.url === '/chat') {
                // Process chat message through AI agent
                console.log('Chat message:', data.message);
                
                // Here you would integrate with your AI agent
                // For now, simulate response
                const response = {
                    type: 'agent',
                    message: `AI Agent received: "${data.message}"`,
                    timestamp: new Date().toISOString()
                };
                
                res.writeHead(200, { 'Content-Type': 'application/json' });
                res.end(JSON.stringify(response));
            }
        } catch (error) {
            console.error('Error:', error);
            res.writeHead(400, { 'Content-Type': 'application/json' });
            res.end(JSON.stringify({ error: 'Invalid request' }));
        }
    });
});

server.listen(port, () => {
    console.log(`Server running on http://localhost:${port}`);
});
```

### 3. Start the Local Server

```bash
node server.js
```

You should see:
```
Server running on http://localhost:3000
```

### 4. Create Cloudflare Tunnel

```bash
cloudflared tunnel --url http://localhost:3000
```

You'll get output like:
```
2025-02-13T19:00:00Z INFO Your quick Tunnel has been created and is available at: https://your-tunnel.trycloudflare.com
```

Copy the URL (e.g., `https://your-tunnel.trycloudflare.com`).

### 5. Configure Chat Interface

1. Go to the Chat page
2. Click ⚙️ Settings
3. Select "Cloudflare Tunnel (Advanced)"
4. Paste the tunnel URL
5. Click "Save & Connect"

The chat will now connect to your local AI agent via the Cloudflare tunnel.

## Connecting Chat to AI Agent

To actually connect the chat to your AI agent, you need to:

### Option 1: WebSocket Integration

Update `server.js` to support WebSocket:

```javascript
const WebSocket = require('ws');
const wss = new WebSocket.Server({ port: 3001 });

wss.on('connection', ws => {
    ws.on('message', message => {
        const data = JSON.parse(message);
        
        // Process through AI agent
        // Send email to agent
        // Wait for agent response
        // Send response back to chat
        
        ws.send(JSON.stringify({
            type: 'agent',
            message: agentResponse
        }));
    });
});
```

### Option 2: Email Bridge (Simpler)

The current chat interface uses an email bridge by default:
- Chat messages -> Email to agent
- Agent responses -> Displayed in chat

This requires no local server setup and works with the existing email agent.

## Security Notes

1. **Authentication**: Add authentication to your local server
2. **Rate Limiting**: Implement rate limiting to prevent abuse
3. **Input Validation**: Validate all incoming messages
4. **HTTPS**: Cloudflare provides HTTPS automatically

## Troubleshooting

**Tunnel not working:**
- Check if local server is running
- Verify tunnel URL is correct
- Check Cloudflare dashboard for tunnel status

**Chat not connecting:**
- Verify tunnel URL is correct
- Check browser console for errors
- Ensure CORS headers are set on local server

**Slow responses:**
- Check AI agent processing time
- Consider adding response caching

## Next Steps

1. Set up local server with Cloudflare tunnel
2. Test connection with Chat page
3. Integrate AI agent (email processing)
4. Deploy to production

For more information:
- Cloudflare Tunnels: https://developers.cloudflare.com/cloudflare-one/connections/connect-apps/
- Chat interface: /chat.html
