# API Documentation - Backend PHP for Sales Management Website

## 1. **Login**
### Endpoint: `POST /api/login.php`
- **Request Headers:**
    - `Content-Type: application/json`
- **Request Body:**
    ```json
    {
        "username": "admin",
        "password": "123456"
    }
    ```
- **Response:**
    ```json
    {
        "success": true,
        "session_token": "9f384172a5482a37c01f08e4c927d7153b6fd7dc7d294f7bfac4ea03c59dcffe",
        "permissions": { "all": true },
        "user_id": 1
    }
    ```

## 2. **Add New User**  (add NV )
### Endpoint: `POST /api/register.php`
- **Request Headers:**
    - `Authorization: 9f384172a5482a37c01f08e4c927d7153b6fd7dc7d294f7bfac4ea03c59dcffe`
    - `Content-Type: application/json`
- **Request Body:**
    ```json
    {
        "username": "user2",
        "password": "password123",
        "permissions": {
            "read": true,
            "write": false,
            "delete": false
        }
    }
    ```
- **Response:**
    ```json
    {
        "success": true,
        "user_id": "4",
        "message": "User registered successfully"
    }
    ```

## 3. **Update User Permissions**
### Endpoint: `PUT /api/update_permissions.php`
- **Request Headers:**
    - `Authorization: d128720a880f55b01b4f8a334f3a787a3bc70b6bc80a302ef220829174e62fc1`
    - `Content-Type: application/json`
- **Request Body:**
    ```json
    {
        "user_id": 2,
        "permissions": {
            "read": true,
            "write": true,
            "delete": false
        }
    }
    ```
- **Response:**
    ```json
    {
        "success": true,
        "message": "Permissions updated successfully"
    }
    ```

## 4. **Check User Role**
### Endpoint: `POST /api/check_role.php`
- **Request Headers:**
    - `Content-Type: application/json`
- **Request Body:**
    ```json
    {
        "session_token": "9f384172a5482a37c01f08e4c927d7153b6fd7dc7d294f7bfac4ea03c59dcffe",
        "feature": "write"
    }
    ```
- **Response:**
    ```json
    {
        "success": true,
        "access_granted": true
    }
    ```
## 5. **Get All Employee Accounts**
### Endpoint: `GET /api/get_all_accounts.php`
- **Request Headers:**
    - `Authorization: <session_token>`
    - `Content-Type: application/json`
- **Response:**
    ```json
    {
        "success": true,
        "accounts": [
            {
                "id": 1,
                "username": "admin",
                "permissions": {
                    "all": true,
                    "read": true,
                    "write": true,
                    "delete": true
                },
                "created_at": "2024-01-01 10:00:00"
            },
            {
                "id": 2,
                "username": "user1",
                "permissions": {
                    "read": true,
                    "write": false,
                    "delete": false
                },
                "created_at": "2024-01-02 11:00:00"
            }
        ]
    }
    ```

---

## 6 **Update Employee Account**
### Endpoint: `PUT /api/update_account.php`
- **Request Headers:**
    - `Authorization: <session_token>`
    - `Content-Type: application/json`
- **Request Body:**
    ```json
    {
        "user_id": 2,
        "username": "new_username",
        "password": "new_password",
        "permissions": {
            "read": true,
            "write": true,
            "delete": false
        }
    }
    ```
- **Response:**
    ```json
    {
        "success": true,
        "message": "User information updated successfully"
    }
    ```


---

# Customer Management API

## 1. **Create Customer**
### Endpoint: `POST /api/customer/create_customer.php`
- **Request Body (raw JSON):**
    ```json
    {
        "session_token": "9f384172a5482a37c01f08e4c927d7153b6fd7dc7d294f7bfac4ea03c59dcffe",
        "customer_name": "Nguyễn Văn A",
        "phone": "0901234567",
        "email": "nguyenvana@example.com",
        "birth_year": "1980",
        "gender": "Nam",
        "note": "Khách hàng VIP",
        "delivery_address": "Đường A, Thành phố B",
        "company_name": "Công ty ABC",
        "tax_code": "123456789",
        "company_email": "abc@company.com",
        "city": "Hà Nội",
        "district": "Quận Hoàn Kiếm",
        "ward": "Phường 1",
        "address": "Số 123, Đường ABC"
    }
    ```

