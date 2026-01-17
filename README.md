# Cancer Detection & Treatment System

A comprehensive Django-based intelligent cancer detection and treatment planning platform that leverages machine learning, medical imaging analysis, and AI-powered clinical decision support to assist healthcare professionals in cancer diagnosis, treatment planning, and patient management.

## 🎯 Project Overview

This system integrates multiple advanced capabilities to provide a holistic approach to cancer care:

- **Intelligent Image Analysis**: Automated cancer detection from medical images using YOLOv8 and OpenCV
- **Personalized Treatment Planning**: AI-generated treatment plans based on patient data and medical guidelines
- **Genomic Profiling**: Analysis and integration of genomic data for precision medicine
- **Histopathology Analysis**: Automated analysis of pathology reports
- **Evidence-Based References**: RAG (Retrieval-Augmented Generation) system for medical evidence integration
- **Clinical Decision Support**: AI services for toxicity prediction and treatment recommendations
- **Patient Portal**: Secure patient access to medical records and treatment information
- **Authentication & KYC**: Doctor verification, patient authentication, and medical record management
- **QR Code Management**: Secure QR code generation for patient records and scan logging

## 🏗️ System Architecture

### Core Applications

#### 1. **Authentication** (`authentication/`)
Handles user management, authentication, and doctor verification
- User type distinction (Patient/Doctor)
- Doctor KYC (Know Your Customer) verification process
- Patient and Doctor profiles with medical credentials
- QR code generation and management for patient records
- Supabase integration for OAuth/authentication
- Medical record upload and management

**Key Features:**
- User registration and login
- Role-based access control
- Doctor verification workflow
- Patient profile management with emergency contacts and medical history
- QR code generation for patient identification

#### 2. **Cancer Detection** (`cancer_detection/`)
Core ML and analysis engine for cancer detection and treatment planning
- **CancerImageAnalysis**: Processes medical images (CT, MRI, X-ray, etc.)
- **PersonalizedTreatmentPlan**: Generates AI-powered treatment recommendations
- **HistopathologyReport**: Analyzes pathology data
- **GenomicProfile**: Stores and processes genomic information
- **TreatmentOutcome**: Tracks and predicts treatment outcomes

**Key Analyzers:**
- `opencv_analyzer.py`: Image processing and feature extraction
- `ml_analyzer.py`: Traditional ML-based cancer detection
- `groq_analyzer.py`: LLM-powered analysis using Groq API
- `histopathology_analyzer.py`: Pathology report processing
- `genomics_analyzer.py`: Genomic data analysis
- `outcome_predictor.py`: Treatment outcome prediction
- `treatment_planner.py`: Treatment planning engine
- `evidence_retriever.py` & `evidence_ingester.py`: Evidence-based medical references

#### 3. **Clinical Decision Support** (`clinical_decision_support/`)
AI-powered clinical decision-making assistance
- Toxicity prediction for drug combinations
- Treatment recommendations based on patient profiles
- Evidence-based medical guidelines integration
- REST API for clinical decision queries

**Key Services:**
- `ai_services.py`: Core AI/ML decision support logic
- `toxicity_service.py`: Drug toxicity and interaction predictions

#### 4. **Patient Portal** (`patient_portal/`)
User-facing interface for patients to manage their care
- Personal health records access
- Treatment plan viewing and updates
- Medical appointments and communication
- Secure document access

## 🚀 Getting Started

### Prerequisites

- Python 3.8+
- PostgreSQL or SQLite (for development)
- pip or conda package manager
- FFmpeg (for video processing, if needed)
- Tesseract OCR (for document text extraction)

### Installation

1. **Clone the Repository**
   ```bash
   git clone <repository-url>
   cd Cancer
   ```

2. **Create Virtual Environment**
   ```bash
   python -m venv "example env"
   "example env\Scripts\activate"  # On Windows
   # source example\ env/bin/activate  # On macOS/Linux
   ```

3. **Install Dependencies**
   ```bash
   pip install -r requirements.txt
   ```

4. **Environment Configuration**
   Create a `.env` file in the project root:
   ```env
   # Django Settings
   SECRET_KEY=your-secret-key-here
   DEBUG=True
   ALLOWED_HOSTS=localhost,127.0.0.1

   # Database Configuration
   DB_ENGINE=django.db.backends.postgresql
   DB_NAME=cancer_db
   DB_USER=postgres
   DB_PASSWORD=your-password
   DB_HOST=localhost
   DB_PORT=5432

   # Supabase Configuration
   SUPABASE_URL=https://your-project.supabase.co
   SUPABASE_ANON_KEY=your-anon-key
   SUPABASE_SERVICE_KEY=your-service-key

   # Groq API (for LLM analysis)
   GROQ_API_KEY=your-groq-api-key

   # AI Services
   OPENAI_API_KEY=your-openai-key  # If using OpenAI
   ```

5. **Database Migrations**
   ```bash
   python manage.py makemigrations
   python manage.py migrate
   ```

6. **Create Superuser**
   ```bash
   python manage.py createsuperuser
   ```

7. **Collect Static Files** (for production)
   ```bash
   python manage.py collectstatic --noinput
   ```

