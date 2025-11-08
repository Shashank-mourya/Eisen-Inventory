# Eisen Inventory Management System

A modern, full-stack inventory management system with real-time alerts, reporting, and data import capabilities.

## 🚀 Features

### ✅ Complete Features
- **Dashboard**: Real-time stats, quick actions, recent alerts
- **Product Management**: Full CRUD with search and filtering
- **Supplier Management**: Track suppliers with contact details
- **Stock Alerts**: Automated alerts when stock falls below minimum levels
- **Reports**: Monthly and yearly stock analytics
- **Data Upload**: Import inventory from Excel/CSV files
- **Admin Panel**: Django admin interface for advanced management
- **User Authentication**: Login/logout system with user management
- **Navigation**: Back button and accessible menu on all pages

### 🎨 UI/UX Features
- Modern glassmorphism design
- GSAP animations
- Responsive layout
- Staggered menu with smooth transitions
- Loading states and error handling
- Toast notifications

## 🛠️ Technology Stack

### Backend
- **Django 4.2.7**: Web framework
- **Django REST Framework**: API endpoints
- **SQLite**: Database (development)
- **openpyxl**: Excel file processing
- **django-cors-headers**: CORS handling

### Frontend
- **React 18**: UI library
- **React Router**: Navigation
- **Vite 5.4.21**: Build tool
- **GSAP 3.12.5**: Animations
- **Axios**: HTTP client

## 📦 Installation & Setup

### Prerequisites
- Python 3.8+
- Node.js 16+
- npm or yarn

### Backend Setup

1. **Navigate to backend directory**:
   ```bash
   cd "X:\CODES\Eisen Inventory\eisen_inventory"
   ```

2. **Install Python dependencies**:
   ```bash
   pip install -r requirements.txt
   ```

3. **Run migrations**:
   ```bash
   python manage.py migrate
   ```

4. **Create sample data** (optional):
   ```bash
   python manage.py create_sample_data
   ```

5. **Create superuser**:
   ```bash
   python manage.py createsuperuser
   ```
   Or use the quick setup:
   - Username: `admin`
   - Password: `admin123`

6. **Start Django server**:
   ```bash
   python manage.py runserver
   ```

### Frontend Setup

1. **Navigate to frontend directory**:
   ```bash
   cd "X:\CODES\Eisen Inventory\frontend"
   ```

2. **Install Node dependencies**:
   ```bash
   npm install
   ```

3. **Build frontend**:
   ```bash
   npm run build
   ```

### Access the Application

- **Main Application**: http://127.0.0.1:8000/
- **Admin Panel**: http://127.0.0.1:8000/admin
- **API Root**: http://127.0.0.1:8000/api/

## 👤 Default Credentials

### Superuser
- **Username**: `admin`
- **Password**: `admin123`

## 📊 Sample Data

The system includes a management command to create sample data:

```bash
python manage.py create_sample_data
```

This creates:
- 3 Suppliers (Acme Metals Inc., Global Supplies Ltd, TechParts Corp)
- 10 Products with varying stock levels
- 4 Active stock alerts
- 5 Supplier-product relationships

## 📁 Data Import

### Upload CSV or Excel Files

1. Navigate to **Upload** page
2. Drag and drop or click to select file
3. Choose mode:
   - **Append**: Add new products, update existing
   - **Replace All**: Clear database and import fresh data

### CSV Format

Required columns:
```csv
sku,name,minimum_stock_level,current_stock
PROD-001,Product Name,50,100
```

A sample file is provided at: `X:\CODES\Eisen Inventory\sample_inventory.csv`

## 🗂️ Project Structure

```
Eisen Inventory/
├── eisen_inventory/          # Django backend
│   ├── eisen_inventory/      # Project settings
│   │   ├── settings.py       # Configuration
│   │   ├── urls.py          # Main URL routing
│   │   └── wsgi.py
│   ├── inventory/           # Main app
│   │   ├── models.py        # Database models
│   │   ├── serializers.py   # DRF serializers
│   │   ├── api_views.py     # API endpoints
│   │   ├── auth_views.py    # Authentication endpoints
│   │   ├── urls.py          # App URL routing
│   │   ├── utils.py         # Helper functions
│   │   ├── admin.py         # Admin configuration
│   │   └── management/
│   │       └── commands/    # Management commands
│   ├── db.sqlite3           # Database file
│   ├── manage.py            # Django CLI
│   └── requirements.txt     # Python dependencies
├── frontend/                # React frontend
│   ├── src/
│   │   ├── components/      # React components
│   │   │   ├── Layout.jsx   # Main layout with nav
│   │   │   ├── StaggeredMenu.jsx
│   │   │   └── SplitText.jsx
│   │   ├── pages/          # Page components
│   │   │   ├── Home.jsx    # Dashboard
│   │   │   ├── Products.jsx
│   │   │   ├── Suppliers.jsx
│   │   │   ├── Alerts.jsx
│   │   │   ├── Reports.jsx
│   │   │   ├── Upload.jsx
│   │   │   └── Login.jsx
│   │   ├── styles/         # CSS files
│   │   │   └── global.css
│   │   ├── utils/
│   │   │   └── axios.js    # Axios configuration
│   │   └── main.jsx        # App entry point
│   ├── dist/               # Built files (served by Django)
│   ├── package.json
│   └── vite.config.js
└── sample_inventory.csv    # Sample data file
```

