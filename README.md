# Simple E-commerce API & Frontend

This project provides a basic e-commerce solution with a Python Flask API backend and a pure HTML/JavaScript frontend. It demonstrates user authentication with JWT, role-based access control (Customer and Admin), product management, cart management, and order creation.

## Features

**Backend (Flask API):**
* **User Authentication & Authorization:**
    * Register new users (default role: `customer`).
    * Login users and receive a JSON Web Token (JWT) for authentication.
    * JWTs are used to secure API routes.
    * Two roles: `customer` and `admin`.
* **Product Management:**
    * View all products (Customer & Admin).
    * Add, Update, Delete products (Admin only).
* **Cart Management:**
    * Add products to cart (Customer only).
    * Update product quantities in cart (Customer only).
    * Remove products from cart (Customer only).
* **Order Management:**
    * Create orders from the cart (Customer only).
    * View all orders (Admin only).
    * View personal orders (Customer only).
    * Update order status (Admin only).
* **In-memory Data Storage:** All data is stored in Python dictionaries for simplicity. Data will reset on server restart.
* **CORS Enabled:** Allows the frontend (running on a different origin) to communicate with the API.

**Frontend (HTML/JavaScript):**
* **Single-Page Application (SPA) Structure:** Uses JavaScript to dynamically render content.
* **Authentication Forms:** Login and Register forms.
* **Role-based UI:** Dynamically displays customer or admin features based on the logged-in user's role.
* **Product Listing:** Displays available products.
* **Shopping Cart:** Interactive cart where users can add, update, and remove items.
* **Order Placement:** Checkout functionality to create an order.
* **My Orders:** Displays a list of orders placed by the current customer.
* **Admin Panels:**
    * Product management (add, edit, delete products).
    * Order management (view all orders, update order status).
* **Responsive Design:** Styled with Tailwind CSS.

## Project Structure


.
├── app.py                  # Flask API backend
├── index.html              # HTML frontend
├── requirements.txt        # Python dependencies
└── .gitignore              # Files to ignore for Git
└── README.md               # This file


## Setup and Running the Project

### 1. Backend Setup (Flask API)

1.  **Clone the repository (or create the files):**
    If you're starting from scratch, create the `app.py`, `requirements.txt`, and `.gitignore` files in a new directory.

2.  **Create a Virtual Environment (Recommended):**
    It's good practice to use a virtual environment to manage dependencies.
    ```bash
    python -m venv venv
    ```

3.  **Activate the Virtual Environment:**
    * **On Windows:**
        ```bash
        .\venv\Scripts\activate
        ```
    * **On macOS/Linux:**
        ```bash
        source venv/bin/activate
        ```

4.  **Install Dependencies:**
    Navigate to the project root directory (where `requirements.txt` is located) and install the required Python packages:
    ```bash
    pip install -r requirements.txt
    ```

5.  **Run the Flask API:**
    ```bash
    python app.py
    ```
    The API will start running on `http://127.0.0.1:5000`. Keep this terminal window open.

### 2. Frontend Setup (HTML/JavaScript)

1.  **Place `index.html`:**
    Ensure `index.html` is in the same directory as `app.py`, or in a subfolder.

2.  **Open in Browser:**
    Simply open the `index.html` file in your web browser (e.g., by double-clicking it).

    * **Important:** The frontend JavaScript expects the API to be running on `http://127.0.0.1:5000`. If you change the Flask API's host or port, you'll need to update the `API_BASE_URL` variable in `index.html` accordingly.

## Usage

### Initial Users (for testing):

The `app.py` script pre-populates two users:

* **Admin User:**
    * Username: `admin`
    * Password: `adminpass`
* **Customer User:**
    * Username: `customer`
    * Password: `customerpass`

You can also register new customer users via the frontend.

### Frontend Interaction:

1.  **Authentication:**
    * Use the "Login" or "Register" forms to authenticate.
    * Upon successful login, the UI will switch to either the "Shop" (Customer) or "Admin Panel" (Admin) view.
    * Your JWT token and user role will be stored in your browser's `localStorage`.

2.  **Customer View:**
    * **Products:** Browse the list of available products.
    * **Add to Cart:** Click "Add to Cart" on any product.
    * **Cart:** View items in your cart, update quantities, or remove items.
    * **Checkout:** Click "Proceed to Checkout" to create an order.
    * **My Orders:** See a list of your placed orders and their statuses.

3.  **Admin View:**
    * **Product Management:**
        * Use the "Add New Product" form to add new items.
        * The "Existing Products" table allows you to "Edit" or "Delete" products.
    * **Order Management:**
        * View all customer orders.
        * Change the status of any order using the dropdown.

## Optional Enhancements (for Extra Credit)

* **Pagination for Product Listing:** Modify the `/products` endpoint in `app.py` to accept `page` and `limit` parameters, and update `fetchProducts` in `index.html` to use them.
* **Product Search/Filtering:** Add a search input and/or category filters to the frontend, and implement corresponding logic in the `/products` endpoint.
* **Persistent Database:** Replace the in-memory data stores in `app.py` with a real database (e.g., SQLite, PostgreSQL, MongoDB) to make data persistent across server restarts.
* **Error Handling Improvements:** More robust error handling and user feedback.
* **Frontend Framework:** Migrate the frontend to a framework like React, Vue, or Angular for better structure and maintainability.
* **Dockerization:** Containerize the API and frontend using Docker.
