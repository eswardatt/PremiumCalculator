# Premium Calculator – Angular + .NET 8

A simple insurance premium calculator that allows a user to enter personal details, choose an occupation, and automatically get the monthly premium calculated.

---

## 🧮 Business Requirement

The system calculates monthly premium using:

```
Premium = (Death Sum Insured * Rating Factor * Age) / 1000 * 12
```

Premium should update automatically when the user changes the occupation.

---

## 🖥️ Tech Stack

### Frontend
- Angular 16+
- Bootstrap UI
- HttpClient for API calls

### Backend
- .NET 8 Web API
- C#
- Dependency Injection

### Database
- ER model included (no scripts required)

---

# 📁 Project Structure

```
premium-calculator/
 ├─ frontend/     → Angular UI
 ├─ backend/      → .NET 8 Web API
 ├─ database/     → ER diagram + documentation
 └─ README.md
```

---

# 🚀 Features

✔ Automatic premium calculation  
✔ Occupation-driven factor mapping  
✔ All fields mandatory  
✔ REST API integration  
✔ Clean service-layer architecture  
✔ Angular form with live updates  

---

# 🔢 Occupation & Rating Factors

| Occupation | Rating |
|-----------|--------|
| Cleaner | Light Manual |
| Doctor | Professional |
| Author | White Collar |
| Farmer | Heavy Manual |
| Mechanic | Heavy Manual |
| Florist | Light Manual |
| Other | Heavy Manual |

### Rating Factor Table

| Rating | Factor |
|--------|--------|
| Professional | 1.5 |
| White Collar | 2.25 |
| Light Manual | 11.50 |
| Heavy Manual | 31.75 |

---

# 🛠️ Backend (.NET 8)

## Routes

### **GET** `/api/premium/occupations`
Returns occupation list.

### **POST** `/api/premium/calculate`
Body:
```json
{
  "name": "John",
  "ageNextBirthday": 30,
  "dob": "10/1991",
  "occupationId": 2,
  "deathSumInsured": 500000
}
```

Response:
```json
{
  "monthlyPremium": 27000
}
```

---

# 🎨 Frontend (Angular)

### Premium auto-calculates on occupation change  
Uses:
- `premium.component.ts`
- `premium.service.ts`
- Template-driven form

---

# 🗄 Database Design

### Table: Members
| Column | Type |
|--------|------|
| MemberId (PK) | int |
| Name | varchar |
| AgeNextBirthday | int |
| DOB | date |
| OccupationId | FK |
| DeathSumInsured | decimal |

### Table: Occupations
| Column | Type |
|--------|------|
| Id | int (PK) |
| Name | varchar |
| Rating | varchar (FK → Rating.RatingName) |

### Table: Rating
| Column | Type |
|--------|------|
| RatingName | varchar (PK) |
| Factor | decimal |

---

# 📌 Assumptions (Important for evaluation)

1. DOB stored as MM/YYYY per requirement.  
2. Age Next Birthday is directly taken from user input.  
3. Occupation list is static and seeded from service.  
4. No authentication required.  
5. API returns premium rounded to 2 decimals.  
6. Database scripts are not required as per instruction.  

---

# ✔ How to Run

## 1️⃣ Backend
```
cd backend/PremiumAPI
dotnet run
```
Runs at: `https://localhost:5001`

## 2️⃣ Frontend
```
cd frontend
npm install
ng serve
```
Runs at: `http://localhost:4200`

---

# 📬 Submission Instructions

- Commit early and often.
- Include all code in GitHub.
- Add link to repository when submitting.

---

# ❓ Questions / Clarifications

If you have any questions about implementation, business rules, or improvements, feel free to contact the reviewer.

---

# 👨‍💻 Developed by
Your Name  
GitHub Profile Link
