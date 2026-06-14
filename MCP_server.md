What is MCP?

Model Context Protocol (MCP) is an open standard introduced by Anthropic that allows AI models (Claude, ChatGPT, AI agents, IDE assistants, etc.) to securely connect with external tools, databases, APIs, files, and services.

Think of MCP as:

"USB-C for AI applications"

Just as USB allows different devices to communicate through a common standard, MCP allows AI models to communicate with different tools through a common protocol.

Why Was MCP Created?

Before MCP:

AI Model → Custom Integration → Database
AI Model → Custom Integration → Slack
AI Model → Custom Integration → GitHub
AI Model → Custom Integration → AWS

Every integration required separate code.

After MCP:

AI Model
     │
     ▼
MCP Client
     │
     ▼
MCP Server
     │
 ┌───┼────┬────┐
 ▼   ▼    ▼    ▼
GitHub Slack AWS Database

Build once.

Connect everywhere.

MCP Architecture

There are three major components:

6
1. MCP Host

The application containing the AI model.

Examples:

Claude Desktop
Cursor
Windsurf
VS Code AI Extensions
AI Agents

Example:

Claude Desktop

Claude is the Host.

2. MCP Client

The component inside the host that communicates with MCP servers.

Responsibilities:

Sends requests
Receives responses
Maintains connections
Manages permissions

Example:

Claude Desktop
      ↓
MCP Client
3. MCP Server

The most important component.

An MCP Server exposes:

Tools
Resources
Prompts

to AI models.

Think:

MCP Server = Bridge

between AI and real-world systems.

What Exactly Is an MCP Server?

An MCP Server is a program that:

Receives requests from AI
Executes actions
Returns results

Example:

User:
List all EC2 instances

AI:
Calls AWS MCP Server

AWS MCP Server:
Fetches EC2 instances

AI:
Returns answer
MCP Server Components

An MCP Server usually contains:

Server
 ├─ Tools
 ├─ Resources
 ├─ Prompts
 └─ Transport Layer

Let's understand each.

1. Tools

Tools perform actions.

Think:

Function Calling

Example:

@mcp.tool()
def add(a: int, b: int):
    return a + b

AI can invoke:

{
  "tool": "add",
  "arguments": {
    "a": 10,
    "b": 20
  }
}

Output:

30
Real World Tool Examples
AWS Tool
@mcp.tool()
def list_ec2_instances():
    pass
GitHub Tool
@mcp.tool()
def create_pull_request():
    pass
Linux Tool
@mcp.tool()
def disk_usage():
    pass
2. Resources

Resources provide data.

Read-only information.

Examples:

File
Document
Database Row
Log File
Configuration
Static Resource
@mcp.resource("docs://intro")
def intro():
    return "Welcome"

Always returns same content.

Dynamic (Templated) Resource
@mcp.resource("docs://{file}")
def get_doc(file):
    pass

Requests:

docs://report.pdf
docs://notes.txt
docs://readme.md

This is why the answer to your MCP quiz was:

✅ Templated Resource with Parameters

Resource Example
logs://app.log

AI requests log.

Server returns content.

AI analyzes it.

3. Prompts

Reusable prompt templates.

Example:

@mcp.prompt()
def summarize(text):
    return f"Summarize:\n{text}"

AI can reuse prompt logic.

MCP Communication Flow

Example:

User asks:

Show disk usage

Flow:

User
 ↓
Claude
 ↓
MCP Client
 ↓
Linux MCP Server
 ↓
disk_usage Tool
 ↓
Output
 ↓
Claude
 ↓
User
MCP Transport Layer

Transport is how client and server communicate.

Common transports:

STDIO

Most popular.

Client <-> stdin/stdout <-> Server

Used by:

Claude Desktop
Cursor
VS Code

Example:

python server.py
HTTP
Client
   ↓
HTTP
   ↓
Server

Good for cloud deployments.

SSE

Server Sent Events.

Used for streaming responses.

MCP Server Lifecycle
Step 1

Server Starts

mcp.run()
Step 2

Registers:

Tools
Resources
Prompts
Step 3

Waits for requests

Step 4

Executes requested operation

Step 5

Returns result

Basic MCP Server Example
from mcp.server.fastmcp import FastMCP

mcp = FastMCP("Calculator")

Tool:

@mcp.tool()
def add(a:int,b:int):
    return a+b

Resource:

@mcp.resource("docs://guide")
def guide():
    return "MCP Guide"

Run:

mcp.run()
Popular MCP Servers
GitHub MCP Server

Provides:

Repositories
Issues
Pull Requests

AI can:

Create PRs
Review code
Open issues
Slack MCP Server

Provides:

Messages
Channels

AI can:

Send messages
Read conversations
Google Drive MCP Server

Provides:

Documents
Sheets

AI can search and summarize files.

AWS MCP Server

Provides:

EC2
S3
ECS
CloudWatch

Useful for DevOps Engineers.

Filesystem MCP Server

Provides:

Read files
Write files
Search files
MCP for DevOps

Since you're pursuing DevOps, MCP is especially powerful.

Imagine:

Claude
  ↓
AWS MCP
  ↓
Terraform MCP
  ↓
Kubernetes MCP
  ↓
GitHub MCP

You can ask:

"Deploy this application to EKS."

AI could:

Create Terraform
Provision infrastructure
Build Docker image
Push to ECR
Deploy to EKS
Verify deployment

through MCP servers.

MCP vs API
Feature	API	MCP
Standardized	❌	✅
AI Native	❌	✅
Tool Discovery	❌	✅
Resource Discovery	❌	✅
Prompt Sharing	❌	✅
Agent Friendly	❌	✅
MCP vs Function Calling
Feature	Function Calling	MCP
Single App	✅	❌
Cross Application	❌	✅
Resources	❌	✅
Prompts	❌	✅
Tool Registry	❌	✅
Important Interview Questions
What is MCP?

A protocol that enables AI models to securely connect and interact with external tools, resources, and services through a standardized interface.

What are the core components of MCP?
Host
Client
Server
What does an MCP Server expose?
Tools
Resources
Prompts
Difference between Tool and Resource?
Tool → Performs an action.
Resource → Provides data.
What is a templated resource?

A resource with parameters in its URI that can dynamically return different content based on the parameter value.

Example:

docs://{filename}
Most common transport?

STDIO.

Why is MCP important?

It allows AI systems to access external capabilities through a common standard instead of requiring custom integrations for every service.
