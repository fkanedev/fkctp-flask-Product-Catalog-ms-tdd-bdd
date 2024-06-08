![Python](https://img.shields.io/badge/Python-3.8-blue.svg)
![Flask](https://img.shields.io/badge/Flask-2.2.3-b5f05d.svg)
![SQLAlchemy](https://img.shields.io/badge/SQLAlchemy-2.0.0-orange.svg)
![Factory Boy](https://img.shields.io/badge/Factory--Boy-3.2.1-brightgreen.svg)
![Powered by PostgreSQL](https://img.shields.io/badge/Powered%20by-PostgreSQL-336791.svg)
![Coverage Status](https://img.shields.io/badge/Coverage-95%25-green)
![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)

# Product Catalog Project

This final project is an **industry-based** case study involving the development of a microservice for a product catalog backend used in an eCommerce application. I undertook this project as part of my training in the [IBM DevOps and Software Engineering Professional Certificate](https://www.coursera.org/professional-certificates/devops-and-software-engineering). It highlights the practical application of Test and Behavior Driven Development (TDD and BDD) skills acquired during the training. To achieve this, I used [this template](https://github.com/ibm-developer-skills-network/xgcyk-tdd-bdd-final-project-template) provided by IBM Developer Skills Network.

## Table of Contents

1. [Introduction](#introduction)
2. [Technologies Used](#technologies-used)
3. [Installation and Configuration](#installation-configuration)
4. [Usage](#usage)
5. [Development](#development)
6. [Testing](#testing)
7. [Deployment](#deployment)
8. [Source](#source)
9. [License](#license)
10. [Contact](#contact)

## Introduction <a name="introduction"></a>

### Project Objective :

This project aims to create a microservice for a product catalog backend for an eCommerce application. Administrators will use the eCommerce application's UI to maintain the product catalog.

### Key Features :

- Create, read, update, delete, and list products by various attributes.
- Search for products by category, availability, and name.
- Administrative user interface for managing products with BDD scenarios.

## Technologies Used <a name="technologies-used"></a>

### Programming Languages :

- Python 3.8

### Tools and Frameworks :

- Flask (for the REST API microservice)
- Nose (for TDD)
- factory-boy (for creating test data)
- Selenium (for BDD)
- Behave (for BDD scenarios)

## Installation and Configuration <a name="installation-configuration"></a>

### Prerequisites :

- Python 3.8
- pip (Python package manager)

### Installation Steps :

1. Clone the GitHub repository:

```bash
git clone https://github.com/ibm-developer-skills-network/xgcyk-tdd-bdd-final-project-template
cd xgcyk-tdd-bdd-final-project-template
```

2. Create and activate a virtual environment:

```bash
python3.8 -m venv venv
source venv/bin/activate  # On Windows, use `venv\Scripts\activate`
```

3. Install the dependencies:

```bash
pip install -r requirements.txt
```

### Environment Configuration :

Ensure the Python environment is properly set up with Python 3.8. Dependencies should be installed via `pip`.

### Environment Variables :

- `FLASK_ENV=development`
- Other required configuration items are already defined in the [service/config.py](https://github.com/fkanedev/fkctp-flask-Product-Catalog-ms-tdd-bdd/blob/main/service/config.py) file.

## Usage <a name="usage"></a>

### Usage Instructions :

To start the application, use the following command:

```bash
flask run
```

### Use Case Examples :

- **Create a product:**
To create a product, send a POST request to the `/products` endpoint with the product details in the request body.

```bash
curl -X POST http://localhost:5000/products -H "Content-Type: application/json" -d '{"name": "Sample Product", "category": "Category1", "available": true, "price": 19.99}'
```

- **Read a product:**
To read a product, send a GET request to the `/products/<product_id>` endpoint with the product ID.

```bash
curl -X GET http://localhost:5000/products/1
```

- **Update a product:**
To update a product, send a PUT request to the `/products/<product_id>` endpoint with the updated product details in the request body.

```bash
curl -X PUT http://localhost:5000/products/1 -H "Content-Type: application/json" -d '{"name": "Updated Product", "category": "Category1", "available": false, "price": 29.99}'
```

- **Delete a product:**
To delete a product, send a DELETE request to the `/products/<product_id>` endpoint with the product ID.

```bash
curl -X DELETE http://localhost:5000/products/1
```

- **List products by category:**
To list products by category, send a GET request to the `/products?category=<category_name>` endpoint.

```bash
curl -X GET http://localhost:5000/products?category=Category1
```

- **List products by availability:**
To list products by availability, send a GET request to the `/products?available=<true|false>` endpoint.

```bash
curl -X GET http://localhost:5000/products?available=true
```

- **List products by name:**
To list products by name, send a GET request to the `/products?name=<product_name>` endpoint.

```bash
curl -X GET http://localhost:5000/products?name=Sample+Product
```

## Development <a name="development"></a>

### Project Structure :

This backend project is primarily organized around the Flask framework. The directory structure includes the following folders:
- `service`: Contains routes and data models.
- `tests`: Contains unit tests and integration tests.
- `features`: Contains BDD scenarios and associated steps.

```plaintext
.
├── service/
│   ├── __init__.py
│   ├── models.py
│   ├── routes.py
│   └── ...
├── tests/
│   ├── test_models.py
│   ├── test_routes.py
│   └── ...
├── features/
│   ├── steps/
│   ├── environment.py
│   └── ...
├── requirements.txt
├── config.py
└── ...
```

### Database :

PostgreSQL serves as the database, accessible through the connection URI specified in the environment variables.SQLAlchemy acts as the Object Relational Mapper (ORM) for interacting with the database. Integrated with Flask through Flask-SQLAlchemy, it provides an interface to create and manage database tables and perform CRUD (Create, Read, Update, Delete) operations with Python.
### Data Model (About the Product Model)

The data model for our product catalog is designed to store essential information about each product available in our eCommerce application. Here's an overview of the main features of the data model:

- **Product Name**: The unique name of the product.
- **Description**: A brief description of the product to help users understand its features.
- **Category**: The category to which the product belongs, facilitating navigation and search for users.
- **Availability**: Indicates whether the product is currently available for purchase.
- **Price**: The price of the product.

This data model is designed to provide a flexible structure while ensuring that all necessary information is easily accessible for users of our application.

## Testing <a name="testing"></a>

The TDD and BDD techniques implemented in this project ensure the most comprehensive testing possible and the maintenance of high code coverage. To verify this, you can follow the steps outlined below. 

### Unit Tests :

Execute the following command to run the unit tests and measure code coverage. Ensure the project maintains at least 95% code coverage:

```bash
nosetests --with-coverage --cover-erase --cover-package=service
```

- `--with-coverage`: Activates the coverage plugin.
- `--cover-erase`: Clears previous coverage data.
- `--cover-package=service`: Measures coverage for the service package only.

### Behavior Tests :

In one terminal, start the application using:

```bash
honcho start
```

In another terminal, execute the BDD scenarios with:

```bash
behave
```

Ensure there are seven scenarios (Read, Update, Delete a Product, List all Products, List by Category, List by Available, List by Name) and that all pass.


## Deployment <a name="deployment"></a>

This project supports both manual deployment and containerized deployment using Docker. Below are the detailed instructions for each method.

### Manual Deployment :

The manual deployment strategy involves directly setting up the environment and running the application on the host machine. This method is simple and suitable for small-scale deployments or development purposes. However, it requires manual setup and is less scalable for larger applications.

1. Clone the repository:

```bash
git clone https://github.com/ibm-developer-skills-network/xgcyk-tdd-bdd-final-project-template.git
```

2. Navigate to the project directory:

```bash
cd xgcyk-tdd-bdd-final-project-template
```

3. Set the environment to production:

```bash
export FLASK_ENV=production
```

4. Install the required dependencies:

```bash
pip install -r requirements.txt
```

5. Run the application:

```bash
flask run
```

### Containerized Deployment :

The containerized deployment strategy involves packaging the application and its dependencies into a Docker container. This ensures consistency and portability across different environments. Docker containers can be easily managed, scaled, and deployed on various platforms, making this method efficient for both development and production environments.

1. Clone the repository:

```bash
git clone https://github.com/ibm-developer-skills-network/xgcyk-tdd-bdd-final-project-template.git
```

2. Navigate to the project directory:

```bash
cd xgcyk-tdd-bdd-final-project-template
```

3. Build the Docker image:

```bash
docker build -t product-catalog .
```

4. Run the Docker container:

```bash
docker run -d -p 5000:5000 --name product-catalog product-catalog
```

## Sources <a name="source"></a>

- **Template : [ibm-developer-skills-network/xgcyk-tdd-bdd-final-project-template](https://github.com/ibm-developer-skills-network/xgcyk-tdd-bdd-final-project-template)**
- **Useful links** :

  - **[Introduction to Test and Behavior Driven Development](https://www.coursera.org/learn/test-and-behavior-driven-development-tdd-bdd/home/week/1)**

  - **[IBM DevOps and Software Engineering Professional Certificate](https://www.coursera.org/professional-certificates/devops-and-software-engineering)**

## License <a name="license"></a>

This project is licensed under the MIT License. See the `LICENSE` file for more information.

## Contact <a name="contact"></a>

### Contact Information :

- Send me email : **fkanecloudtech@gmailcom**
- Connect with me on [LinkedIn](https://www.linkedin.com/in/your-profile/)
- Visit my [portfolio](https://yourname.github.io) to explore my projects and services.


### Contribution and Support :

Contributions are welcome. Please refer to the `CONTRIBUTING.md` file for more information on how to contribute.
