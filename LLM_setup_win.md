# Setting up an LLM locally

I am currently trying to set up **LLAMA** locally on my machine. It will be an open-source LLM; among other ones, I have found this one to be appropriate for this project.
This isn't very easy. I am trying to follow the steps.
Once it is done, I will update the instructions on how to do this on Windows 11.
Stay tuned!

Update: Finally, I was able to install the llama LLM on my local machine after a number of retries, failures, and debugging. Here is the list of steps for installation on a Windows 11 machine:

**Step 1 — Clean build folder**

cd D:\LLM\llama.cpp
mkdir build

Step 2 — Configure CMake
cmake -S . -B build -G "Visual Studio 16 2019" -A x64 -DLLAMA_CURL=OFF

Step 3 — Build all normal tools
cmake --build build --config Release --target llama-cli
cmake --build build --config Release --target llama-server
cmake --build build --config Release --target quantize


You can also build EVERYTHING:

cmake --build build --config Release

📂 Where to find the executables

Look in:

D:\LLM\llama.cpp\build\bin\Release\


Or:

D:\LLM\llama.cpp\build\Release\


You will find:

llama-cli.exe
llama-server.exe
quantize.exe
embedding.exe

🎉 Now how to test it
1. Download a tiny model (so testing is fast)

Example: Phi-2 or TinyLlama.

I can give you direct links if you want.

2. Run llama-cli
.\llama-cli -m yourmodel.gguf -p "Hello AI"

3. Run llama-server
.\llama-server -m yourmodel.gguf --port 8080




Then use:

http://localhost:8080/v1/chat/completions

