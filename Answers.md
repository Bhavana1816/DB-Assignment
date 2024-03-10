1    The relationship between the "Product" and "Product_Category" entities in the provided diagram appears to be One-to-many realationship, where one product 
     category can have multiple products associated with it, 
     but each product belongs to only one category.
     In the "Product_Category" entity, there is an "id" field which serves as the primary key.This "id" fields is referenced in the "Category_id" field of the 
    "product" entity.This"Category_id" fields in the "Product" 
     entity acts as a foreign key linking each product to its respective category.
     Therefor,each product listed in the "product" entity, there will be a corresponding "Category_id" that indicates the products category and this "category_id" 
     must match an "id" in the "product"entity, establishing
     the relationship between the two entities.This allows for the categorization of products and enables quaries that retrive products based on their associated 
     categories.

2    The ensure the product in the "Product" table has a valid category assigned to it, you can use a foreign key constraint in the databases schema. Specifically,you 
     would enforce referential integroty by setting up a forign key
     relationship between the "catory_id" column in the "product" table and "id" column in the "Product_category" table.
     1.Define Foreign Key Constrants
     2.Enforce Cascade Actions(optional)
     3.Handling Null Values
     
     ALTER TABLE PRODUCT
     ADD CONSTRANT FK_PRODUCT_CATEGORY
     FOREIGN KEY(CATEGORY_ID)
     REFERNCE PRODUCT_CATEGORY(ID)
     ON DELECT CASCADE;

3.   Answers.sql
4.              -- Create Product_Category table
CREATE TABLE Product_Category (
    id INT AUTO_INCREMENT PRIMARY KEY,
    name VARCHAR(255),
    description TEXT,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    modified_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP
);

-- Create Product table
CREATE TABLE Product (
    id INT AUTO_INCREMENT PRIMARY KEY,
    name VARCHAR(255),
    deleted_at TIMESTAMP,
    category_id INT,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    modified_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP,
    FOREIGN KEY (category_id) REFERENCES Product_Category(id)
);

-- Create Product_Inventory table
CREATE TABLE Product_Inventory (
    id INT AUTO_INCREMENT PRIMARY KEY,
    SKU VARCHAR(255),
    quantity INT,
    category_id INT,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    modified_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP,
    FOREIGN KEY (category_id) REFERENCES Product_Category(id)
);

-- Create Discount table
CREATE TABLE Discount (
    id INT AUTO_INCREMENT PRIMARY KEY,
    name VARCHAR(255),
    description TEXT,
    discount_percent DECIMAL(5,2),
    active BOOLEAN,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    modified_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP
);
