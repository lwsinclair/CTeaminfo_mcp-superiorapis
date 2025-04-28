[![MseeP Badge](https://mseep.net/pr/mcp-mirror-cteaminfo-mcp-superiorapis-badge.jpg)](https://mseep.ai/app/mcp-mirror-cteaminfo-mcp-superiorapis)

# SuperiorAPIs MCP Server Tool

## 📖 Description
This project is a Python-based **MCP Server** that dynamically fetches plugin definitions from **SuperiorAPIs** and auto-generates MCP tool functions based on OpenAPI schemas.

The server will:
- Fetch plugin metadata
- Parse the schema
- Generate tool functions dynamically
- Run the MCP server

## 🚀 Features
- Dynamic plugin loading from **SuperiorAPIs**
- Auto-generation of `pydantic` models and async functions
- Asynchronous API execution using `aiohttp`
- Runtime MCP tool registration
- Supports environment-based configuration
- Ready for UVX platform deployment

## 📂 Project Structure
```
.
├── main.py                 # MCP server core logic
├── requirements.txt        # Python dependency list
├── setup.py                # Packaging setup
├── Dockerfile              # (Optional) Docker container build file
└── README.md               # Project documentation
```

## ⚙️ Installation
Clone the project and install the dependencies:
```bash
git clone https://your-repo-url.git
cd your-repo
pip install -r requirements.txt
```

## 🌍 Environment Variables
Before running, set the following environment variables:

**Linux/macOS**
```bash
export TOKEN=your_token_here
export APPLICATION_ID=your_application_id_here
```

**Windows CMD**
```cmd
set TOKEN=your_token_here
set APPLICATION_ID=your_application_id_here
```

## 🖥️ Usage
Run the MCP server:
```bash
python main.py
```

The server will:
1. Fetch plugin data from SuperiorAPIs
2. Dynamically generate MCP tool functions
3. Register the tools
4. Start the MCP server

## 🔗 API Endpoint
Plugin definitions are fetched from:
```
https://superiorapis-creator.cteam.com.tw/manager/module/plugins/list_v2
```
Authorization is required via the `token` header.

## 🧠 Example Generated Tool Function
```python
@mcp.tool()
async def post_example_tool(param1: Optional[str] = None, param2: Optional[int] = None) -> str:
    """
    Tool description | API summary.

    # Args:
        param1 (string, optional): Description of param1.
        param2 (integer, optional): Description of param2.

    # Returns:
        200 (object): API response.
    """
```

## 📜 Requirements
```
aiohttp>=3.8.6
pydantic>=2.5.3
mcp-sdk>=0.1.0
```

## ❗ Error Handling
If the API call fails or returns `status: 0`, the program will exit with:
```
❌ Error: API returned no data or status is 0. Please check if the API is working properly.
```

## 📦 Packaging (Optional)
Build the package:
```bash
python setup.py sdist bdist_wheel
```

Install the package:
```bash
pip install dist/mcp-superiorapis-1.0.0-py3-none-any.whl
```

Run using Docker (if needed):
```bash
docker build -t superiorapis-mcp .
docker run -e TOKEN=your_token -e APPLICATION_ID=your_app_id superiorapis-mcp
```

## 📄 License
MIT License (or your custom license)

## 👨‍💻 Author
Your Name / Your Company  
Contact: your_email@example.com