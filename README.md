# 🌴 GO CEYLON TRAVELS – PROFESSIONAL TOURISM WEB APPLICATION

> **Main Tagline**: EXPLORE SRI LANKA. EXPERIENCE PARADISE.  
> **Brand Name**: GO CEYLON TRAVELS

A modern, luxury, fully responsive tourism web application built with **Java Spring Boot**, **HTML5**, **CSS3**, **JavaScript**, **Maven**, and **MySQL**.

---

## 📸 Website Overview & Pages

The application showcases the beauty of Sri Lanka and provides end-to-end travel booking inquiry capabilities:

1. **Page 01 – Home Page (`index.html`)**
   - Full-screen cinematic Sri Lankan hero banner with gold accents
   - Quick Booking Search bar (Destination, Start Date, Guests, Tour Type)
   - Welcome Section highlighting tailor-made private tours
   - Popular Tour Packages (Cultural, Safari, Coast, Hill Country, Round Island, Adventure)
   - Why Choose Us (6 core pillars)
   - Featured Destinations (Sigiriya, Ella, Mirissa, Kandy, Yala, Galle)
   - Live Stats Counter & Call-to-Action banner
   - Modern luxury footer with links, contacts, and social links

2. **Page 02 – Tours Page (`tours.html`)**
   - 8 Tour Categories with instant filter chips:
     1. Cultural and Heritage Tours
     2. Wildlife and Safari Tours
     3. Beach and Coastal Tours
     4. Hill Country Tours
     5. Adventure Tours
     6. Family Tours
     7. Honeymoon Tours
     8. Round Island Tours
   - Search bar and duration filter
   - Rich interactive tour cards with highlights and duration badges
   - Comprehensive Tour Details Modal featuring day-by-day itineraries
   - One-click "Book This Tour" button pre-populating booking form

3. **Page 03 – Sri Lanka Attractions (`attractions.html`)**
   - Filterable tabs across 22+ iconic destinations:
     - **Cultural & Historical**: Sigiriya Rock, Temple of the Tooth Kandy, Dambulla Cave, Anuradhapura, Polonnaruwa, Galle Dutch Fort
     - **Nature & Hill Country**: Ella, Nine Arch Bridge, Little Adam's Peak, Nuwara Eliya, Horton Plains & World's End, Knuckles Range
     - **Beach Destinations**: Mirissa, Unawatuna, Bentota, Arugam Bay, Hiriketiya, Hikkaduwa
     - **Wildlife Sanctuaries**: Yala National Park, Udawalawe National Park, Minneriya Elephant Gathering, Wilpattu National Park
   - Interactive detail modal with visiting seasons and "Add to Custom Tour" button

4. **Page 04 – About Us (`about.html`)**
   - Company heritage and 15+ years story
   - Mission & Vision
   - Professional Travel Services
   - Trust and sustainability pledge

