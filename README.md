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

note: you can use experimental models without paying for them, look for the url: https://ai.google.dev/gemini-api/docs/models/experimental-models

current experimental model is: gemini-exp-1206

you need to edit delay routine to not to throttle the api but it may still throttle (stops responding after a outputting few files)
```
await new Promise(resolve => setTimeout(resolve, 60 * 1000)); // Delay
```
you can directly paste contents of the "ai-studio prompt.txt" file to the https://aistudio.google.com/prompts/new_chat and see the tagged output one report at a time. Note: you must save the output as an html file, by adding ".html" extension, and see the result in a browser.
you can directly paste contents of the "ai-studio prompt.txt" file to the and see the tagged output one report at a time. Note: you must save the output as a html file, by adding ".html" extension, and see the result by opening that file in a web browser. Please edit safety setting in google ai studio, and set "block none" for all of them.

