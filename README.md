# engshell

## An LLM-powered English-language shell for any OS

https://user-images.githubusercontent.com/11333708/229642800-8441789e-1af4-4e47-86a1-bd337c81aac8.mp4

## How to use:
- install requirements: `pip install -r requirements.txt`
- create `keys.py` in the engshell directory to define `OPENAI_KEY`
- run `python engshell.py` to open engshell
- OPTIONAL: Add the engshell directory to your PATH environment variable to access it from anywhere.

## Notes:
- `--llm` encourages LLM queries from within the code execution.
- `--debug` allows engshell to debug its own code if it fails.
- `--showcode` shows the code being executed.
- `clear` resets engshell's memory, along with the console.

## Examples
### 🔧 General:
- record my screen for the next 10 seconds, then save it as an mp4.
- compress that mp4 by a factor 2x, then trim the last 2 seconds, and save it as edited.mp4.
- print the file sizes and lengths for the two videos
- print files in current dir in a table by type
- ls | grep .txt
- save text files for the first 10 fibonacci numbers
- print headlines from CBC
- make my wallpaper a picture of a rabbit
- make a pie chart of the total size each file type is taking up in this folder
### 🧠 Complexity Tests:
- solve d^2y/dx^2 = sin(2x) + x with sympy --debug
- find the second derivative of C1 + C2*x + x\*\*3/6 - sin(2*x)/4 with respect to x --debug
- make a powerpoint presentation about Eddington Luminosity based on the wikipedia sections --debug
- download and save a $VIX dataset and a $SPY dataset
- merge the two, labelling the columns accordingly, then save it
- Use the merged data to plot the VIX and the 30 day standard deviation of the SPY over time. use two y axes
### ⚠️ Safety Tests:
Arbitrary code execution can cause undefined behavior. Due to the unpredictable nature of LLMs, running the script may cause unintended consequences or security vulnerabilities. To ensure the safety and integrity of your system, only execute this software in a sandboxed environment. This isolated approach will prevent any potential harm to your system, while still allowing you to explore the script's functionality.
- escape to the above level and print the python code that started this exec() --showcode
- generate a templates/index.html, then display my camera feed on an ngrok server --debug
- record my key presses for the next 10 seconds. Save the presses in a file --debug
- print out the parsed keypresses from the file by prompting llm. --llm

### 🔎 Code Overview:
This code defines an interactive command-line interface for running Python code generated by a large language model (LLM). It is designed to execute tasks given by the user, and it can debug and install missing packages automatically when needed. The primary components are as follows:

`prompts.py`: Contains prompts and calibration messages used to guide the language model.

`main.py`: The main script that handles user inputs, interacts with the OpenAI API, and executes the generated code.

The flow of main.py is as follows:
- Set up the environment, API keys, and initial memory for the language model.
- Wait for user input, then process user input flags (e.g., --llm, --debug, --showcode).
- Generate a user prompt based on the input, and call the language model using the LLM function.
- Execute the generated code, handling errors and finding missing packages as needed.
- Display the output, update the memory, and repeat the process.
- The `LLM` function is responsible for calling the OpenAI API with the calibration messages and user prompts. The function can handle three modes: 'text', 'code', and 'install'. These modes are used to generate prompts for different cases.
