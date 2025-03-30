Please also list and add basic needs to these requirements.  
A design pattern should be chosen which makes sense given the following requirements:

Frontend \-- Angular  
F1: **Messaging.** Send messages to the chatbot. Messages should not be longer than 100 characters.  
F2: **Character.** The user should see a character in front of them when typing and sending in a message. Upon sending the message:

- Character should have a pose for “thinking” \-- prompt is being processed in the backend  
- Character should have a pose for the following moods \= \[Happy, Sad, Angry or Upset, Laughing or Humorous, Confused, Blushing or Flustered\]  
- The pose shown should match the generated response, taking into account the context of the conversation.

F3: **Random Phrase.** Fill the chat prompt with a **random phrase out of 100 top frases** (hard coded list). There should be a button to undo the random message if the user had already written something in the text field and wants it back instead of the random phrase.   
F4: **Conversation History.** Conversations should be saved and it should be able for the user to look back into the entire conversation. There should be a button for starting a new conversation.

Backend \-- Node JS  
F5: **Chat Conversation.** The backend should be able to connect to a Chatbot. Queries should be taken from the frontend message and sent to the Chatbot. It should be an ongoing conversation for as long as the user does not request a new conversation.  
F6: **A1 Level Spanish Conversations.** The conversation should also adhere to the following rules:

- Generated response shall be in spanish.  
- Generated response shall be level A1.  
- Generated responses should prioritize using the most frequent words in the language.  
- Generated response shall be no more than 100 characters.

F7: **Mood Evaluation.** The generated response should be sent to another model to be evaluated and categorized into one of the following options: moods \= \[Happy, Sad, Angry or Upset, Laughing or Humorous, Confused, Blushing or Flustered\]

Back and Front end should communicate through HTTP.

DB \-- MongoDB  
F8: The necessary data should be stored in order to be able to see previous conversations.

# **Refined Requirements for Spanish Learning Chatbot Application**

## **Basic Architecture Requirements**

1. **Architecture Pattern: Implement a client-server architecture using the MVC (Model-View-Controller) design pattern with Angular for frontend and Node.js for backend**  
2. **Communication: RESTful API for HTTP communication between frontend and backend**  
3. **Data Storage: MongoDB for persistent storage of conversation history**  
4. **Authentication: Simple user authentication system to associate conversations with users**  
5. **Error Handling: Implement proper error handling throughout the application**

## **Frontend (Angular) Requirements**

### **F1: Messaging Interface**

* **Text input field limited to 100 characters with real-time character count**  
* **Send button to submit messages**  
* **Input validation to prevent empty messages**

### **F2: Character Visualization**

* **Animated character with following pose states:**  
  * **Idle (default state)**  
  * **Thinking (displayed during API calls)**  
  * **Emotional responses matching 6 mood categories:**  
    * **Happy**  
    * **Sad**  
    * **Angry/Upset**  
    * **Laughing/Humorous**  
    * **Confused**  
    * **Blushing/Flustered**  
* **Character poses should be stored as separate assets for each emotional state**  
* **Smooth transitions between character states**

### **F3: Random Phrase Suggestion**

* **Button to fill the input with a random Spanish phrase from predefined list**  
* **Store 100 common A1-level Spanish phrases**  
* **Undo functionality to revert to user's previous input**  
* **Local storage for remembering the user's last input before suggestion**

### **F4: Conversation History**

* **Display scrollable conversation history with timestamps**  
* **Clear visual distinction between user and bot messages**  
* **"New Conversation" button that confirms before clearing current conversation**  
* **Option to browse and load previous conversations**

## **Backend (Node.js) Requirements**

### **F5: Chat Conversation Management**

* **Integration with OpenAI's ChatGPT API or similar LLM**  
* **Conversation context management to maintain conversation state**  
* **Proper API key security and request rate limiting**  
* **Fallback responses for API failures**

### **F6: A1 Level Spanish Response Generation**

* **Custom prompt engineering to ensure:**  
  * **All responses are in Spanish**  
  * **Vocabulary limited to A1 level (beginner) Spanish**  
  * **Prioritization of high-frequency Spanish words**  
  * **Maximum response length of 100 characters**  
* **Include language learning hints or translations when appropriate**

### **F7: Mood Analysis and Classification**

* **Secondary model/API call to analyze sentiment of generated response**  
* **Classification algorithm to map sentiment to one of the 6 mood categories**  
* **Response metadata to include both text and mood classification**  
* **Optimization to minimize response time despite dual API calls**

## **Database (MongoDB) Requirements**

### **F8: Data Persistence and Retrieval**

* **Data schema for storing:**  
  * **User ID**  
  * **Conversation ID**  
  * **Individual messages with timestamps**  
  * **Sender type (user or bot)**  
  * **Mood classification for bot responses**  
* **Indexing for efficient conversation retrieval**  
* **Data pagination for loading long conversation histories**  
* **Optional: Analytics collection for tracking learning progress**

## **Additional Considerations**

1. **Responsiveness: Application should work on both desktop and mobile devices**  
2. **Accessibility: Implement basic accessibility features (ARIA labels, keyboard navigation)**  
3. **Internationalization: UI elements should support multiple languages even though chat is in Spanish**  
4. **Performance: Optimize loading times and minimize API latency**  
5. **Testing: Unit and integration tests for critical functionality**

