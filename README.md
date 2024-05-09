# Vendor Management System with Performance Metrics

## Vendor Profile Management

# Django REST API Setup

This repository contains a Django project with a RESTful API using Django REST Framework.

## Prerequisites

- Python (version 3.x recommended)
- Django
- Django REST Framework

# Setup Instructions

## Create a Virtual Environment:
- pip install virtualenv
- python -m venv envname

## Install Dependencies:
- pip install django
- pip install djangorestframework

## Set up a new project with a single application
- django-admin startproject vendor_management_system                 
- cd vendor_management_system
- django-admin startapp vendorsApp              

## Database migration                    
- python manage.py makemigrations      
- python manage.py migrate

## Superuser creation and Token generation
- python manage.py createsuperuser

## Running the server
- python manage.py runserver

## Access Django Admin:
Open the Django admin at http://127.0.0.1:8000/admin/ and log in using the superuser credentials. This is to access the database as a admin user.

### Create a New Vendor
- **Method:** POST
- **URL:** `/api/vendors/`

**Request Body**
```json
{
    "name": "Girish",
    "contact_details": "6363309263",
    "address": "Bangalore"
}
**Response**
Status Code: 200 OK
{
    "name": "Girish",
    "contact_details": "6363309263",
    "address": "Bangalore",
    "vendor_code": "fc16a182-7d26-4e1c-9c57-a4343c5e41e8",
    "on_time_delivery_rate": 0.0,
    "quality_rating_avg": 0.0,
    "average_response_time": 0.0,
    "fulfillment_rate": 0.0
}
List All Vendors
Method: GET
URL: /api/vendors/
Response

Status Code: 200 OK
[
    {
        "name": "Girish",
        "contact_details": "6363309263",
        "address": "Bangalore",
        "vendor_code": "fc16a182-7d26-4e1c-9c57-a4343c5e41e8",
        "on_time_delivery_rate": 0.0,
        "quality_rating_avg": 0.0,
        "average_response_time": 0.0,
        "fulfillment_rate": 0.0
    },
    {
        "name": "Nandan",
        "contact_details": "6360409263",
        "address": "Bangalore",
        "vendor_code": "790c3e68-89df-45bb-a838-9af1ba8c2496",
        "on_time_delivery_rate": 0.0,
        "quality_rating_avg": 0.0,
        "average_response_time": 0.0,
        "fulfillment_rate": 0.0
    }
]

Retrieve a Specific Vendor's Details
Method: GET
URL: /api/vendors/{vendor_id}/
Response

Status Code: 200 OK
{
    "name": "Girish",
    "contact_details": "6363309263",
    "address": "Bangalore",
    "vendor_code": "fc16a182-7d26-4e1c-9c57-a4343c5e41e8",
    "on_time_delivery_rate": 0.0,
    "quality_rating_avg": 0.0,
    "average_response_time": 0.0,
    "fulfillment_rate": 0.0
}

Update a Vendor's Details
Method: PUT
URL: /api/vendors/{vendor_id}/
Request Body
{
    "name": "Girish",
    "contact_details": "6363309263",
    "address": "Bangalore"
}

Response

Status Code: 200 OK
{
    "name": "Girish",
    "contact_details": "6363309263",
    "address": "Bangalore",
    "vendor_code": "fc16a182-7d26-4e1c-9c57-a4343c5e41e8",
    "on_time_delivery_rate": 0.0,
    "quality_rating_avg": 0.0,
    "average_response_time": 0.0,
    "fulfillment_rate": 0.0
}

Delete a Vendor
Method: DELETE
URL: /api/vendors/{vendor_id}/
Response

Status Code: 200 OK
{
    "message": "Vendor deleted successfully."
}

Purchase Order Tracking
Create a Purchase Order
Method: POST
URL: /api/purchase_orders/
Request Body
{
  "po_number": "PO123867",
  "vendor": 4,
  "delivery_date": "2023-12-06T15:30:00Z",
  "items": [
    {
      "name": "Widget A",
      "description": "A high-quality widget",
      "price": 19.99,
      "quantity": 10
    },
    {
      "name": "Gizmo B",
      "description": "An innovative gizmo",
      "price": 29.99,
      "quantity": 5
    }
  ],
  "quantity": 15,
  "status": "completed",
  "quality_rating": null,
  "issue_date": "2023-12-06T15:30:00Z",
  "acknowledgment_date": null
}

Response

Status Code: 200 OK
{
    "id": 6,
    "po_number": "PO123867",
    "order_date": "2023-12-06T05:38:34.397261Z",
    "delivery_date": "2023-12-06T15:30:00Z",
    "items": [
        {
            "name": "Widget A",
            "description": "A high-quality widget",
            "price": 19.99,
            "quantity": 10
        },
        {
            "name": "Gizmo B",
            "description": "An innovative gizmo",
            "price": 29.99,
            "quantity": 5
        }
    ],
    "quantity": 15,
    "status": "completed",
    "quality_rating": null,
    "issue_date": "2023-12-06T15:30:00Z",
    "acknowledgment_date": null,
    "vendor": 5
}

List All Purchase Orders
Method: GET
URL: /api/purchase_orders/
Response

Status Code: 200 OK
[
    {
        "id": 6,
        "po_number": "PO123867",
        "order_date": "2023-12-06T05:38:34.397261Z",
        "delivery_date": "2023-12-06T15:30:00Z",
        "items": [
            {
                "name": "Widget A",
                "price": 19.99,
                "quantity": 10,
                "description": "A high-quality widget"
            },
            {
                "name": "Gizmo B",
                "price": 29.99,
                "quantity": 5,
                "description": "An innovative gizmo"
            }
        ],
        "quantity": 15,
        "status": "completed",
        "quality_rating": null,
        "issue_date": "2023-12-06T15:30:00Z",
        "acknowledgment_date": null,
        "vendor": 5
    },
    {
        "id": 7,
        "po_number": "PO123868",
        "order_date": "2023-12-06T05:41:05.764726Z",
        "delivery_date": "2023-12-06T15:30:00Z",
        "items": [
            {
                "name": "Water Bottle",
                "price": 89.99,
                "quantity": 5,
                "description": "A high-quality widget"
            },
            {
                "name": "Gym Bag",
                "price": 49.99,
                "quantity": 10,
                "description": "An innovative gizmo"
            }
        ],
        "quantity": 20,
        "status": "pending",
        "quality_rating": null,
        "issue_date": "2023-12-06T15:30:00Z",
        "acknowledgment_date": null,
        "vendor": 7
    }
]

Filter Purchase Orders by Vendor ID
Method: GET
URL: /api/purchase_orders?vendor=5
Response

Status Code: 200 OK
[
    {
        "id": 6,
        "po_number": "PO123867",
        "order_date": "2023-12-06T05:38:34.397261Z",
        "delivery_date": "2023-12-06T15:30:00Z",
        "items": [
            {
                "name": "Widget A",
                "price": 19.99,
                "quantity": 10,
                "description": "A high-quality widget"
            },
            {
                "name": "Gizmo B",
                "price": 29.99,
                "quantity": 5,
                "description": "An innovative gizmo"
            }
        ],
        "quantity": 15,
        "status": "completed",
        "quality_rating": null,
        "issue_date": "2023-12-06T15:30:00Z",
        "acknowledgment_date": null,
        "vendor": 5
    }
]

Retrieve Details of a Specific Purchase Order
Method: GET
URL: /api/purchase_orders/{po_id}/
Response

Status Code: 200 OK
{
    "id": 6,
    "po_number": "PO123867",
    "order_date": "2023-12-06T05:38:34.397261Z",
    "delivery_date": "2023-12-06T15:30:00Z",
    "items": [
        {
            "name": "Widget A",
            "price": 19.99,
            "quantity": 10,
            "description": "A high-quality widget"
        },
        {
            "name": "Gizmo B",
            "price": 29.99,
            "quantity": 5,
            "description": "An innovative gizmo"
        }
    ],
    "quantity": 15,
    "status": "completed",
    "quality_rating": null,
    "issue_date": "2023-12-06T15:30:00Z",
    "acknowledgment_date": null,
    "vendor": 5
}

Update a Purchase Order
Method: PUT
URL: /api/purchase_orders/{po_id}/
Request Body
{
  "po_number": "PO123868",
  "vendor": 7,
  "delivery_date": "2023-12-06T15:30:00Z",
  "items": [
    {
      "name": "Water Bottle",
      "description": "A high-quality widget",
      "price": 89.99,
      "quantity": 5
    },
    {
      "name": "Gym Bag",
      "description": "An innovative gizmo",
      "price": 49.99,
      "quantity": 10
    }
  ],
  "quantity": 20,
  "status": "pending",
  "quality_rating": null,
  "issue_date": "2023-12-06T15:30:00Z",
  "acknowledgment_date": null
}

Delete a Purchase Order
Method: DELETE
URL: /api/purchase_orders/{po_id}/
Response

Status Code: 200 OK
{
    "message": "Purchase Order deleted successfully"
}

Vendor Performance Evaluation
Get Vendor Performance
Method: GET
URL: /api/vendors/{vendor_id}/performance
{
    "on_time_delivery_rate": 0.0,
    "quality_rating_avg": 0.0,
    "average_response_time": 0.0,
    "fulfillment_rate": 100.0
}

Acknowledgment Update of PO
Method: POST
URL: /api/purchase_orders/{po_id}/acknowledge
Response
{
    "message": "Purchase Order acknowledged successfully."
}