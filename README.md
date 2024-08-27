# personalized_treatment_planning

**Medical content builder using gemini API**

**Introduction:**
Project overview:
We are building a medical content builder which focuses on ostomy care and provides guidance which also provides a user friendly environment with the help of gemini API.

Objective:
Main goal of this project is to provide information for the ostomy patients with highly accurate info and sitting the references alongside with the animated images for easy use and understanding of medical devices.

**Prerequisites:**
Technical requirements and API access:

*Modules needed are as follows:
    streamlit
    google-generativeai
    python-dotenv

*Creating an .env file for google api or can directly use the api by generating it as follows:
1)Go to google cloud platform.
2)Then by using the navigation menu select APIs and services.
3)Select the Enable APIs and services option.
4)click on +.
5)Now in the search bar we can search for gemini api and create it and enable it.
6)Once created all you need to do is copy the api key  and this can also be managed through credentials in APIs services in the menu bar.

**Setting up Environment:**
Installing necessary libraries:
# Q&A Chatbot
      #from langchain.llms import OpenAI
      from dotenv import load_dotenv
      load_dotenv()  # take environment variables from .env.
      import streamlit as st
      import os
      import pathlib
      import textwrap
      import google.generativeai as genai
      from IPython.display import display
      from IPython.display import Markdown

**Integrating with Gemini API:**

**Api authentication:**
      os.getenv("GOOGLE_API_KEY")
      genai.configure(api_key=os.getenv("GOOGLE_API_KEY"))
**Making a request:**

      def get_gemini_response(question):
        
          model = genai.GenerativeModel('gemini-1.5-flash')
          response = model.generate_content(question)
          return response.text


**Building the chatbot interface:**
          Designing conversation flow:
          
              ##initialize our streamlit app
              st.set_page_config(page_title="Q&A Demo")
              st.header("Gemini Application")
              input=st.text_input("Input: ",key="input")
              submit=st.button("Ask the question")

**Generating responses from gemini api:**
              if submit:
             
                  response=get_gemini_response(input)
                  st.subheader("The Response is")
                  st.write(response)



**Testing and Debugging:**
Test cases:

**query**:Summarise the anatomy and functions of the digestive and urinary systems, mentioning key organs and conditions. Give the user friendly response for better understanding Limit to 150-200 words and cite  two reference link from where it fetched information

**Response**:
Your Body's Two Waste Management Systems: Digestion & Urination
Imagine your body as a busy factory. The digestive system breaks down the food you eat into tiny nutrients your body can use, like a food processing line. It starts with your mouth, where you chew and swallow. Food then travels down the oesophagus, through the stomach where it's churned and mixed with acids, and finally to the small and large intestines where most nutrients are absorbed. Waste products are then eliminated as stool.

The urinary system filters your blood, removing waste products like urea and excess water. Your kidneys are like tiny factories, constantly filtering and cleaning your blood. The filtered waste is then collected as urine and travels through the ureters to your bladder, where it's stored until you urinate.

Common conditions: Digestive issues like heartburn, constipation, and ulcers can affect your digestion. Urinary problems include kidney stones, urinary tract infections, and incontinence.

References:

National Institute of Diabetes and Digestive and Kidney Diseases
National Kidney Foundation


**Debugging tips:**

Always ensure that the api key is enabled on the google platform or you can always create the api by disabling it and again enabling it, if in case there is some problem in fetching responses

**User documentation:**

User guide:
For running the application run by 
Streamlit run app.py    //app.py is file name where i developed my code
And then the chatbot opens and simply test it through prompt.
![Screenshot 2024-08-16 220906](https://github.com/user-attachments/assets/ade213ad-d6d5-4b08-834f-b7ec8998ac1c)

![Screenshot 2024-08-16 220712](https://github.com/user-attachments/assets/1b5767be-26fc-4ba2-bfc6-fa0c9ae2f178)