## 2. **Update Customer**
### Endpoint: `POST /api/customer/update_customer.php`
- **Request Body (raw JSON):**
    ```json
    {
        "session_token": "9f384172a5482a37c01f08e4c927d7153b6fd7dc7d294f7bfac4ea03c59dcffe",
        "customer_id": 1,
        "customer_name": "Nguyễn Văn A Cập Nhật",
        "phone": "0901234567",
        "email": "nguyenvana_updated@example.com",
        "birth_year": "1980",
        "gender": "Nam",
        "note": "Khách hàng VIP đã cập nhật",
        "delivery_address": "Đường B, Thành phố C",
        "company_name": "Công ty XYZ",
        "tax_code": "987654321",
        "company_email": "xyz@company.com",
        "city": "Hà Nội",
        "district": "Quận Ba Đình",
        "ward": "Phường 3",
        "address": "Số 456, Đường XYZ"
    }
    ```

## 3. **Delete Customer**
### Endpoint: `POST /api/customer/delete_customer.php`
- **Request Body (raw JSON):**
    ```json
    {
        "session_token": "your_session_token_here",
        "customer_id": 1
    }
    ```

## 4. **Get Customers**
### Endpoint: `POST /api/customer/get_customers.php`
- **Request Body (raw JSON):**
    ```json
    {
        "session_token": "your_session_token_here"
    }
    ```

## 5. **Get Customer by ID**
### Endpoint: `POST /api/customer/get_customer_by_id.php`
- **Request Body (raw JSON):**
    ```json
    {
        "session_token": "your_session_token_here",
        "customer_id": 1
    }
    ```

# Order Management API

## 1. **Create Order**
### Endpoint: `POST /api/order/create_order.php`
- **Request Body (raw JSON):**
    ```json
    {
    "session_token": "46574efc138b9af80ba70d6bdc8f2a68c36573efb7c3e688eb5f445b69be4e42",
    "customer_id": 1,
    "recipient_name": "John Doe",
    "recipient_phone": "1234567890",
    "delivery_address": "123 Main St, Hanoi",
    "order_status": 1,
    "notes": "Urgent order",
    "product_details": [
        {
            "product_code": "SP001",
            "quantity": 10,
            "price": 11110
        },
        {
            "product_code": "SP002",
            "quantity": 5,
            "price": 15000
        }
    ],
    "processing_employee_id": 2,
    "estimated_delivery_date": "2024-12-15"
    }
    ```

## 2. **Get Order**
### Endpoint: `POST /api/order/get_order.php`
- **Request Body (raw JSON):**
    ```json
    {
        "session_token": "your_session_token_here",
        "order_id": 1
    }
    ```

## 3. **Update Order Status**
### Endpoint: `POST /api/order/update_order_status.php`
- **Request Body (raw JSON):**
    ```json
    {
        "session_token": "your_session_token_here",
        "order_id": 1,
        "order_status": 2    }
    ```

## 4. **Delete Order**
### Endpoint: `POST /api/order/delete_order.php`
- **Request Body (raw JSON):**
    ```json
    {
        "session_token": "your_session_token_here",
        "order_id": 1
    }
    ```
## 5. **Get Orders**
### Endpoint: `POST /api/order/get_orders.php`

- **Request Body (raw JSON):**
    ```json
    {
        "session_token": "your_session_token_here",
        "page": 1,
        "limit": 10
    }
    ```

# Order Status Management API

## 1. **Add Order Status**
### Endpoint: `POST /api/order_status.php`
- **Request Headers:**
    - `Content-Type: application/json`
- **Request Body:**
    ```json
    {
        "session_token": "your-session-token",
        "status_name": "Đang báo giá",
        "description": "Nhân viên đang báo giá"
    }
    ```
- **Response:**
    ```json
    {
        "success": true,
        "message": "Order status added successfully"
    }
    ```

## 2. **Update Order Status**
### Endpoint: `PUT /api/order_status.php`
- **Request Headers:**
    - `Content-Type: application/json`
