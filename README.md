# Medical Appointment & Pharmacy Management System

This project contains two Windows Forms applications for managing medical appointments and pharmacy inventory, both connecting to SQL Server databases using ADO.NET.

## Prerequisites

### Software Requirements
- **Visual Studio 2019 or later** (Community, Professional, or Enterprise)
- **SQL Server 2019 or later** (Express, Developer, or Standard)
- **SQL Server Management Studio (SSMS)** - for database management
- **.NET Framework 4.7.2 or later** or **.NET Core 3.1/.NET 5+**

### NuGet Packages to Install
1. **System.Data.SqlClient** (for .NET Framework) or **Microsoft.Data.SqlClient** (for .NET Core/5+)
2. **System.Configuration.ConfigurationManager** (if using .NET Core/5+)

### Installation Commands
In Visual Studio Package Manager Console:
```
Install-Package System.Data.SqlClient
Install-Package System.Configuration.ConfigurationManager
```

## Project Structure

```
Solution/
├── MedicalAppointmentSystem/
│   ├── Forms/
│   │   ├── MainForm.cs
│   │   ├── DoctorListForm.cs
│   │   ├── AppointmentForm.cs
│   │   └── ManageAppointmentsForm.cs
│   ├── App.config
│   └── Program.cs
├── PharmacyManagementSystem/
│   ├── Forms/
│   │   └── MainForm.cs
│   ├── App.config
│   └── Program.cs
├── DatabaseScripts/
│   ├── MedicalDB_Setup.sql
│   └── PharmacyDB_Setup.sql
└── README.md
```

## Task 1: Medical Appointment Booking System

### Features
- **MainForm**: Landing page with navigation buttons
- **DoctorListForm**: Displays all available doctors in a DataGridView
- **AppointmentForm**: Allows patients to book appointments
- **ManageAppointmentsForm**: View, update, or delete existing appointments

### Database Tables
1. **Doctors**: DoctorID, FullName, Specialty, Availability
2. **Patients**: PatientID, FullName, Email
3. **Appointments**: AppointmentID, DoctorID, PatientID, AppointmentDate, Notes

### Key Technologies Used
- **ADO.NET**: SqlConnection, SqlCommand, SqlDataReader, SqlDataAdapter, DataSet
- **Windows Forms**: DataGridView, TextBox, ComboBox, Button, DateTimePicker
- **Event Handling**: Click, SelectedIndexChanged, TextChanged events
- **Parameterized Queries**: Protection against SQL injection
- **Exception Handling**: Try-catch blocks with user-friendly error messages

## Task 2: Pharmacy Management System

### Features
- **Add Medicine**: Insert new medicines into inventory
- **Search Medicine**: Find medicines by name or category
- **Update Stock**: Modify quantity levels
- **Record Sale**: Process medicine purchases
- **View All**: Display complete medicine inventory

### Database Tables
1. **Medicines**: MedicineID, Name, Category, Price, Quantity
2. **Sales**: SaleID, MedicineID, QuantitySold, SaleDate

### Stored Procedures
- `AddMedicine(@Name, @Category, @Price, @Quantity)`
- `SearchMedicine(@SearchTerm)`
- `UpdateStock(@MedicineID, @Quantity)`
- `RecordSale(@MedicineID, @QuantitySold)`
- `GetAllMedicines()`

### Key Technologies Used
- **Stored Procedures**: All database operations use stored procedures
- **SqlCommand**: CommandType.StoredProcedure
- **Execution Methods**: ExecuteNonQuery(), ExecuteReader(), ExecuteScalar()
- **Partial Classes**: Separation of UI and business logic
- **Event Delegates**: Button click event handlers

## Setup Instructions

### 1. Database Setup
1. Open SQL Server Management Studio
2. Connect to your SQL Server instance
3. Execute the scripts in this order:
   - `DatabaseScripts/MedicalDB_Setup.sql`
   - `DatabaseScripts/PharmacyDB_Setup.sql`

### 2. Connection String Configuration
Update the connection strings in both App.config files:

```xml
<connectionStrings>
    <add name="MedicalDB" 
         connectionString="Data Source=YOUR_SERVER;Initial Catalog=MedicalDB;Integrated Security=True" />
    <add name="PharmacyDB" 
         connectionString="Data Source=YOUR_SERVER;Initial Catalog=PharmacyDB;Integrated Security=True" />
</connectionStrings>
```

Replace `YOUR_SERVER` with:
- `localhost` or `(local)` for local installations
- `.\SQLEXPRESS` for SQL Server Express
- Your specific server name/IP

### 3. Visual Studio Setup
1. Create a new Windows Forms App (.NET Framework) solution
2. Add both projects to the solution
3. Install the required NuGet packages
4. Copy the provided source code files
5. Build and run each project

## Running the Applications

### Medical Appointment System
1. Start with MainForm - provides navigation to all features
2. View doctors in DoctorListForm
3. Book appointments through AppointmentForm
4. Manage existing appointments in ManageAppointmentsForm

### Pharmacy Management System
1. Launch the main form
2. Add medicines to build inventory
3. Search and filter medicines
4. Update stock levels as needed
5. Record sales transactions
6. View complete inventory in the DataGridView

## Error Handling
Both applications include comprehensive error handling:
- Database connection failures
- SQL execution errors
- Data validation errors
- User-friendly error messages via MessageBox

## Security Features
- **Parameterized Queries**: Prevents SQL injection attacks
- **Input Validation**: Ensures data integrity
- **Connection Management**: Proper opening/closing of database connections
- **Exception Handling**: Graceful error recovery

## Sample Data
Both database setup scripts include sample data:
- **Medical System**: Sample doctors and patients
- **Pharmacy System**: Sample medicines and initial inventory

## Troubleshooting

### Common Issues
1. **Connection String Errors**: Verify server name and database existence
2. **Package Not Found**: Ensure NuGet packages are properly installed
3. **Database Access**: Check SQL Server authentication and permissions
4. **Form Design**: Ensure all controls have proper names and event handlers

### Debug Tips
- Check the Output window for compilation errors
- Use breakpoints to debug database operations
- Verify stored procedures exist in the database
- Test connection strings in SSMS first

## Additional Notes
- Both applications use partial classes for better code organization
- Event handlers are implemented using delegates
- All database operations are wrapped in try-catch blocks
- DataGridView controls provide rich data display and interaction
- Forms are designed with intuitive user interfaces

## Support
If you encounter issues:
1. Check connection strings match your SQL Server setup
2. Verify all NuGet packages are installed
3. Ensure database scripts ran successfully
4. Review error messages in MessageBox dialogs
