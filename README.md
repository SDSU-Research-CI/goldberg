# Running Ollama in the LLM Notebook on JupyterHub
The following steps will get Ollama running locally in your Jupyter Notebook for commandline or API access.

## Server Setup
1. Navigate to [jupyterhub-research.sdsu.edu](jupyterhub-research.sdsu.edu) and sign in with your SDSUid credentials
2. Click Start Server
3. Select at least 1 GPU of either type
   -  We have a total of 68 NVIDIA L40 48GB and 12 NVIDIA A100 80GB GPUs available for scheduling
4. Select at least 4 CPUs and 8-16GB RAM
5. Select the LLM Notebook
6. Click start
   - If the server does not start within ten minutes it will shut down automatically and allow you to reschedule. If this occurs, it is most likely that the requested resources could not be scheduled. Please reach out to us at itd-research.ci@sdsu.edu if this issue recurs and please include a screenshot or copy & paste of any error message.

## Ollama Setup

### Starting Ollama
Repeat these steps each time you start your notebook
1. Click the "+" icon in the top left
2. From the start page, select the Terminal icon to pull up a linux terminal
3. Run the command `ollama serve`
4. Leave this terminal window running as you continue your work

### Downloading Models
1. Click the "+" icon in the top left
2. From the start page, select the Terminal icon to pull up a linux terminal
3. Check the [Ollama site for models](https://ollama.com/library)
4. Pull down models with `ollama pull [model-name-here]`
   - I. E. `ollama pull llama3`
5. Repeat steps 3-4 for each model you would like to download
6. Make sure all the models you want downloaded successfully with the command `ollama list`

These models should remain under /home/jovyan/.ollama/models. Anything stored under the path /home/jovyan will be remain after notebook restarts.

## Running LLMs with Ollama

### OpenAI API Example
You can clone this repository into your notebook to get a copy of the Jupyter Notebook:
1. Click the "+" icon in the top left
2. From the start page, select the Terminal icon to pull up a linux terminal
3. Run the command `git clone https://github.com/SDSU-Research-CI/goldberg.git`
4. Navigate to the repository directory via the file explorer
5. Open the example notebook `OllamaOpenAIDemo` and make sure you are running it with the "Python \[conda env:llm\]" kernel
6. Modify the model and message content as appropriate for one of the models you downloaded
7. Execute the cell to verify everything works as expected

### Commandline Interaction
You can also run Ollama from the commandline. This is useful for quick interactions with an LLM before writing the code to ineract with the API
1. Click the "+" icon in the top left
2. From the start page, select the Terminal icon to pull up a linux terminal
3. Run the command `ollama run [model-name-here]`
   - I.E. `ollama run llama3`
4. The model may take a moment to load onto the GPU
5. Once loaded, you can type messages and hit enter to send to the LLM
5. When done, enter the message `/bye` to exit commandline interaction
