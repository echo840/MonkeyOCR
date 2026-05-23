# Quick Start
## Locally Install
### 1. Install MonkeyOCR
See the [installation guide](https://github.com/Yuliang-Liu/MonkeyOCR/blob/main/docs/install_cuda_pp.md#install-with-cuda-support) to set up your environment.
### 2. Download Model Weights
Download our model from Huggingface.
```python
pip install huggingface_hub

python tools/download_model.py -n MonkeyOCR-pro-3B # or MonkeyOCR-pro-1.2B, MonkeyOCR
```
You can also download our model from ModelScope.

```python
pip install modelscope

python tools/download_model.py -t modelscope -n MonkeyOCR-pro-3B  # or MonkeyOCR-pro-1.2B, MonkeyOCR
```
### 3. Inference
You can parse a file or a directory containing PDFs or images using the following commands:
```bash
# Replace input_path with the path to a PDF or image or directory

# End-to-end parsing
python parse.py input_path

# Parse files in a dir with specific group page num
python parse.py input_path -g 20

# Single-task recognition (outputs markdown only)
python parse.py input_path -t text/formula/table

# Parse PDFs in input_path and split results by pages
python parse.py input_path -s

# Specify output directory and model config file
python parse.py input_path -o ./output -c config.yaml
```

MonkeyOCR mainly generates three types of output files:

1. **Processed Markdown File** (`your.md`): The final parsed document content in markdown format, containing text, formulas, tables, and other structured elements.
2. **Layout Results** (`your_layout.pdf`): The layout results drawed on origin PDF.
2. **Intermediate Block Results** (`your_middle.json`): A JSON file containing detailed information about all detected blocks, including:
   - Block coordinates and positions
   - Block content and type information
   - Relationship information between blocks

These files provide both the final formatted output and detailed intermediate results for further analysis or processing.

</details>

### 4. Gradio Demo
```bash
python demo/demo_gradio.py
```
Once the demo is running, you can access it at http://localhost:7860.