## 🔌 API Endpoints

### Products
- `GET /api/products/` - List all products
- `POST /api/products/` - Create product
- `GET /api/products/{id}/` - Get product details
- `PUT /api/products/{id}/` - Update product
- `DELETE /api/products/{id}/` - Delete product

### Suppliers
- `GET /api/suppliers/` - List all suppliers
- `POST /api/suppliers/` - Create supplier
- `GET /api/suppliers/{id}/` - Get supplier details
- `PUT /api/suppliers/{id}/` - Update supplier
- `DELETE /api/suppliers/{id}/` - Delete supplier

### Stock Alerts
- `GET /api/stock-alerts/` - List all alerts
- `POST /api/stock-alerts/{id}/resolve/` - Resolve alert
- `POST /api/stock-alerts/evaluate/` - Evaluate all alerts

### Reports
- `GET /api/stock-snapshots/monthly/` - Monthly aggregates
- `GET /api/stock-snapshots/yearly/` - Yearly aggregates

### Upload
- `POST /api/uploads/upload_excel/` - Upload Excel file
- `POST /api/uploads/upload_csv/` - Upload CSV file

### Authentication
- `POST /api/auth/login/` - User login
- `POST /api/auth/logout/` - User logout
- `GET /api/auth/user/` - Get current user
- `POST /api/auth/register/` - Register new user

## 🎯 Navigation

### Header Controls
- **Back Button** (←): Navigate to previous page
- **Menu Button** (☰): Open navigation menu

### Menu Items
1. Dashboard
2. Products
3. Suppliers
4. Alerts
5. Reports
6. Upload
7. Admin Panel

## 🔧 Management Commands

```bash
# Create sample data
python manage.py create_sample_data

# Import from CSV
python manage.py import_inventory_csv path/to/file.csv

# Evaluate stock alerts
python manage.py evaluate_stock_alerts

# Create stock snapshot
python manage.py snapshot_stock_levels
```

## 🐛 Troubleshooting

### Server Issues
If the server won't start:
```bash
cd "X:\CODES\Eisen Inventory\eisen_inventory"
python manage.py runserver
```

### Frontend Not Updating
Rebuild the frontend:
```bash
cd "X:\CODES\Eisen Inventory\frontend"
npm run build
```

### Upload Not Working
- Ensure file is CSV or Excel format
- Check file has required columns: `sku`, `name`, `minimum_stock_level`, `current_stock`
- Verify server is running
- Check browser console for errors

### Login Issues
- Default credentials: admin / admin123
- Create new superuser: `python manage.py createsuperuser`
- Access admin panel: http://127.0.0.1:8000/admin

## 📝 Notes

### CSRF Protection
The application uses CSRF tokens for security. The axios configuration automatically handles this.

### CORS Configuration
CORS is enabled for http://127.0.0.1:8000 and http://localhost:8000 in development.

### Database
- Development uses SQLite (db.sqlite3)
- For production, configure PostgreSQL in settings.py

## 🚦 Quick Start

**One-command startup** (after initial setup):

```bash
cd "X:\CODES\Eisen Inventory\eisen_inventory" && python manage.py runserver
```

Then visit: **http://127.0.0.1:8000/**

## 📞 Support

For issues or questions:
1. Check the troubleshooting section
2. Review the Django admin panel logs
3. Check browser console for frontend errors
4. Review terminal output for backend errors

## 🎉 All Features Working

✅ Dashboard with real-time stats  
✅ Product CRUD operations  
✅ Supplier management  
✅ Stock alerts system  
✅ Monthly/yearly reports  
✅ Excel/CSV data upload  
✅ User authentication  
✅ Back button navigation  
✅ Accessible menu on all pages  
✅ Admin panel integration  
✅ Modern, animated UI  
✅ Sample data included  

---

**Eisen Inventory** - Modern Inventory Management Made Simple