8. **Run Development Server**
   ```bash
   python manage.py runserver
   ```

   Access the application at `http://localhost:8000`

## 📦 Key Dependencies

### Core Framework
- **Django 6.0**: Web framework
- **Django REST Framework 3.14.0**: API framework

### Machine Learning & Image Processing
- **YOLOv8 (Ultralytics 8.3.237)**: Real-time object detection for cancer lesions
- **OpenCV 4.12.0.88**: Image processing and analysis
- **scikit-learn 1.8.0**: Traditional ML algorithms
- **PyTorch 2.9.1 & torchvision 0.24.1**: Deep learning framework
- **PyTesseract**: OCR for document processing

### Data Processing
- **Polars 1.36.1**: Fast data manipulation
- **Pandas-compatible**: Data analysis
- **NumPy 2.2.6**: Numerical computing
- **SciPy 1.16.3**: Scientific computing

### Database & Authentication
- **Supabase 2.25.0**: Backend as a Service for auth and database
- **psycopg2-binary 2.9.11**: PostgreSQL adapter
- **PyJWT 2.10.1**: JWT token handling

### AI & LLM Integration
- **Groq 0.15.0**: LLM API for advanced analysis
- **sentence-transformers 3.0.1**: Semantic search and embeddings

### PDF & Document Processing
- **PyPDF2 3.0.1**: PDF manipulation
- **pdf2image 1.17.0**: PDF to image conversion
- **python-docx 1.1.2**: Microsoft Word document handling

### QR Code & Security
- **qrcode 8.2**: QR code generation
- **pycryptodome 3.23.0**: Cryptographic operations

### Visualization
- **Matplotlib 3.10.8**: Data visualization
- **Pillow 12.0.0**: Image processing library

## 📊 Database Schema Overview

### Authentication Models
- **User**: Extended Django User with user_type and Supabase integration
- **PatientProfile**: Patient demographics and medical history
- **DoctorProfile**: Doctor credentials, specialization, and KYC status
- **PatientQRCode**: QR codes linked to patient records
- **QRCodeScanLog**: Audit trail of QR code scans
- **MedicalRecord**: Patient medical documents and records
- **DoctorKYC**: Doctor verification and credentialing

### Cancer Detection Models
- **CancerImageAnalysis**: Medical image uploads and analysis results
- **PersonalizedTreatmentPlan**: AI-generated treatment recommendations
- **HistopathologyReport**: Pathology findings and analysis
- **GenomicProfile**: Genomic sequencing and mutation data
- **TreatmentOutcome**: Treatment results and patient outcomes

## 🔧 API Endpoints

### Cancer Detection
- `POST /cancer/upload/`: Upload medical image for analysis
- `GET /cancer/analysis/<id>/`: Retrieve analysis results
- `POST /cancer/treatment-plan/`: Generate personalized treatment plan
- `GET /cancer/outcomes/`: View treatment outcomes

### Clinical Decision Support
- `POST /clinical/toxicity-prediction/`: Predict drug toxicity
- `POST /clinical/treatment-recommendations/`: Get treatment recommendations

### Authentication
- `POST /auth/register/`: Register new user
- `POST /auth/login/`: Authenticate user
- `POST /auth/doctor-kyc/`: Submit doctor verification
- `POST /auth/generate-qr/`: Generate patient QR code

## 🔐 Security Features

- **Role-Based Access Control (RBAC)**: Different access levels for patients and doctors
- **Supabase Authentication**: Secure OAuth and JWT-based authentication
- **Database Encryption**: Patient data encryption at rest
- **QR Code Verification**: Secure patient identification
- **HTTPS/SSL Ready**: Security middleware configured
- **CSRF Protection**: Django CSRF middleware enabled
- **SQL Injection Prevention**: ORM-based queries with parameterized statements

## 📁 Project Structure

```
Cancer/
├── manage.py                          # Django management script
├── requirements.txt                   # Python dependencies
├── README.md                          # This file
├── yolov8n.pt                         # YOLOv8 nano model weights
│
├── cancer_treatment_system/           # Main Django project settings
│   ├── settings.py                    # Django configuration
│   ├── urls.py                        # URL routing
│   ├── wsgi.py                        # WSGI application
│   └── asgi.py                        # ASGI application
│
├── authentication/                    # User auth and doctor KYC
│   ├── models.py                      # User, Profile models
│   ├── views.py                       # Authentication views
│   ├── urls.py                        # Auth URL routes
│   ├── forms.py                       # Registration/Login forms
│   ├── qr_utils.py                    # QR code utilities
│   ├── supabase_client.py             # Supabase integration
│   └── templates/                     # Auth templates
│
├── cancer_detection/                  # ML analysis engine
│   ├── models.py                      # Analysis models
│   ├── views.py                       # Analysis views
│   ├── urls.py                        # Cancer detection routes
│   ├── opencv_analyzer.py             # Image analysis
│   ├── ml_analyzer.py                 # ML models
│   ├── groq_analyzer.py               # LLM analysis
│   ├── histopathology_analyzer.py     # Pathology analysis
│   ├── genomics_analyzer.py           # Genomic analysis
│   ├── treatment_planner.py           # Treatment planning
│   ├── outcome_predictor.py           # Outcome prediction
│   ├── evidence_retriever.py          # Medical evidence RAG
│   ├── evidence_ingester.py           # Evidence ingestion
│   ├── evidence_models.py             # Evidence storage models
│   └── templates/                     # Analysis templates
│
├── clinical_decision_support/        # Clinical AI
│   ├── models.py                      # Decision support models
│   ├── views.py                       # Clinical views
│   ├── urls.py                        # Clinical routes
│   ├── ai_services.py                 # AI decision logic
│   ├── toxicity_service.py            # Toxicity prediction
│   └── templates/                     # Clinical templates
│
├── patient_portal/                    # Patient interface
│   ├── models.py                      # Portal models
│   ├── views.py                       # Portal views
│   ├── urls.py                        # Portal routes
│   └── templates/                     # Patient templates
│
├── templates/                         # Global templates
│   ├── base.html                      # Base template
│   └── partials/                      # Reusable components
│
├── static/                            # CSS, JS, images
│   ├── css/
│   ├── js/
│   └── images/
│
├── media/                             # User-uploaded content
│   ├── cancer_images/
│   ├── histopathology_reports/
│   ├── kyc/
│   ├── medical_records/
│   └── patient_qr_codes/
```

