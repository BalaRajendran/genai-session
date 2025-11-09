# Setup Guide for LangChain Design Patterns Workshop

This guide will help you set up your local environment to run the LangChain design patterns notebook.

## Prerequisites

- Python 3.10 or higher
- Visual Studio Code (VSCode)
- An OpenAI API key (required for running the examples)

## Step 1: Install uv

`uv` is a fast Python package installer and resolver. Install it using one of the methods below:

### macOS/Linux
```bash
curl -LsSf https://astral.sh/uv/install.sh | sh
```

### Windows (PowerShell)
```powershell
powershell -c "irm https://astral.sh/uv/install.ps1 | iex"
```

### Alternative: Using pip
```bash
pip install uv
```

After installation, verify it works:
```bash
uv --version
```

## Step 2: Clone or Download the Project

If you received this as a ZIP file, extract it. Otherwise, clone from the repository.

Navigate to the notebook directory:
```bash
cd notebook
```

## Step 3: Create a Virtual Environment

Using `uv`, create a virtual environment named `genai-session`:

```bash
uv venv genai-session
```

This creates a `genai-session` directory in your current folder.

## Step 4: Activate the Virtual Environment

### macOS/Linux
```bash
source genai-session/bin/activate
```

### Windows (Command Prompt)
```cmd
genai-session\Scripts\activate.bat
```

### Windows (PowerShell)
```powershell
genai-session\Scripts\Activate.ps1
```

You should see `(genai-session)` in your terminal prompt.

## Step 5: Install Dependencies

Install all required packages from the requirements file:

```bash
uv pip install -r requirements.txt
```

This will install:
- `langchain` - Core LangChain framework
- `langchain-openai` - OpenAI integration
- `langchain-google-genai` - Google AI integration
- `langchain-chroma` - Vector database for RAG
- `langchain-community` - Community tools (PDF loader)
- `langgraph` - Graph-based workflows
- `langfuse` - LLM observability
- `python-dotenv` - Environment variable management
- `pypdf` - PDF parsing
- `pydantic` - Data validation
- `typing-extensions` - Type hints

## Step 6: Install Jupyter Extension in VSCode

1. Open Visual Studio Code
2. Go to Extensions (or press `Ctrl+Shift+X` / `Cmd+Shift+X`)
3. Search for "Jupyter"
4. Install the **Jupyter** extension by Microsoft
5. Restart VSCode if prompted

## Step 7: Configure API Keys

1. Copy the example environment file:
   ```bash
   cp .env.example .env
   ```

2. Edit the `.env` file and add your API keys:
   ```
   OPENAI_API_KEY="your-openai-api-key-here"
   ```

### How to get an OpenAI API Key:
1. Go to [https://platform.openai.com](https://platform.openai.com)
2. Sign up or log in
3. Navigate to API Keys section
4. Create a new API key
5. Copy and paste it into your `.env` file

**Important:** Never commit your `.env` file to version control!

## Step 8: Verify PDF Resources

Make sure the `pdf` directory contains the required PDF file:
```bash
ls pdf/
```

You should see `pondicherry.pdf` or similar files used in the examples.

## Step 9: Open Notebook in VSCode

1. Open VSCode in the notebook directory:
   ```bash
   code .
   ```

2. Open `langchain_design_patterns.ipynb` file

3. VSCode will prompt you to select a Python kernel
   - Click on "Select Kernel" in the top right
   - Choose "Python Environments"
   - Select the `genai-session` virtual environment you created

4. You can now run the cells using the "Run" button next to each cell or press `Shift + Enter`

## Troubleshooting

### Issue: `ModuleNotFoundError`
- Make sure your virtual environment is activated
- Verify VSCode is using the correct Python kernel (check top-right corner)
- Reinstall dependencies: `uv pip install -r requirements.txt`

### Issue: API Key Error
- Check that your `.env` file exists in the `notebook` directory
- Verify your API key is correct (no extra spaces)
- Make sure you have credits/access in your OpenAI account

### Issue: ChromaDB errors
- The first time you run RAG examples, ChromaDB will create a `chroma_db` directory
- If you get errors, try deleting this directory and running again

### Issue: PDF Loading fails
- Ensure the PDF file exists in the `pdf` directory
- Check the file path in the notebook matches your actual file name

### Issue: uv command not found
- Restart your terminal after installing uv
- Or manually add uv to your PATH

### Issue: VSCode doesn't show the kernel
- Make sure the Jupyter extension is installed
- Try reloading VSCode window: `Cmd+Shift+P` → "Reload Window"
- Check that your virtual environment is activated in the terminal

## Understanding the Examples

The notebook covers:

1. **Basic Translation Pipeline** - Simple LangChain chain with prompts
2. **Zero-Shot Prompting** - Task execution without examples
3. **One-Shot Prompting** - Using one example to guide the model
4. **Few-Shot Prompting** - Multiple examples for better accuracy
5. **Chain of Thought** - Step-by-step reasoning
6. **RAG (Retrieval-Augmented Generation)** - Using external documents

## Additional Resources

- [LangChain Documentation](https://python.langchain.com/)
- [OpenAI API Documentation](https://platform.openai.com/docs)
- [uv Documentation](https://github.com/astral-sh/uv)
- [VSCode Jupyter Extension](https://marketplace.visualstudio.com/items?itemName=ms-toolsai.jupyter)

## Need Help?

If you encounter any issues during setup, please:
1. Check the error message carefully
2. Ensure all steps were followed in order
3. Verify your Python version: `python --version`
4. Contact your instructor with specific error messages

---

Happy Learning!
