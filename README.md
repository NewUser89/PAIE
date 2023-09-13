


## How it looks
### Using Llama
Using LLama2 is one of the best offline and free options out there. It is currently under improvement I am working on a prompt that will better incorporate cybersecurity perspective into the AI.


The Accuracy of the AI offline and outside the codes test was great and had equal accuracy to openai or bard but while in code it was facing a few issues may be because of the prompting and all. I will try and fix it.
The speed depends on your system and the GPU and CPU configs you have. currently, it is using the `TheBloke/Llama-2-7B-Chat-GGML` model and can be changed via the `portscanner` and `dnsrecon` files.


The prompt for the model usage looks like this:
```prompt
[INST] <<SYS>> {user_instruction}<</SYS>> NMAP Data to be analyzed: {user_message} [/INST]
```
The instructions looks like this:
```prompt
    Do a NMAP scan analysis on the provided NMAP scan information. The NMAP output must return in a asked format accorging to the provided output format. The data must be accurate in regards towards a pentest report.
    The data must follow the following rules:
    1) The NMAP scans must be done from a pentester point of view
    2) The final output must be minimal according to the format given.
    3) The final output must be kept to a minimal.
    4) If a value not found in the scan just mention an empty string.
    5) Analyze everything even the smallest of data.
    6) Completely analyze the data provided and give a confirm answer using the output format.
    7) mention all the data you found in the output format provided so that regex can be used on it.
    8) avoid unnecessary explaination.
    9) the critical score must be calculated based on the CVE if present or by the nature of the services open
    10) the os information must contain the OS used my the target.
    11) the open ports must include all the open ports listed in the data[tcp] and varifying if it by checking its states value.  you should not negect even one open port.
    12) the vulnerable services can be determined via speculation of the service nature or by analyzing the CVE's found.
    The output format:
        critical score:
        - Give info on the criticality
        "os information":
        - List out the OS information
        "open ports and services":
        - List open ports
        - List open ports services
        "vulnerable service":
        - Based on CVEs or nature of the ports opened list the vulnerable services
        "found cve":
        - List the CVE's found and list the main issues.
```

Using the instruction set and the data provided via the prompt the llama AI generates its output.


cd hackbot
```

### Step 2: Install Dependencies

```bash
pip3 install -r requirements.txt
```

### Step 3: Download the AI Model

```bash
python3 hackbot.py
```

The first time you run HackBot, it will check for the AI model required for the chatbot. If the model is not present, it will be automatically downloaded and saved as "llama-2-7b-chat.ggmlv3.q4_0.bin" in the project directory.

## Usage

To start a conversation with HackBot, run the following command:

### For Local LLama users
The `.env` file must look like this:
```env
RUNPOD_ENDPOINT_ID = ""
RUNPOD_API_KEY = ""
AI_OPTION = "LLAMALOCAL"
```
After that is done run this.
```bash
python hackbot.py
```
### For RunPod LLama users
The `.env` file must look like this:
```env
RUNPOD_ENDPOINT_ID = "<<SERVERLESS ENDPOINT ID>>"
RUNPOD_API_KEY = "<<RUNPOD API KEY>>"
AI_OPTION = "RUNPOD"
```
After that is done run this.
```bash
python3 hackbot.py
```

HackBot will display a banner and wait for your input. You can ask cybersecurity-related questions, and HackBot will respond with informative answers. To exit the chat, simply type "quit_bot" in the input prompt.