- **Request Body:**
    ```json
    {
        "session_token": "your-session-token",
        "id": 1,
        "status_name": "Đang xử lý",
        "description": "Đơn hàng đang được xử lý"
    }
    ```
- **Response:**
    ```json
    {
        "success": true,
        "message": "Order status updated successfully"
    }
    ```

## 3. **Delete Order Status**
### Endpoint: `DELETE /api/order_status.php`
- **Request Headers:**
    - `Content-Type: application/json`
- **Request Body:**
    ```json
    {
        "session_token": "your-session-token",
        "id": 1
    }
    ```
- **Response:**
    ```json
    {
        "success": true,
        "message": "Order status deleted successfully"
    }
    ```

---

# Category Management API

## 1. **Add Category**
### Endpoint: `POST /api/categories.php`
- **Request Headers:**
    - `Content-Type: application/json`
- **Request Body:**
    ```json
    {
        "session_token": "your-session-token",
        "category_name": "Điện tử",
        "description": "Các sản phẩm thuộc nhóm điện tử"
    }
    ```
- **Response:**
    ```json
    {
        "success": true,
        "message": "Category added successfully"
    }
    ```

## 2. **Update Category**
### Endpoint: `PUT /api/categories.php`
- **Request Headers:**
    - `Content-Type: application/json`
- **Request Body:**
    ```json
    {
        "session_token": "your-session-token",
        "id": 1,
        "category_name": "Đồ gia dụng",
        "description": "Các sản phẩm thuộc nhóm đồ gia dụng"
    }
    ```
- **Response:**
    ```json
    {
        "success": true,
        "message": "Category updated successfully"
    }
    ```

## 3. **Delete Category**
### Endpoint: `DELETE /api/categories.php`
- **Request Headers:**
    - `Content-Type: application/json`
- **Request Body:**
    ```json
    {
        "session_token": "your-session-token",
        "id": 1
    }
    ```
- **Response:**
    ```json
    {
        "success": true,
        "message": "Category deleted successfully"
    }
    ```
## 4. **Get All Categories**
### Endpoint: `GET /api/categories.php`
- **Request Headers:**
    - `Authorization: <session_token>`
    - `Content-Type: application/json`
- **Response:**
    ```json
    {
        "success": true,
        "categories": [
            {
                "id": 1,
                "category_name": "Giấy",
                "description": "ChUyêN fr0ntEnD IT =))))))"
            },
            {
                "id": 2,
                "category_name": "giấy",
                "description": "Các sản phẩm thuộc nhóm thời trang"
            }
        ]
    }
    ```



# Product Management API

## 1. **Add Product (One Price)**
### Endpoint: `POST /product/qlsp.php`
- **Request Headers:**
    - `Content-Type: application/json`
- **Request Body:**
    ```json
    {
        "session_token": "your-session-token",
        "category_id": 1,
        "product_name": "Ống Sắt",
        "rules": "Quy cách chuẩn.....",
        "notes": "Sản phẩm thông dụng",
        "nhieuquycach": false,
        "pricing": [
            {
                "quantity": 10,
                "price": 16000
            }
        ]
    }
    ```
- **Response:**
    ```json
    {
        "success": true,
        "message": "Product added successfully"
    }
    ```

## 2. **Add Product (Multiple Prices)**
### Endpoint: `POST /product/qlsp.php`
- **Request Headers:**
    - `Content-Type: application/json`
- **Request Body:**
    ```json
    {
        "session_token": "your-session-token",
        "category_id": 1,
        "product_name": "Ống sắt nhiều giá",
        "rules": "Quy cách chuẩn .....",
        "notes": "Sản phẩm cao cấp",
        "nhieuquycach": true,
        "pricing": [
            {
                "quantity": 10,
                "price": 17000,
                "note": "Giá lẻ"
            },
            {
                "quantity": 50,
                "price": 7500,
                "note": "Giá sỉ"
            }
        ]
    }
    ```
- **Response:**
    ```json
    {
        "success": true,
        "message": "Product added successfully"
    }
    ```

## 3. **Edit Product**
### Endpoint: `PUT /product/qlsp.php`
- **Request Headers:**
    - `Content-Type: application/json`
