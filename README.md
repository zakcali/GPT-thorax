# GPT-thorax

GPT-NER for Thorax-CT reports

nodejs program to send "Thorax CT" reports and receive tagged outputs

you must define enviromental variable GEMINI_API_KEY, which you obtain from google-ai-studio

Install the libraries by entering the following command in the keyboard:
```
npm install @google/generative-ai
```
make an empty folder "ouputs"

Run the program by typing:
```
node test-bt-exp-1206.js
```
find the tagged html reports in "outputs" folder

js (nodejs) program reads the file named "bt prompt.html", appends one report to the end of prompt, sends prompt to gemini-api, receives and outputs the responses

you may need to edit delay routine to not to throttle the api but it may still throttle (stops responding after outputting a few files)
```
await new Promise(resolve => setTimeout(resolve, 60 * 1000)); // Delay
```
you can directly paste contents of the "ai-studio prompt.txt" file to the https://aistudio.google.com/prompts/new_chat and see the tagged output one report at a time. Note: you must save the output as an html file, by adding ".html" extension, and see the result in a browser.
you can directly paste contents of the "ai-studio prompt.txt" file to the and see the tagged output one report at a time. Note: you must save the output as a html file, by adding ".html" extension, and see the result by opening that file in a web browser. Please edit safety setting in google ai studio, and set "block none" for all of them.

note: you can use experimental models without paying for them, look for the url: https://ai.google.dev/gemini-api/docs/models/experimental-models

current experimental model is: gemini-exp-1206

look for limits of experimental models: https://discuss.ai.google.dev/t/whats-the-rate-limit-for-the-experimental-models/38226

you can list the usable models for you with your api key. type this to your address bar of the browser https://generativelanguage.googleapis.com/v1beta/models?key=$GEMINI_API_KEY

if your GEMINI_API_KEY is "lFrWertd-tUyhGhpWwWwsD", then you must type this
```
https://generativelanguage.googleapis.com/v1beta/models?key=lFrWertd-tUyhGhpWwWwsD
```