## 🧪 Testing

Run tests for all applications:
```bash
python manage.py test
```

Run tests for specific app:
```bash
python manage.py test authentication
python manage.py test cancer_detection
python manage.py test clinical_decision_support
```

Run with verbose output:
```bash
python manage.py test --verbosity=2
```

## 📈 Workflow

### Patient Journey
1. Patient registers in the system
2. Uploads medical images or documents
3. System performs automated analysis
4. AI generates personalized treatment plan
5. Patient reviews recommendations in portal
6. Doctor approves and initiates treatment
7. Outcomes tracked and updated

### Doctor Workflow
1. Doctor registers and completes KYC verification
2. Accesses patient records and analysis results
3. Reviews AI-generated treatment recommendations
4. Creates clinical notes and treatment plans
5. Tracks patient outcomes and adjusts treatment
6. Generates reports and documentation

## 🚀 Deployment

### Development
```bash
python manage.py runserver
```

### Production
1. Update settings for production security
2. Configure allowed hosts and static files
3. Use a production WSGI server (Gunicorn):
   ```bash
   gunicorn cancer_treatment_system.wsgi:application
   ```
4. Configure reverse proxy (Nginx/Apache)
5. Set up HTTPS/SSL certificates
6. Configure environment variables securely
7. Use a production-grade database (PostgreSQL)

## 🔄 Key Features Explained

### Intelligent Image Analysis
- Accepts multiple image formats (JPEG, PNG, BMP, TIFF)
- Uses YOLOv8 for real-time lesion detection
- OpenCV-based feature extraction
- Automatic image preprocessing and augmentation

### AI-Powered Treatment Planning
- Analyzes patient demographics, medical history, and genetics
- Cross-references evidence-based medical guidelines
- Generates personalized treatment options using Groq LLM
- Considers drug interactions and toxicity predictions

### Evidence Integration
- RAG-based medical reference retrieval
- Semantic search using sentence transformers
- Support for PDF, DOCX, and text evidence sources
- Evidence traceability and citation tracking

### Outcome Prediction
- ML models trained on historical treatment data
- Predicts treatment success rates
- Identifies risk factors and complications
- Supports clinical decision-making

## 📝 Migrations

Database migrations are tracked in `*/migrations/` directories. Apply migrations:
```bash
python manage.py migrate
```

Create new migrations after model changes:
```bash
python manage.py makemigrations
python manage.py migrate
```

## 🤝 Contributing

1. Create a feature branch
2. Make your changes
3. Run tests to ensure functionality
4. Commit with clear messages
5. Push and create a pull request

## 📞 Support

For issues, questions, or contributions:
- Review documentation in this README
- Check Django and specific package documentation
- Review application-specific code comments
- Check model docstrings in `models.py` files

## 📋 Environment Checklist

Before deploying:
- [ ] Environment variables configured in `.env`
- [ ] Database migrations applied
- [ ] Superuser created
- [ ] Static files collected
- [ ] Media directories writable
- [ ] Supabase credentials valid
- [ ] Groq API key configured
- [ ] YOLOv8 model weights present
- [ ] HTTPS certificates installed
- [ ] Backup strategy in place

## 🔗 External Services

- **Supabase**: Authentication, real-time database, storage
- **Groq**: LLM API for advanced analysis
- **YOLOv8/Ultralytics**: Pre-trained computer vision models

## 📚 Documentation

- [Django Documentation](https://docs.djangoproject.com/)
- [Django REST Framework](https://www.django-rest-framework.org/)
- [YOLOv8 Documentation](https://docs.ultralytics.com/)
- [Supabase Documentation](https://supabase.com/docs)
- [Groq API Documentation](https://groq.com/docs)

## 📄 License

[Include your license information here]

## 👥 Team

[Include team information here]

---

**Last Updated**: January 2026
**Version**: 1.0.0
