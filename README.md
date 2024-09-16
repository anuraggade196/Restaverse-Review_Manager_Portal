# **Review Manager Portal**

### **Project Link**
[Review Manager Portal](http://restaverse-tf-312.centralindia.cloudapp.azure.com/)

---

## **Overview**
The Review Manager Portal is a centralized dashboard where business owners can manage reviews across multiple locations using the Google MyBusiness API. The platform provides an intuitive UI to quickly respond to reviews, filter feedback, and view detailed review information. It features:

- A homepage for quick replies to reviews.
- A reviews page displaying detailed information with filtering options.
- Reviews color-coded based on sentiment (positive, negative, or neutral).
- Secure login through Google OAuth.

---

## **Technologies Used**
- **Frontend**: React.js
- **Backend**: Flask
- **Styling**: Tailwind CSS
- **Deployment**: Docker, Terraform, Microsoft Azure

---

## **Challenges Faced**
1. **OAuth Setup**:  
   - Implementing OAuth securely, ensuring token encryption during client-server communication.
   - Overcoming the challenge of passing tokens via headers and understanding OAuth flow using Google's documentation and community resources.

2. **Mock API Development**:  
   - Since Google MyBusiness API access wasn't available, a mock API was created to replicate the responses for testing.

---

## **Future Prospects**
1. **Features to Implement**:
   - Add analytics and data visualizations for reviews.
   - More filtering options (e.g., by sentiment or date).
   - Enhanced UI/UX with subtle animations.
   - Implement caching to optimize performance.
   - Allow users to run custom queries on reviews.

2. **Development Enhancements**:
   - Secure the server with SSL.
   - Integrate data visualization tools like Chart.js.
   - Enable autoscaling in the cloud infrastructure.
   - Improve security by using a proxy server for isolation.
   - Conduct more extensive unit and integration testing.

---

## **How to Use the Website**
1. **Login**:  
   Click the Google login icon at the bottom of the navbar to sign in.
   
2. **View and Manage Reviews**:  
   - On successful sign-in, the homepage will display the latest reviews, allowing users to quickly reply using the quick-reply option (toggle by hovering).
   - Users can post replies or delete them directly from the homepage.
   
3. **Detailed Review Information**:  
   For more details on reviews or to filter them by location, visit the **Reviews** tab.

4. **Logout**:  
   Click the user icon at the bottom of the navbar to log out.

---

## **Note**
- The current version uses mock data mimicking the response format of the Google MyBusiness API. Any Google account can log in and interact with this data.

---

## **How to Run this Project**

### **Prerequisites**
- **Python**: 3.11+
- **Node.js**: v20+
- **Npm**: v8+
- **Docker** (for containerized deployment)
- **Azure subscription** (for cloud deployment)

---

### **Local Setup**

1. **Google OAuth Setup**:
   - Create a new project in Google Cloud Console.
   - Enable OAuth and configure credentials as explained below.

2. **Backend Setup (Flask)**:
   - Navigate to `/API` and install dependencies:
     ```bash
     pip install -r requirements.txt
     ```
   - Run the Flask server:
     ```bash
     python3 -m flask --app app run --debug
     ```

3. **Frontend Setup (React)**:
   - Navigate to `/client` and install dependencies:
     ```bash
     npm install
     ```
   - Start the React app in development mode:
     ```bash
     npm run dev
     ```

4. **Environment Variables**:
   - For the **API**, configure `.env` in the API folder:
     - `DEBUG`, `CLIENT_ID`, `SECRET_KEY`, `FRONTEND_URL`, `BACKEND_URL`, `ALGORITHM`.
   - For the **Frontend**, configure `.env.local` in the client folder:
     - `VITE_BASEAPI_URL`.

---
## **Screenshots**

<details>
  <summary>Click to view screenshots</summary>

  <img src="https://github.com/anuraggade196/Restaverse-Review_Manager_Portal/blob/main/291281688-1915e867-50b8-4a9b-b418-1301c92bbfa4.png?raw=true" width="30%">

</details>