- **Request Body:**
    ```json
    {
        "session_token": "your-session-token",
        "id": 1,
        "category_id": 1,
        "product_name": "Ống sắt Updated",
        "rules": "Quy cách .......",
        "notes": "Sản phẩm thông dụng đã cập nhật",
        "nhieuquycach": false,
        "pricing": [
            {
                "quantity": 10,
                "price": 16000
            }
        ]
    }
    ```
- **Response:**
    ```json
    {
        "success": true,
        "message": "Product updated successfully"
    }
    ```

## 4. **Delete Product**
### Endpoint: `DELETE /product/qlsp.php`
- **Request Headers:**
    - `Content-Type: application/json`
- **Request Body:**
    ```json
    {
        "session_token": "your-session-token",
        "id": 1
    }
    ```
- **Response:**
    ```json
    {
        "success": true,
        "message": "Product deleted successfully"
    }
    ```

## 5. **Get All Products**
### Endpoint: `GET /product/show_products.php`
- **Request Headers:**
    - `Content-Type: application/json`
- **Request Body:**
    - `session_token`: (User session token to verify the request)
- **Response:**
    ```json
    {
        "success": true,
        "products": [
            {
                "id": 1,
                "product_name": "Couche 150gsm",
                "rules": "Quy cách chuẩn in giấy",
                "notes": "Sản phẩm thông dụng",
                "multiple_pricing": false,
                "category_name": "Giấy Couche",
                "pricing": [
                    {
                        "quantity": 10,
                        "price": 16000,
                        "note": "Giá lẻ"
                    }
                ]
            },
            {
                "id": 2,
                "product_name": "Couche 200gsm",
                "rules": "Quy cách chuẩn in giấy",
                "notes": "Sản phẩm cao cấp",
                "multiple_pricing": true,
                "category_name": "Giấy Couche",
                "pricing": [
                    {
                        "quantity": 10,
                        "price": 17000,
                        "note": "Giá lẻ"
                    },
                    {
                        "quantity": 50,
                        "price": 7500,
                        "note": "Giá sỉ"
                    }
                ]
            }
        ]
    }
    ```

## 6. **Get Product Details By ID**
### Endpoint: `GET /product/show_product_by_id.php`
- **Request Headers:**
    - `Content-Type: application/json`
- **Query Parameters:**
    - `session_token`: (User session token)
    - `product_id`: (Product ID to view details)
- **Response:**
    ```json
    {
        "success": true,
        "product": {
            "id": 1,
            "product_name": "Couche 150gsm",
            "rules": "Quy cách chuẩn in giấy",
            "notes": "Sản phẩm thông dụng",
            "multiple_pricing": false,
            "category_name": "Giấy Couche",
            "pricing": [
                {
                    "quantity": 10,
                    "price": 16000,
                    "note": "Giá lẻ"
                }
            ]
        }
    }
    ```
## 7. **Check Product Orders**
### Endpoint: `POST /product/check_product_orders.php`
- **Request Headers:**
    - `Content-Type: application/json`
- **Request Body:**
    - `session_token`: (User session token to verify the request)
    - `product_name`: (The name of the product to check for in orders, case-insensitive)

- **Response:**
    - **Success**:
    ```json
    {
        "success": true,
        "message": "Orders found for the product",
        "orders": [
            {
                "order_id": 1,
                "customer_id": 2,
                "recipient_name": "John Doe",
                "recipient_phone": "1234567890",
                "delivery_address": "123 Main St, Hanoi",
                "order_date": "2024-11-24 10:00:00",
                "order_status": 1,
                "notes": "Urgent order",
                "product_details": "[{\"product_code\": \"SP001\", \"quantity\": 10}]",
                "printing_company_id": null
            },
            {
                "order_id": 2,
                "customer_id": 3,
                "recipient_name": "Jane Doe",
                "recipient_phone": "0987654321",
                "delivery_address": "456 Other St, Hanoi",
                "order_date": "2024-11-25 14:00:00",
                "order_status": 1,
                "notes": "Standard delivery",
                "product_details": "[{\"product_code\": \"SP001\", \"quantity\": 20}]",
                "printing_company_id": 1
            }
        ]
    }
    ```
