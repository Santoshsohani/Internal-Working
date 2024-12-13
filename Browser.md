
### **The Browser's Main Components**

![[Browser_Components.png]]


1. **Data**: Handles session management, cookies, local storage, and indexed databases.
2. **UI**: Manages the user-facing interface, like the address bar, bookmarks, and other visible elements.
3. **Rendering Engine**: Constructs the **Render Tree** and displays content on the screen.
4. **JavaScript Engine**: Parses and executes JavaScript code, handling dynamic functionalities of web pages.
5. **Network**: Manages HTTP/HTTPS requests and responses for resources like HTML, CSS, JavaScript, and images.
6. **Timers**: Powers asynchronous operations such as `setTimeout`, `setInterval`, and the Event Loop.

---

### **How Data is Rendered**

#### **1. DOM (Document Object Model)**

The browser processes the HTML file to build the DOM in several stages:

- **File Loading**: The browser fetches the HTML file via the network.
- **Raw Bytes**: The file's binary data is decoded into characters based on its encoding (e.g., UTF-8).
- **Tokenization**: The character stream is tokenized into elements like `<h1>`, `<p>`, and `<div>`.
- **Object Creation**: Tokens are transformed into objects representing the HTML structure:
    
    ```json
    {
      "tag": "",
      "title": "",
      "description": ""
    }
    ```
    
- **Modeling**: These objects are structured into a tree hierarchy called the **Document Object Model (DOM)**.
- **NodeList**: The DOM Tree is represented as a `NodeList`, where each node corresponds to a part of the document.

#### **2. CSS-OM (CSS Object Model)**

Similar to the DOM, the CSS is processed to create the CSS Object Model (CSS-OM):

- **File Loading**: The browser fetches CSS files or inline styles.
- **Raw Bytes**: CSS is converted from binary data to characters.
- **Tokenization**: The character stream is tokenized into CSS rules (e.g., selectors and properties).
- **Object Creation**: These rules are converted into objects.
- **Modeling**: Objects are organized into a tree structure called the **CSS Object Model (CSS-OM)**.

#### **3. Render Tree**

- The **DOM** and **CSS-OM** are initially independent.
- To display content, the browser's rendering engine merges the two models, performing **layout calculations** (e.g., determining dimensions, positions, and styles).
- The merged structure is called the **Render Tree**, which contains only the visible elements on the page.
- The browser paints the content of the Render Tree to the screen.

---

####  **JavaScript Execution**

When the browser encounters a `<script>` tag, the following happens:

1. **CSS-OM Check**:
    - If the CSS-OM is still being constructed, the JavaScript execution is delayed until the CSS-OM is ready.
2. **DOM Check**:
    - If the CSS-OM is ready but the DOM is still under construction, the browser halts DOM processing temporarily to execute the JavaScript.
3. **Execution**:
    - Once JavaScript is executed, DOM construction resumes, ensuring synchronous behavior.

This behavior ensures that styles and scripts are properly applied without conflicts.
