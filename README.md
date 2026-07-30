# Krishi AI: A Multi-Modal AI Assistant for Farmers

A proof-of-concept for an AI-powered agricultural assistant that provides visual disease diagnosis and conversational advice to farmers via common messaging platforms.

---

### ⚠️ Project Status & Disclaimer

**Please Note:** This project is a functional proof-of-concept. The core AI components have been successfully built and tested individually, but their final integration is still under engineering. The code and models in this submission represent our current progress. As we are actively working to improve the system, the final presented version may include further enhancements and optimizations. 
The plant detection/ disease identification model has a 98.43% validation accuracy and 97.65% Training accuracy with low losses. When the model is run it give a high accuracy answer with varying confidence levels, yet a still very high confidence levels for most test cases (even for random pictures from the internet).(Made with Transfer learning, data augmentation learning, etc)

The AGENTIC AI for this project has been built and is still being trained to improve its answers to give accurate and well human readable answers in different languages. (Made with 7b llm gguf integrated will llama)

Pictures and code(Partial- the agentic ai has picture confirmation) for the project is added in the zip file.

---
## System Architecture (Proposed)

This diagram shows the intended end-to-end workflow for Krishi AI.

`Farmer (WhatsApp)  ->  [Proposed Server & API Gateway]  ->  Image Analysis (CV Model)  ->  Contextual Info (Weather/Finance APIs)  ->  Conversational Advice (Agentic_AI) (7B LLM)  ->  Farmer`

---

## How to Run This Project

The project's components can be tested as described below. Note that the full integration is the next phase of development.

### Part 1: Plant Disease Identification Model (Functional Demo)
This model can identify 15 different plant diseases from an image.

1.  Open the included `Krishi_AI_Notebook.ipynb` file in Google Colab.
2.  Upload the included `my_augmented_model.zip` file to the Colab environment.
3.  Run the first cell in the notebook to unzip the model.
4.  Run the subsequent cells to load the model and the inference script.
5.  Upload a plant leaf image when prompted to get a diagnosis with a confidence score.

### Part 2: Agentic AI (Local Demo)
This is the conversational agent that provides detailed advice.

**Note:** The 7B LLM GGUF file (~4 GB) is too large for this submission and must be downloaded separately.

1.  A powerful local machine with an NVIDIA GPU is required.
2.  Set up `llama.cpp` with CUDA bindings.
3.  Run the local Python script, which will load the 7B GGUF model and allow you to ask crop-related questions in the terminal.

### Part 3: API Integrations (Conceptual Design)
This section outlines the APIs intended for the fully integrated version of Krishi AI.

* **WhatsApp Business API**: To serve as the primary user interface.
* **Weather API**: To provide real-time, localized weather data for context-aware advice.
* **Finance API**: To integrate local market prices for crops, helping farmers make economically informed decisions.

---
## Inspiration

The motivation to develop this agentic AI model for farmers arose from witnessing how intensely farmers battle crop diseases and the absence of timely advice. Most rural farmers lack easy access to agricultural specialists, and before they notice a disease, it already results in significant yield losses. With how platforms such as WhatsApp and Meta have simplified the way people communicate, We wished to make something similar but for agriculture—a smart assistant that is convenient to use for farmers. The plan was to integrate AI with affordable technology in a way that farmers would only need to send a photo of their crops, respond to a few queries, and receive precise information regarding potential diseases and cures instantly. This project came into being based on the dream of minimizing the loss of crops, equipping farmers with information, and ultimately supporting food security and sustainable agriculture.

---
## What it does

Krishi AI is an agentic AI assistant designed to support farmers in protecting and improving their crops. By simply sending a photo of their plants on WhatsApp, farmers can instantly get insights about possible diseases along with practical solutions. The system is enhanced with weather and finance APIs, so it can give recommendations that are more accurate and suited to local conditions. Our goal with Krishi AI is to make advanced agricultural support accessible, affordable, and easy to use for every farmer.

---
## Technology Stack

Python, PyTorch, C++, Hugging Face Transformers, MobileNetV2, 7B LLM, GGUF, PlantVillage Dataset, Transfer Learning, Fine-tuning, **Data Augmentation**, Prompt Engineering, Quantization, llama.cpp, CUDA, NVIDIA RTX 4070, OpenCV, NumPy, Matplotlib, Pillow (PIL), Google Colab, Weather APIs, Finance APIs.


---
## How we built it
We created a multi-modal AI by fine-tuning a **MobileNetV2** computer vision model on the **PlantVillage dataset**. By implementing **data augmentation** techniques (random flips, rotations, and color adjustments), we trained a highly robust model. This diagnostic tool is designed to be integrated with a **7B parameter LLM** running locally via `llama.cpp` with CUDA acceleration, which provides farmers with detailed, multilingual conversational advice. The full pipeline envisions integrating with a WhatsApp Business Account and combining weather and finance APIs for better insights.

---
## Challenges we ran into
Key challenges included debugging the image data pipeline and managing GPU memory to run the 7B LLM efficiently offline using GGUF quantization. A significant effort was made to ensure the AI's output, both visual and text-based, was simple and farmer-friendly. We also faced the challenge of not being able to deploy it on a server due to financial constraints, which limited the scalability of our solution.

---
## Accomplishments that we're proud of
We successfully built an end-to-end computer vision system that achieves **98.43% validation accuracy**. Our model demonstrates **high confidence** on both test images from the dataset and random, "in-the-wild" images, showing strong generalization. We are also proud of successfully deploying a 7B parameter LLM locally, proving a tool that can guide a farmer from a simple photo to a complete treatment plan is feasible without cloud costs.

---
## What we learned
This project demonstrated the power of combining specialized models. We learned that **transfer learning with data augmentation** is key for high-accuracy vision tasks, while **quantization** is essential for running large-scale language models on local hardware. We also learned how to connect AI models with real-world platforms using APIs and design impactful solutions while balancing technical and financial constraints.

---
## What's next for Krishi AI
Our next step is to secure funding to pipeline the individual components and deploy the integrated system on a server. The ultimate goal is to launch a pilot program with a small group of farmers to gather real-world feedback, further improving the model's performance and usability.
