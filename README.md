<div align="center">
   
# 🍲 KulinerKita - Cloud Computing
## 🍴 KulinerKita (Team C242-PS155) - CC Repository
![Nodejs Badge](https://img.shields.io/badge/-Nodejs-3C873A?style=for-the-badge&labelColor=black&logo=node.js&logoColor=3C873A)
![Express](https://img.shields.io/badge/Express%20js-000000?style=for-the-badge&logo=express&logoColor=white)
![MySQL](https://img.shields.io/badge/MySQL-4479A1?style=for-the-badge&logo=mysql&logoColor=white)

</div>

<div align="justify">
   
**KulinerKita Cloud Computing Repository** for Bangkit Capstone Project. Building Scalable Cloud Infrastructure for a Culinary Platform with Serverless Functions and Cloud Databases.

## KulinerKita's Developer of Cloud Computing Bangkit Academy Capstone Team C242-PS155

<div align="center">
   
|            Member           | Student ID |        Path        |                    Role                    |                                                       Contacts                                                      |
| :-------------------------: | :--------: | :----------------: | :----------------------------------------: | :-----------------------------------------------------------------------------------------------------------------: |
| Dzaki Akmal Rabbani Alqadrie | C312B4KY1214  |  Cloud Computing  | Cloud Engineer |[dzakiakmal](https://github.com/dzakiakmal)|
| Fanes Arasadina          | C421B4KX1388 |  Cloud Computing  | Cloud Engineer | [fanesarasy](https://github.com/fanesarasy) |

</div>

---  

**KulinerKita** is a dynamic mobile app that helps users discover dining places. This section of the project focuses on the **Cloud Computing** aspect, which includes cloud infrastructure setup, database management, and server-side logic. Utilizing cloud services, it enhances the app's scalability, performance, and real-time features.

## Implementation Section:
- **Cloud Database Management**: Stores and manages data about dining places, categories, reviews, operating hours, and more.
- **APIs**: Enables communication between the mobile app and cloud resources, allowing for efficient search, filtering, and user interactions.
- **Scalability & Performance**: Uses cloud solutions to ensure the app can handle growing data and increasing numbers of users.

---

## Features

- **City and Subdistrict Search**: Filter restaurants by city or specific subdistrict.
- **Category-Based Search**: Find restaurants based on their category.
- **Eco-Friendly Options**: Search for restaurants that are environmentally friendly.
- **Weather Preferences**: Get recommendations for restaurants suitable for specific weather conditions.
- **Operating Hours**: Search restaurants open in the morning, afternoon, night, or operating 24 hours.
- **Ratings and Reviews**: Filter restaurants by minimum ratings and number of reviews.
- **Price Range**: Query restaurants within a specific price range.
- **Optimized Results**: Returns results with neatly formatted ratings and operating hours.

## Installation

1. Clone this repository:
   ```bash
   git clone https://github.com/kulinerkita/CC.git
   cd backend-v2
   ```

2. Initialize project and install dependencies:
   ```bash
   npm init -y
   npm install express mysql2
   ```

3. Set up the database connection:
   - Modify a `db.js` file in the project root with your own database connection configuration.

4. Start the server:
   ```bash
   node server.js
   ```

5. Access the API at:
   ```
   http://localhost:3000
   ```

## API Endpoints

### `GET /restaurants/search`

Search for restaurants based on various filters.

#### Query Parameters

| Parameter      | Type    | Description                                         |
|----------------|---------|-----------------------------------------------------|
| `city`         | String  | Filter by city.                                    |
| `subdistrict`  | String  | Filter by subdistrict ID.                          |
| `ecoFriendly`  | Boolean | Filter by eco-friendly status.                     |
| `weather`      | String  | Filter by weather category.                        |
| `categoryId`   | Number  | Filter by restaurant category ID.                  |
| `openingHours` | String  | Filter by operating hours (e.g., `Morning`, `24 hours`). |
| `minRating`    | Number  | Filter by minimum rating.                          |
| `minReviews`   | Number  | Filter by minimum number of reviews.               |
| `minPrice`     | Number  | Filter by minimum price.                           |
| `maxPrice`     | Number  | Filter by maximum price.                           |

#### Example Request
```bash
GET https://kulinerkita.et.r.appspot.com/restaurants/search?categoryId=6
```

#### Example Response
```json
[
  {
        "id": 246,
        "name": "Selat Solo Tenda Biru - Dr. Wahidin",
        "address": "Jl. Dr. Wahidin No.26, Purwosari, Kec. Laweyan, Kota Surakarta, Jawa Tengah 57142",
        "phone_number": "082136659775",
        "latitude": -7.5686559,
        "longitude": 110.8052207,
        "category_id": 6,
        "categorize_weather": "Dingin",
        "maps_url": "https://www.google.com/maps/place/Selat+Solo+Tenda+Biru+-+Dr.+Wahidin/@-7.5686559,110.8052207,764m/data=!3m2!1e3!4b1!4m6!3m5!1s0x2e7a15d40a61c385:0x97027f5ac68485d3!8m2!3d-7.5686559!4d110.8052207!16s%2Fg%2F11b6zv3lhm?authuser=0&entry=ttu&g_ep=EgoyMDI0MTExOS4yIKXMDSoASAFQAw%3D%3D",
        "min_price": 25000,
        "max_price": 50000,
        "kecamatan_id": 1,
        "eco_friendly": 0,
        "rating": "4.60",
        "reviews": 7090,
        "operating_hours": {
            "opening_time": "08:00:00",
            "closing_time": "21:00:00"
        }
   }
]
```

## Project Structure

```
backend-v2/
├── db.js              # Database connection configuration
├── server.js          # Main application server
└── package.json       # Node.js dependencies and scripts
```

## Technologies Used

- **Node.js**: JavaScript runtime for building scalable applications.
- **Express**: Web framework for Node.js.
- **Cloud SQL (MySQL)**: Relational database management system.
- **Google App Engine**: Deploying the application and APIs automatically.
- **Cloud Run**: Deploying the machine learning models.
- **Google Cloud Storage**: For storing image and media data. 

---

## **Database Schema**

The database schema consists of several tables that are interrelated to manage restaurant data, including information on categories, locations, ratings, and operational hours. Below is a breakdown of each table and its relationships.

## 1. `places` Table
This table stores information about restaurants or dining places.

### Key Columns:
- **id**: Primary key of the table.
- **category_id**: Foreign key referencing the `categories` table (indicating the restaurant's category).
- **kecamatan_id**: Foreign key referencing the `kecamatan` table (indicating the location of the restaurant).

### Relationships:
- **One-to-Many** with `categories`: A category can be associated with many restaurants.
- **One-to-Many** with `kecamatan`: A kecamatan (district) can have many restaurants.
- **One-to-Many** with `ratings`: A restaurant can have many ratings.
- **One-to-Many** with `operatinghours`: A restaurant can have multiple operating hours.

---

## 2. `categories` Table
This table stores information about food or restaurant categories, such as Food, Drinks, etc.

### Key Columns:
- **id**: Primary key of the table.
- **name**: Name of the category.

### Relationships:
- **One-to-Many** with `places`: A category can be used by many restaurants. This relationship is defined by the `category_id` in the `places` table.

---

## 3. `kecamatan` Table
This table stores data about districts (kecamatan).

### Key Columns:
- **id**: Primary key of the table.
- **name**: Name of the district.

### Relationships:
- **One-to-Many** with `places`: A district can have many restaurants. This relationship is defined by the `kecamatan_id` in the `places` table.

---

## 4. `ratings` Table
This table stores restaurant ratings and the number of reviews.

### Key Columns:
- **id**: Primary key of the table.
- **place_id**: Foreign key referencing the `places` table (indicating the restaurant being rated).
- **rating**: Rating value of the restaurant (decimal number).
- **reviews**: Number of reviews for the restaurant.

### Relationships:
- **Many-to-One** with `places`: Many ratings are associated with one restaurant.

---

## 5. `operatinghours` Table
This table stores the operating hours for each restaurant based on the day.

### Key Columns:
- **id**: Primary key of the table.
- **place_id**: Foreign key referencing the `places` table (indicating the restaurant).
- **day**: The operational day (Monday, Tuesday, etc.).
- **opening_time**: Opening time of the restaurant.
- **closing_time**: Closing time of the restaurant.

### Relationships:
- **Many-to-One** with `places`: Many operating hours are associated with one restaurant.

---

## Relationships Between Tables

- **`places`** is the central table:
  - It connects to the `categories` table through the `category_id`.
  - It connects to the `kecamatan` table through the `kecamatan_id`.
  - It connects to the `ratings` table through the `place_id`.
  - It connects to the `operatinghours` table through the `place_id`.

- **`categories`** serves as a reference for restaurant categories, used in the `places` table to categorize restaurants.
- **`kecamatan`** serves as a reference for the location of each restaurant, stored in the `places` table.
- **`ratings`** stores feedback on each restaurant and links to `places` via the `place_id`.
- **`operatinghours`** stores the operational hours of each restaurant and is connected to `places` via the `place_id`.

---

## Example Relational Diagram
places ↔ categories (1 category, many places) categories.id ↔ places.category_id

places ↔ kecamatan (1 kecamatan, many places) kecamatan.id ↔ places.kecamatan_id

places ↔ ratings (1 place, many ratings) places.id ↔ ratings.place_id

places ↔ operatinghours (1 place, many operating hours) places.id ↔ operatinghours.place_id

---

## **Deployment Steps**

### **1. Cloud SQL Database Setup**

1. Create a **Cloud SQL (MySQL)** instance in the GCP Console.
2. Create the database and tables based on the schema provided above.
3. Configure database access for the app deployed in App Engine or Cloud Functions.
   
### **2. API Deployment to Google App Engine**

1. Set up your application in Google App Engine, using an `app.yaml` file for configuration.
2. Deploy your application to **App Engine** using the GCP CLI:
   ```bash
   gcloud app deploy
   ```
   
### **3. Cloud Run Deployment for ML API**

1. Create a **Cloud Run** for the prediction API.
2. Deploy the function using the GCP CLI:
   ```bash
   gcloud run deploy predict --runtime python39 --trigger-http --allow-unauthenticated
   ```
---

## **How to Run Locally**

1. **Clone the Repository**
   Clone this repository to your local machine using the following command:
   ```bash
   git clone https://github.com/kulinerkita/CC.git
   cd ML-Backend-API
   ```

2. **Install Dependencies**
   Navigate to the project directory and install the required dependencies:
   ```bash
   pip install -r requirements.txt
   ```

3. **Set Up Database Connection**
   Configure the database connection to **Cloud SQL** by using the connection string provided by Google Cloud Platform (GCP). Ensure you have the correct permissions and access to the Cloud SQL instance.

4. **Run the Application Locally**
   Use the Flask CLI to start the application:
   ```bash
   flask --app app run
   ```
   The application will typically run on `http://127.0.0.1:5000` by default.

5. **Test the Endpoints**
   Use Postman or any API testing tool to test the application. Here is an example endpoint and payload:
   
   **Endpoint:**
   ```
   https://ml-model-predict-636814706436.asia-southeast2.run.app/predict
   ```

   **Request Payload:**
   ```json
   {
       "latitude": -7.579666911699041,
       "longitude": 110.78387592210068
   }
   ```

   **Sample Response:**
   ```json
   {
       "data": [
           {
               "address": "Jl. Gajahmada No.34, Timuran, Kec. Banjarsari, Kota Surakarta, Jawa Tengah 57131",
               "categorize_weather": "Dingin",
               "category_id": 7,
               "eco_friendly": 1,
               "id": 313,
               "kecamatan_id": 2,
               "latitude": -7.5809585,
               "longitude": 110.7849666,
               "maps_url": "https://www.google.com/maps/place/Nasi+Liwet+Yu+Djamboel/@-7.5809585,110.7849666,14z/data=!4m11!1m3!2m2!1ssego+liwet+solo!6e5!3m6!1s0x2e7a17745574dcbd:0x6d6246af38815618!8m2!3d-7.5675501!4d110.8177592!15sCg9zZWdvIGxpd2V0IHNvbG9aESIPc2VnbyBsaXdldCBzb2xvkgEKcmVzdGF1cmFudOABAA!16s%2Fg%2F11f6cyx32n?authuser=0&entry=ttu&g_ep=EgoyMDI0MTEwNi4wIKXMDSoASAFQAw%3D%3D",
               "max_price": 25000,
               "min_price": 1000,
               "name": "Nasi Liwet Yu Djamboel",
               "operating_hours": {
                   "closing_time": "23:00:00",
                   "opening_time": "18:00:00"
               },
               "phone_number": "0858783102274",
               "rating": "4.50",
               "reviews": 16
           }
       ]
   }
   
---

## Contributing

Contributions are welcome! Please follow these steps:

1. Fork the repository.
2. Create a new branch for your feature or bug fix.
3. Commit your changes and push the branch.
4. Open a pull request describing your changes.

---

</div>

## **License**

This project is licensed under the [MIT License](LICENSE).

For further questions, please contact the Cloud Computing team at kulinerkitaofficial28@gmail.com.
