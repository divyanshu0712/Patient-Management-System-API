# Patient-Management-System-API
A REST API built with FastAPI and Python for managing patient records. Supports full CRUD operations, BMI calculation, and data validation.

🛠️ Tech Stack

FastAPI — Web framework
Pydantic — Data validation
Python — Backend language
JSON — Data storage (upgradeable to PostgreSQL)
Uvicorn — ASGI server


⚙️ Installation & Setup
1. Clone the repository
bashgit clone https://github.com/divyanshubhayani0712/fastapi-patients.git
cd fastapi-patients
2. Create virtual environment
bashpython -m venv myenv
myenv\Scripts\activate  # Windows
source myenv/bin/activate  # Mac/Linux
3. Install dependencies
bashpip install fastapi uvicorn pydantic[email]
4. Run the server
bashuvicorn main:app --reload
5. Open API docs
http://127.0.0.1:8000/docs

📌 API Endpoints
MethodEndpointDescriptionGET/Welcome messageGET/aboutAbout the APIGET/viewGet all patientsGET/patients/{patient_id}Get patient by IDGET/sort?sort_by=age&order=ascSort patientsPOST/createAdd new patientPUT/update/{patient_id}Update patientDELETE/delete/{patient_id}Delete patient

📋 Patient Model
json{
  "id": "P011",
  "name": "John Doe",
  "city": "Mumbai",
  "age": 30,
  "gender": "male",
  "weight": 70.0,
  "height": 1.75
}

🤖 Auto Calculated Fields
These fields are automatically calculated — do not pass them in request:
FieldDescriptionbmiCalculated from weight and heightverdictUnderweight / Normal / Overweight / Obese

📊 BMI Verdict Logic
BMI RangeVerdictBelow 18.5Underweight18.5 — 24.9Normal25 — 29.9Overweight30 and aboveObese

🔍 Example Requests
Create a patient
bashcurl -X POST "http://127.0.0.1:8000/create" \
-H "Content-Type: application/json" \
-d '{
  "id": "P011",
  "name": "John Doe",
  "city": "Mumbai",
  "age": 30,
  "gender": "male",
  "weight": 70.0,
  "height": 1.75
}'
Get patient by ID
bashcurl -X GET "http://127.0.0.1:8000/patients/P001"
Sort by age descending
bashcurl -X GET "http://127.0.0.1:8000/sort?sort_by=age&order=desc"