here is the current output as July 30, 2025
```
{
  "models": [
    {
      "name": "models/embedding-gecko-001",
      "version": "001",
      "displayName": "Embedding Gecko",
      "description": "Obtain a distributed representation of a text.",
      "inputTokenLimit": 1024,
      "outputTokenLimit": 1,
      "supportedGenerationMethods": [
        "embedText",
        "countTextTokens"
      ]
    },
    {
      "name": "models/gemini-1.5-pro-latest",
      "version": "001",
      "displayName": "Gemini 1.5 Pro Latest",
      "description": "Alias that points to the most recent production (non-experimental) release of Gemini 1.5 Pro, our mid-size multimodal model that supports up to 2 million tokens.",
      "inputTokenLimit": 2000000,
      "outputTokenLimit": 8192,
      "supportedGenerationMethods": [
        "generateContent",
        "countTokens"
      ],
      "temperature": 1,
      "topP": 0.95,
      "topK": 40,
      "maxTemperature": 2
    },
    {
      "name": "models/gemini-1.5-pro-002",
      "version": "002",
      "displayName": "Gemini 1.5 Pro 002",
      "description": "Stable version of Gemini 1.5 Pro, our mid-size multimodal model that supports up to 2 million tokens, released in September of 2024.",
      "inputTokenLimit": 2000000,
      "outputTokenLimit": 8192,
      "supportedGenerationMethods": [
        "generateContent",
        "countTokens",
        "createCachedContent"
      ],
      "temperature": 1,
      "topP": 0.95,
      "topK": 40,
      "maxTemperature": 2
    },
    {
      "name": "models/gemini-1.5-pro",
      "version": "001",
      "displayName": "Gemini 1.5 Pro",
      "description": "Stable version of Gemini 1.5 Pro, our mid-size multimodal model that supports up to 2 million tokens, released in May of 2024.",
      "inputTokenLimit": 2000000,
      "outputTokenLimit": 8192,
      "supportedGenerationMethods": [
        "generateContent",
        "countTokens"
      ],
      "temperature": 1,
      "topP": 0.95,
      "topK": 40,
      "maxTemperature": 2
    },
    {
      "name": "models/gemini-1.5-flash-latest",
      "version": "001",
      "displayName": "Gemini 1.5 Flash Latest",
      "description": "Alias that points to the most recent production (non-experimental) release of Gemini 1.5 Flash, our fast and versatile multimodal model for scaling across diverse tasks.",
      "inputTokenLimit": 1000000,
      "outputTokenLimit": 8192,
      "supportedGenerationMethods": [
        "generateContent",
        "countTokens"
      ],
      "temperature": 1,
      "topP": 0.95,
      "topK": 40,
      "maxTemperature": 2
    },
    {
      "name": "models/gemini-1.5-flash",
      "version": "001",
      "displayName": "Gemini 1.5 Flash",
      "description": "Alias that points to the most recent stable version of Gemini 1.5 Flash, our fast and versatile multimodal model for scaling across diverse tasks.",
      "inputTokenLimit": 1000000,
      "outputTokenLimit": 8192,
      "supportedGenerationMethods": [
        "generateContent",
        "countTokens"
      ],
      "temperature": 1,
      "topP": 0.95,
      "topK": 40,
      "maxTemperature": 2
    },
    {
      "name": "models/gemini-1.5-flash-002",
      "version": "002",
      "displayName": "Gemini 1.5 Flash 002",
      "description": "Stable version of Gemini 1.5 Flash, our fast and versatile multimodal model for scaling across diverse tasks, released in September of 2024.",
      "inputTokenLimit": 1000000,
      "outputTokenLimit": 8192,
      "supportedGenerationMethods": [
        "generateContent",
        "countTokens",
        "createCachedContent"
      ],
      "temperature": 1,
      "topP": 0.95,
      "topK": 40,
      "maxTemperature": 2
    },
    {
      "name": "models/gemini-1.5-flash-8b",
      "version": "001",
      "displayName": "Gemini 1.5 Flash-8B",
      "description": "Stable version of Gemini 1.5 Flash-8B, our smallest and most cost effective Flash model, released in October of 2024.",
      "inputTokenLimit": 1000000,
      "outputTokenLimit": 8192,
      "supportedGenerationMethods": [
        "createCachedContent",
        "generateContent",
        "countTokens"
      ],
      "temperature": 1,
      "topP": 0.95,
      "topK": 40,
      "maxTemperature": 2
    },
    {
      "name": "models/gemini-1.5-flash-8b-001",
      "version": "001",
      "displayName": "Gemini 1.5 Flash-8B 001",
      "description": "Stable version of Gemini 1.5 Flash-8B, our smallest and most cost effective Flash model, released in October of 2024.",
      "inputTokenLimit": 1000000,
      "outputTokenLimit": 8192,
      "supportedGenerationMethods": [
        "createCachedContent",
        "generateContent",
        "countTokens"
      ],
      "temperature": 1,
      "topP": 0.95,
      "topK": 40,
      "maxTemperature": 2
    },
    {
      "name": "models/gemini-1.5-flash-8b-latest",
      "version": "001",
      "displayName": "Gemini 1.5 Flash-8B Latest",
      "description": "Alias that points to the most recent production (non-experimental) release of Gemini 1.5 Flash-8B, our smallest and most cost effective Flash model, released in October of 2024.",
      "inputTokenLimit": 1000000,
      "outputTokenLimit": 8192,
      "supportedGenerationMethods": [
        "createCachedContent",
        "generateContent",
        "countTokens"
      ],
      "temperature": 1,
      "topP": 0.95,
      "topK": 40,
      "maxTemperature": 2
    },
    {
      "name": "models/gemini-2.5-pro-preview-03-25",
      "version": "2.5-preview-03-25",
      "displayName": "Gemini 2.5 Pro Preview 03-25",
      "description": "Gemini 2.5 Pro Preview 03-25",
      "inputTokenLimit": 1048576,
      "outputTokenLimit": 65536,
      "supportedGenerationMethods": [
        "generateContent",
        "countTokens",
        "createCachedContent",
        "batchGenerateContent"
      ],
      "temperature": 1,
      "topP": 0.95,
      "topK": 64,
      "maxTemperature": 2,
      "thinking": true
    },
    {
      "name": "models/gemini-2.5-flash-preview-05-20",
      "version": "2.5-preview-05-20",
      "displayName": "Gemini 2.5 Flash Preview 05-20",
      "description": "Preview release (April 17th, 2025) of Gemini 2.5 Flash",
      "inputTokenLimit": 1048576,
      "outputTokenLimit": 65536,
      "supportedGenerationMethods": [
        "generateContent",
        "countTokens",
        "createCachedContent",
        "batchGenerateContent"
      ],
      "temperature": 1,
      "topP": 0.95,
      "topK": 64,
      "maxTemperature": 2,
      "thinking": true
    },
    {
      "name": "models/gemini-2.5-flash",
      "version": "001",
      "displayName": "Gemini 2.5 Flash",
      "description": "Stable version of Gemini 2.5 Flash, our mid-size multimodal model that supports up to 1 million tokens, released in June of 2025.",
      "inputTokenLimit": 1048576,
      "outputTokenLimit": 65536,
      "supportedGenerationMethods": [
        "generateContent",
        "countTokens",
        "createCachedContent",
        "batchGenerateContent"
      ],
      "temperature": 1,
      "topP": 0.95,
      "topK": 64,
      "maxTemperature": 2,
      "thinking": true
    },
    {
      "name": "models/gemini-2.5-flash-lite-preview-06-17",
      "version": "2.5-preview-06-17",
      "displayName": "Gemini 2.5 Flash-Lite Preview 06-17",
      "description": "Preview release (June 11th, 2025) of Gemini 2.5 Flash-Lite",
      "inputTokenLimit": 1048576,
      "outputTokenLimit": 65536,
      "supportedGenerationMethods": [
        "generateContent",
        "countTokens",
        "createCachedContent",
        "batchGenerateContent"
      ],
      "temperature": 1,
      "topP": 0.95,
      "topK": 64,
      "maxTemperature": 2,
      "thinking": true
    },
    {
      "name": "models/gemini-2.5-pro-preview-05-06",
      "version": "2.5-preview-05-06",
      "displayName": "Gemini 2.5 Pro Preview 05-06",
      "description": "Preview release (May 6th, 2025) of Gemini 2.5 Pro",
      "inputTokenLimit": 1048576,
      "outputTokenLimit": 65536,
      "supportedGenerationMethods": [
        "generateContent",
        "countTokens",
        "createCachedContent",
        "batchGenerateContent"
      ],
      "temperature": 1,
      "topP": 0.95,
      "topK": 64,
      "maxTemperature": 2,
      "thinking": true
    },
    {
      "name": "models/gemini-2.5-pro-preview-06-05",
      "version": "2.5-preview-06-05",
      "displayName": "Gemini 2.5 Pro Preview",
      "description": "Preview release (June 5th, 2025) of Gemini 2.5 Pro",
      "inputTokenLimit": 1048576,
      "outputTokenLimit": 65536,
      "supportedGenerationMethods": [
        "generateContent",
        "countTokens",
        "createCachedContent",
        "batchGenerateContent"
      ],
      "temperature": 1,
      "topP": 0.95,
      "topK": 64,
      "maxTemperature": 2,
      "thinking": true
    },
    {
      "name": "models/gemini-2.5-pro",
      "version": "2.5",
      "displayName": "Gemini 2.5 Pro",
      "description": "Stable release (June 17th, 2025) of Gemini 2.5 Pro",
      "inputTokenLimit": 1048576,
      "outputTokenLimit": 65536,
      "supportedGenerationMethods": [
        "generateContent",
        "countTokens",
        "createCachedContent",
        "batchGenerateContent"
      ],
      "temperature": 1,
      "topP": 0.95,
      "topK": 64,
      "maxTemperature": 2,
      "thinking": true
    },
    {
      "name": "models/gemini-2.0-flash-exp",
      "version": "2.0",
      "displayName": "Gemini 2.0 Flash Experimental",
      "description": "Gemini 2.0 Flash Experimental",
      "inputTokenLimit": 1048576,
      "outputTokenLimit": 8192,
      "supportedGenerationMethods": [
        "generateContent",
        "countTokens",
        "bidiGenerateContent"
      ],
      "temperature": 1,
      "topP": 0.95,
      "topK": 40,
      "maxTemperature": 2
    },
    {
      "name": "models/gemini-2.0-flash",
      "version": "2.0",
      "displayName": "Gemini 2.0 Flash",
      "description": "Gemini 2.0 Flash",
      "inputTokenLimit": 1048576,
      "outputTokenLimit": 8192,
      "supportedGenerationMethods": [
        "generateContent",
        "countTokens",
        "createCachedContent",
        "batchGenerateContent"
      ],
      "temperature": 1,
      "topP": 0.95,
      "topK": 40,
      "maxTemperature": 2
    },
    {
      "name": "models/gemini-2.0-flash-001",
      "version": "2.0",
      "displayName": "Gemini 2.0 Flash 001",
      "description": "Stable version of Gemini 2.0 Flash, our fast and versatile multimodal model for scaling across diverse tasks, released in January of 2025.",
      "inputTokenLimit": 1048576,
      "outputTokenLimit": 8192,
      "supportedGenerationMethods": [
        "generateContent",
        "countTokens",
        "createCachedContent",
        "batchGenerateContent"
      ],
      "temperature": 1,
      "topP": 0.95,
      "topK": 40,
      "maxTemperature": 2
    },
    {
      "name": "models/gemini-2.0-flash-exp-image-generation",
      "version": "2.0",
      "displayName": "Gemini 2.0 Flash (Image Generation) Experimental",
      "description": "Gemini 2.0 Flash (Image Generation) Experimental",
      "inputTokenLimit": 1048576,
      "outputTokenLimit": 8192,
      "supportedGenerationMethods": [
        "generateContent",
        "countTokens",
        "bidiGenerateContent"
      ],
      "temperature": 1,
      "topP": 0.95,
      "topK": 40,
      "maxTemperature": 2
    },
    {
      "name": "models/gemini-2.0-flash-lite-001",
      "version": "2.0",
      "displayName": "Gemini 2.0 Flash-Lite 001",
      "description": "Stable version of Gemini 2.0 Flash-Lite",
      "inputTokenLimit": 1048576,
      "outputTokenLimit": 8192,
      "supportedGenerationMethods": [
        "generateContent",
        "countTokens",
        "createCachedContent",
        "batchGenerateContent"
      ],
      "temperature": 1,
      "topP": 0.95,
      "topK": 40,
      "maxTemperature": 2
    },
    {
      "name": "models/gemini-2.0-flash-lite",
      "version": "2.0",
      "displayName": "Gemini 2.0 Flash-Lite",
      "description": "Gemini 2.0 Flash-Lite",
      "inputTokenLimit": 1048576,
      "outputTokenLimit": 8192,
      "supportedGenerationMethods": [
        "generateContent",
        "countTokens",
        "createCachedContent",
        "batchGenerateContent"
      ],
      "temperature": 1,
      "topP": 0.95,
      "topK": 40,
      "maxTemperature": 2
    },
    {
      "name": "models/gemini-2.0-flash-preview-image-generation",
      "version": "2.0",
      "displayName": "Gemini 2.0 Flash Preview Image Generation",
      "description": "Gemini 2.0 Flash Preview Image Generation",
      "inputTokenLimit": 32768,
      "outputTokenLimit": 8192,
      "supportedGenerationMethods": [
        "generateContent",
        "countTokens"
      ],
      "temperature": 1,
      "topP": 0.95,
      "topK": 64,
      "maxTemperature": 2
    },
    {
      "name": "models/gemini-2.0-flash-lite-preview-02-05",
      "version": "preview-02-05",
      "displayName": "Gemini 2.0 Flash-Lite Preview 02-05",
      "description": "Preview release (February 5th, 2025) of Gemini 2.0 Flash-Lite",
      "inputTokenLimit": 1048576,
      "outputTokenLimit": 8192,
      "supportedGenerationMethods": [
        "generateContent",
        "countTokens",
        "createCachedContent",
        "batchGenerateContent"
      ],
      "temperature": 1,
      "topP": 0.95,
      "topK": 40,
      "maxTemperature": 2
    },
    {
      "name": "models/gemini-2.0-flash-lite-preview",
      "version": "preview-02-05",
      "displayName": "Gemini 2.0 Flash-Lite Preview",
      "description": "Preview release (February 5th, 2025) of Gemini 2.0 Flash-Lite",
      "inputTokenLimit": 1048576,
      "outputTokenLimit": 8192,
      "supportedGenerationMethods": [
        "generateContent",
        "countTokens",
        "createCachedContent",
        "batchGenerateContent"
      ],
      "temperature": 1,
      "topP": 0.95,
      "topK": 40,
      "maxTemperature": 2
    },
    {
      "name": "models/gemini-2.0-pro-exp",
      "version": "2.5-exp-03-25",
      "displayName": "Gemini 2.0 Pro Experimental",
      "description": "Experimental release (March 25th, 2025) of Gemini 2.5 Pro",
      "inputTokenLimit": 1048576,
      "outputTokenLimit": 65536,
      "supportedGenerationMethods": [
        "generateContent",
        "countTokens",
        "createCachedContent",
        "batchGenerateContent"
      ],
      "temperature": 1,
      "topP": 0.95,
      "topK": 64,
      "maxTemperature": 2,
      "thinking": true
    },
    {
      "name": "models/gemini-2.0-pro-exp-02-05",
      "version": "2.5-exp-03-25",
      "displayName": "Gemini 2.0 Pro Experimental 02-05",
      "description": "Experimental release (March 25th, 2025) of Gemini 2.5 Pro",
      "inputTokenLimit": 1048576,
      "outputTokenLimit": 65536,
      "supportedGenerationMethods": [
        "generateContent",
        "countTokens",
        "createCachedContent",
        "batchGenerateContent"
      ],
      "temperature": 1,
      "topP": 0.95,
      "topK": 64,
      "maxTemperature": 2,
      "thinking": true
    },
    {
      "name": "models/gemini-exp-1206",
      "version": "2.5-exp-03-25",
      "displayName": "Gemini Experimental 1206",
      "description": "Experimental release (March 25th, 2025) of Gemini 2.5 Pro",
      "inputTokenLimit": 1048576,
      "outputTokenLimit": 65536,
      "supportedGenerationMethods": [
        "generateContent",
        "countTokens",
        "createCachedContent",
        "batchGenerateContent"
      ],
      "temperature": 1,
      "topP": 0.95,
      "topK": 64,
      "maxTemperature": 2,
      "thinking": true
    },
    {
      "name": "models/gemini-2.0-flash-thinking-exp-01-21",
      "version": "2.5-preview-05-20",
      "displayName": "Gemini 2.5 Flash Preview 05-20",
      "description": "Preview release (April 17th, 2025) of Gemini 2.5 Flash",
      "inputTokenLimit": 1048576,
      "outputTokenLimit": 65536,
      "supportedGenerationMethods": [
        "generateContent",
        "countTokens",
        "createCachedContent",
        "batchGenerateContent"
      ],
      "temperature": 1,
      "topP": 0.95,
      "topK": 64,
      "maxTemperature": 2,
      "thinking": true
    },
    {
      "name": "models/gemini-2.0-flash-thinking-exp",
      "version": "2.5-preview-05-20",
      "displayName": "Gemini 2.5 Flash Preview 05-20",
      "description": "Preview release (April 17th, 2025) of Gemini 2.5 Flash",
      "inputTokenLimit": 1048576,
      "outputTokenLimit": 65536,
      "supportedGenerationMethods": [
        "generateContent",
        "countTokens",
        "createCachedContent",
        "batchGenerateContent"
      ],
      "temperature": 1,
      "topP": 0.95,
      "topK": 64,
      "maxTemperature": 2,
      "thinking": true
    },
    {
      "name": "models/gemini-2.0-flash-thinking-exp-1219",
      "version": "2.5-preview-05-20",
      "displayName": "Gemini 2.5 Flash Preview 05-20",
      "description": "Preview release (April 17th, 2025) of Gemini 2.5 Flash",
      "inputTokenLimit": 1048576,
      "outputTokenLimit": 65536,
      "supportedGenerationMethods": [
        "generateContent",
        "countTokens",
        "createCachedContent",
        "batchGenerateContent"
      ],
      "temperature": 1,
      "topP": 0.95,
      "topK": 64,
      "maxTemperature": 2,
      "thinking": true
    },
    {
      "name": "models/gemini-2.5-flash-preview-tts",
      "version": "gemini-2.5-flash-exp-tts-2025-05-19",
      "displayName": "Gemini 2.5 Flash Preview TTS",
      "description": "Gemini 2.5 Flash Preview TTS",
      "inputTokenLimit": 8192,
      "outputTokenLimit": 16384,
      "supportedGenerationMethods": [
        "countTokens",
        "generateContent"
      ],
      "temperature": 1,
      "topP": 0.95,
      "topK": 64,
      "maxTemperature": 2
    },
    {
      "name": "models/gemini-2.5-pro-preview-tts",
      "version": "gemini-2.5-pro-preview-tts-2025-05-19",
      "displayName": "Gemini 2.5 Pro Preview TTS",
      "description": "Gemini 2.5 Pro Preview TTS",
      "inputTokenLimit": 8192,
      "outputTokenLimit": 16384,
      "supportedGenerationMethods": [
        "countTokens",
        "generateContent"
      ],
      "temperature": 1,
      "topP": 0.95,
      "topK": 64,
      "maxTemperature": 2
    },
    {
      "name": "models/learnlm-2.0-flash-experimental",
      "version": "2.0",
      "displayName": "LearnLM 2.0 Flash Experimental",
      "description": "LearnLM 2.0 Flash Experimental",
      "inputTokenLimit": 1048576,
      "outputTokenLimit": 32768,
      "supportedGenerationMethods": [
        "generateContent",
        "countTokens"
      ],
      "temperature": 1,
      "topP": 0.95,
      "topK": 64,
      "maxTemperature": 2
    },
    {
      "name": "models/gemma-3-1b-it",
      "version": "001",
      "displayName": "Gemma 3 1B",
      "inputTokenLimit": 32768,
      "outputTokenLimit": 8192,
      "supportedGenerationMethods": [
        "generateContent",
        "countTokens"
      ],
      "temperature": 1,
      "topP": 0.95,
      "topK": 64
    },
    {
      "name": "models/gemma-3-4b-it",
      "version": "001",
      "displayName": "Gemma 3 4B",
      "inputTokenLimit": 32768,
      "outputTokenLimit": 8192,
      "supportedGenerationMethods": [
        "generateContent",
        "countTokens"
      ],
      "temperature": 1,
      "topP": 0.95,
      "topK": 64
    },
    {
      "name": "models/gemma-3-12b-it",
      "version": "001",
      "displayName": "Gemma 3 12B",
      "inputTokenLimit": 32768,
      "outputTokenLimit": 8192,
      "supportedGenerationMethods": [
        "generateContent",
        "countTokens"
      ],
      "temperature": 1,
      "topP": 0.95,
      "topK": 64
    },
    {
      "name": "models/gemma-3-27b-it",
      "version": "001",
      "displayName": "Gemma 3 27B",
      "inputTokenLimit": 131072,
      "outputTokenLimit": 8192,
      "supportedGenerationMethods": [
        "generateContent",
        "countTokens"
      ],
      "temperature": 1,
      "topP": 0.95,
      "topK": 64
    },
    {
      "name": "models/gemma-3n-e4b-it",
      "version": "001",
      "displayName": "Gemma 3n E4B",
      "inputTokenLimit": 8192,
      "outputTokenLimit": 2048,
      "supportedGenerationMethods": [
        "generateContent",
        "countTokens"
      ],
      "temperature": 1,
      "topP": 0.95,
      "topK": 64
    },
    {
      "name": "models/gemma-3n-e2b-it",
      "version": "001",
      "displayName": "Gemma 3n E2B",
      "inputTokenLimit": 8192,
      "outputTokenLimit": 2048,
      "supportedGenerationMethods": [
        "generateContent",
        "countTokens"
      ],
      "temperature": 1,
      "topP": 0.95,
      "topK": 64
    },
    {
      "name": "models/gemini-2.5-flash-lite",
      "version": "001",
      "displayName": "Gemini 2.5 Flash-Lite",
      "description": "Stable verion of Gemini 2.5 Flash-Lite, released in July of 2025",
      "inputTokenLimit": 1048576,
      "outputTokenLimit": 65536,
      "supportedGenerationMethods": [
        "generateContent",
        "countTokens",
        "createCachedContent",
        "batchGenerateContent"
      ],
      "temperature": 1,
      "topP": 0.95,
      "topK": 64,
      "maxTemperature": 2,
      "thinking": true
    },
    {
      "name": "models/embedding-001",
      "version": "001",
      "displayName": "Embedding 001",
      "description": "Obtain a distributed representation of a text.",
      "inputTokenLimit": 2048,
      "outputTokenLimit": 1,
      "supportedGenerationMethods": [
        "embedContent"
      ]
    },
    {
      "name": "models/text-embedding-004",
      "version": "004",
      "displayName": "Text Embedding 004",
      "description": "Obtain a distributed representation of a text.",
      "inputTokenLimit": 2048,
      "outputTokenLimit": 1,
      "supportedGenerationMethods": [
        "embedContent"
      ]
    },
    {
      "name": "models/gemini-embedding-exp-03-07",
      "version": "exp-03-07",
      "displayName": "Gemini Embedding Experimental 03-07",
      "description": "Obtain a distributed representation of a text.",
      "inputTokenLimit": 8192,
      "outputTokenLimit": 1,
      "supportedGenerationMethods": [
        "embedContent",
        "countTextTokens",
        "countTokens"
      ]
    },
    {
      "name": "models/gemini-embedding-exp",
      "version": "exp-03-07",
      "displayName": "Gemini Embedding Experimental",
      "description": "Obtain a distributed representation of a text.",
      "inputTokenLimit": 8192,
      "outputTokenLimit": 1,
      "supportedGenerationMethods": [
        "embedContent",
        "countTextTokens",
        "countTokens"
      ]
    },
    {
      "name": "models/gemini-embedding-001",
      "version": "001",
      "displayName": "Gemini Embedding 001",
      "description": "Obtain a distributed representation of a text.",
      "inputTokenLimit": 2048,
      "outputTokenLimit": 1,
      "supportedGenerationMethods": [
        "embedContent",
        "countTextTokens",
        "countTokens"
      ]
    },
    {
      "name": "models/aqa",
      "version": "001",
      "displayName": "Model that performs Attributed Question Answering.",
      "description": "Model trained to return answers to questions that are grounded in provided sources, along with estimating answerable probability.",
      "inputTokenLimit": 7168,
      "outputTokenLimit": 1024,
      "supportedGenerationMethods": [
        "generateAnswer"
      ],
      "temperature": 0.2,
      "topP": 1,
      "topK": 40
    },
    {
      "name": "models/imagen-3.0-generate-002",
      "version": "002",
      "displayName": "Imagen 3.0 002 model",
      "description": "Vertex served Imagen 3.0 002 model",
      "inputTokenLimit": 480,
      "outputTokenLimit": 8192,
      "supportedGenerationMethods": [
        "predict"
      ]
    },
    {
      "name": "models/imagen-4.0-generate-preview-06-06",
      "version": "01",
      "displayName": "Imagen 4 (Preview)",
      "description": "Vertex served Imagen 4.0 model",
      "inputTokenLimit": 480,
      "outputTokenLimit": 8192,
      "supportedGenerationMethods": [
        "predict"
      ]
    }
  ],
  "nextPageToken": "Cihtb2RlbHMvaW1hZ2VuLTQuMC1nZW5lcmF0ZS1wcmV2aWV3LTA2LTA2"
}

```


