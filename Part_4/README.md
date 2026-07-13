## LLM-Powered Feature: Structured Extraction
 
 **Structured JSON Extraction is chosen because it turns unpredictable LLM text into guaranteed, type-safe data that your software can immediately use.**

 The steps of this parts are given below:
 * **Load necessary libraries.**
 * **API_KEY Setup**
 * **Set up the LLM API connection:** define a function call_llm
 * **Prompt design:**
      * **system prompt:** 'You are a structured data extractor.'
      * **user prompt:** 'What are the factors affecting a student lifestyle?'

    Chose temperature=0 for this task because low temperature near 0 results in deterministic, predictable outputs suitable for structured data tasks.
* **Temperature A/B comparison:**
  
  * **temperature 0:** deteminstic, predictable and simple output.
  *  **tempreature 0.7:** creative and unpredictable output.
 
  * **Structured output handling:**
  *  **Guardrails**
  

  
      