5. **Page 05 – Contact Us (`contact.html`)**
   - Office Address: Go Ceylon Travels, Palathota Road, Kalutara, Sri Lanka.
   - Direct Hotline: +94 77 761 3691
   - WhatsApp Support: +94 77 761 3691 (https://wa.me/94777613691)
   - Email: goceylon.travels@gmail.com
   - Interactive Google Maps embed focused on Palathota Road, Kalutara
   - Working contact form with validation and persistence

6. **Dedicated Tour Booking System (`booking.html` & Universal Modal)**
   - All 11 required fields validated:
     1. Full Name
     2. Email Address
     3. WhatsApp / Contact Number
     4. Country
     5. Select Tour Package
     6. Preferred Travel Date
     7. Number of Adults
     8. Number of Children
     9. Number of Days
     10. Pickup Location
     11. Special Requirements / Message
   - Generates unique reference number format: `GCT-2026-XXXXX`
   - Real-time confirmation modal with WhatsApp follow-up link

7. **Admin Management Portal (`admin.html`)**
   - Review all submitted inquiries
   - Filter by status (`PENDING`, `CONTACTED`, `CONFIRMED`, `CANCELLED`)
   - Search by Reference Code, Guest Name, Email, or Country
   - Live status update via REST API
   - Contact messages inbox management
   - Real-time KPI stats cards

---

## 🛠️ Technology Stack

| Layer | Technology |
|---|---|
| **Backend** | Java 17+, Spring Boot 3.2.x, Spring Data JPA, Hibernate Validator |
| **Frontend** | HTML5, CSS3, JavaScript (Vanilla ES6+), Google Fonts (Cinzel, Outfit, Plus Jakarta Sans) |
| **Database** | MySQL 8.0+ (Production) / H2 Embedded (Zero-config development) |
| **Build Tool** | Apache Maven 3.8+ / Maven Wrapper (`mvnw`) |

---

## 🚀 How to Run the Application

### Option 1: Running with Spring Boot & Maven

1. **Prerequisites**: Ensure Java JDK 17+ and Maven are installed.
2. Open a terminal in the project directory:
   ```bash
   cd "d:\DO NOT TOUCH\Kirul DO NOT TOUCH\My\Web\Go Ceylon"
   ```
3. Run the Spring Boot application:
   ```bash
   mvn spring-boot:run
   ```
4. Access the web application:
   - **Main Website**: [http://localhost:8080/](http://localhost:8080/)
   - **Tours**: [http://localhost:8080/tours.html](http://localhost:8080/tours.html)
   - **Attractions**: [http://localhost:8080/attractions.html](http://localhost:8080/attractions.html)
   - **About Us**: [http://localhost:8080/about.html](http://localhost:8080/about.html)
   - **Contact Us**: [http://localhost:8080/contact.html](http://localhost:8080/contact.html)
   - **Booking Inquiry**: [http://localhost:8080/booking.html](http://localhost:8080/booking.html)
   - **Admin Management Portal**: [http://localhost:8080/admin.html](http://localhost:8080/admin.html)
   - **H2 Developer Console**: [http://localhost:8080/h2-console](http://localhost:8080/h2-console) (JDBC URL: `jdbc:h2:file:./data/goceylon_db`, User: `sa`, Password: empty)

---

### Option 2: Running with MySQL Database

1. Create the MySQL database and tables by running the SQL script located in:
   ```
   src/main/resources/schema-mysql.sql
   ```
   Or execute:
   ```sql
   CREATE DATABASE IF NOT EXISTS go_ceylon_db CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci;
   ```
2. In `src/main/resources/application.properties` (or using `--spring.profiles.active=mysql`), set your MySQL username and password:
   ```properties
   spring.datasource.url=jdbc:mysql://localhost:3306/go_ceylon_db?createDatabaseIfNotExist=true&useSSL=false&serverTimezone=Asia/Colombo
   spring.datasource.username=root
   spring.datasource.password=your_password
   ```
3. Run Spring Boot:
   ```bash
   mvn spring-boot:run -Dspring-boot.run.profiles=mysql
   ```

---

### Option 3: Instant Browser Preview (Zero-Install Mode)

You can directly double-click `index.html` in Windows Explorer or open it in any browser!
The frontend features an intelligent client-side persistence layer with local storage:
- It attempts to communicate with the Spring Boot backend (`/api/bookings`, `/api/contact`, etc.).
- If the backend is active, inquiries persist straight into the MySQL database.
- If opened directly from disk without Spring Boot running, it seamlessly stores submissions in browser storage, generates the authentic `GCT-2026-XXXXX` reference code, and displays the confirmation popup and admin records without throwing errors!

---

## 📡 REST API Endpoints

| Method | Endpoint | Description |
|---|---|---|
| `POST` | `/api/bookings` | Submit new booking inquiry (generates `GCT-2026-XXXXX` ref) |
| `GET` | `/api/bookings` | Retrieve all booking inquiries (supports `?status=PENDING`) |
| `GET` | `/api/bookings/{ref}` | Get booking details by reference code |
| `PATCH`| `/api/bookings/{id}/status` | Update booking status (`PENDING`, `CONTACTED`, `CONFIRMED`, `CANCELLED`) |
| `POST` | `/api/contact` | Submit contact message |
| `GET` | `/api/contact` | Retrieve all contact messages |
| `PATCH`| `/api/contact/{id}/status` | Update message status (`NEW`, `READ`, `REPLIED`) |
| `GET` | `/api/tours` | List all tours (supports `?category=...&search=...`) |
| `GET` | `/api/tours/{id}` | Get single tour package details and itinerary |
| `GET` | `/api/attractions` | List all 22+ attractions |
| `GET` | `/api/stats` | Dashboard KPI summary statistics |

---

## 📁 Project Structure

```
Go Ceylon/
├── pom.xml                                  # Maven project configuration & dependencies
├── mvnw & mvnw.cmd                          # Maven wrapper executables
├── index.html                               # Page 01: Home Page
├── tours.html                               # Page 02: Tours Page
├── attractions.html                         # Page 03: Sri Lanka Attractions
├── about.html                               # Page 04: About Us
├── contact.html                             # Page 05: Contact Us
├── booking.html                             # Dedicated Tour Booking Page
├── admin.html                               # Admin Management Portal
├── css/
│   ├── styles.css                           # Core Luxury Design System & Components
│   └── responsive.css                       # Responsive Breakpoints (Desktop, Tablet, Mobile)
├── js/
│   ├── main.js                              # Header state, mobile drawer, modals, toast alerts
│   ├── animations.js                        # Scroll reveals & animated counters
│   ├── tours.js                             # Tours catalog, filter chips, search & itinerary modal
│   ├── attractions.js                       # 22+ Attractions catalog & modal details
│   ├── booking.js                           # 11-field form validation & reference generator
│   ├── contact.js                           # Contact form handler & DB connector
│   └── admin.js                             # Admin management dashboard controller
└── src/
    └── main/
        ├── java/com/goceylon/travels/
        │   ├── GoCeylonTravelsApplication.java
        │   ├── config/WebMvcConfig.java
        │   ├── controller/
        │   │   ├── BookingController.java
        │   │   ├── ContactController.java
        │   │   ├── TourController.java
        │   │   ├── AttractionController.java
        │   │   └── AdminStatsController.java
        │   ├── model/
        │   │   ├── BookingInquiry.java
        │   │   ├── ContactMessage.java
        │   │   ├── TourPackage.java
        │   │   └── Attraction.java
        │   ├── repository/
        │   │   ├── BookingRepository.java
        │   │   └── ContactMessageRepository.java
        │   ├── service/
        │   │   ├── BookingService.java
        │   │   ├── ContactService.java
        │   │   ├── TourService.java
        │   │   └── AttractionService.java
        │   └── dto/
        │       ├── BookingRequest.java
        │       ├── BookingResponse.java
        │       ├── ContactRequest.java
        │       └── ApiResponse.java
        └── resources/
            ├── application.properties
            ├── application-mysql.properties
            ├── schema-mysql.sql
            ├── data.sql
            └── static/                      # Static resources served by Spring Boot
```

---

## 🎨 Design Philosophy
- **Colors**: Ocean Navy (`#0e2444`), Deep Forest (`#064e3b`), Ceylon Sunburst Gold (`#f59e0b`), Pure White & Sand Off-whites.
- **Typography**: Cinzel (Luxury Display Serif), Outfit (Modern Geometric Headings), Plus Jakarta Sans (Crisp Body).
- **Interactions**: Subtle glassmorphism, image hover zoom, smooth scroll reveals, animated number counters, and responsive mobile sliding drawer.
