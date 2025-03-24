# DeepSeek AI Agent: Code Generation with Execution Feedback

## Overview
This project implements an AI-driven coding agent leveraging the DeepSeek R1 model. It generates, executes, and refines Python code based on natural language prompts, providing real-time execution feedback to iteratively improve accuracy and functionality.

## Key Features
- **Natural Language to Code:** Converts natural language prompts into Python code using DeepSeek's Large Language Model (LLM).
- **Execution Feedback Loop:** Automatically executes generated code, evaluates correctness based on defined test cases, and utilizes output feedback (including errors) to iteratively refine the code.
- **Automatic Format Enforcement:** Ensures generated code is properly formatted and enclosed within Python code blocks for seamless integration and execution.
- **Tool Integration:** Modular tool architecture allows for extensibility and incorporation of additional functionalities.

## Components
### 1. Code Generation
Generates Python code from natural language prompts using the DeepSeek LLM, ensuring responses contain valid Python code enclosed within triple backticks.

### 2. Code Execution
Executes generated Python code in an isolated environment, capturing and returning output or errors, essential for providing actionable feedback.

### 3. Testing Suite
Runs predefined tests on generated code, verifying correctness against expected outputs to guide iterative improvements.

### 4. Refinement Mechanism
Employs detailed feedback, including full execution outputs and formatting instructions, to prompt the LLM to generate refined and correctly formatted code.

## Setup Instructions
### Dependencies
Ensure the required dependencies are installed:
```bash
pip install torch transformers pyyaml
```

### Model Setup
Ensure the DeepSeek model path is correctly specified in the `model_name` variable:
```python
model_name = "/kaggle/input/deepseek-r1/transformers/deepseek-r1-distill-qwen-1.5b/2"
```

### Running the Agent
Execute the main script to interact with the agent:
```bash
python your_script_name.py
```

## Usage Example
```python
prompt_example = "Write a Python function named gcd that computes the greatest common divisor of two numbers."
final_code, final_output = agent.run(
    prompt=prompt_example,
    function_to_test="gcd",
    test_args=[48, 18],
    expected_output="6"
)
print("Final Generated Code:\n", final_code)
print("Execution Output:\n", final_output)
```

## YAML Prompt Templates (Optional)
If using YAML prompt templates (`prompts.yaml`), structure them clearly to define custom prompts and instructions. Example structure:
```yaml
code_generation:
  system: "You are a coding assistant. Generate valid Python code."
  user_template: "Write a Python function named {function_name} that {description}."
```

## Limitations & Future Work
- Current execution uses basic isolation; enhanced sandboxing for secure execution is recommended for future implementations.
- Extensible tool architecture is in place; future integrations might include secure execution environments, richer test reporting, and additional language support.

## Contributions
Contributions to extend functionality, improve execution safety, and enhance tool integration are welcome.



