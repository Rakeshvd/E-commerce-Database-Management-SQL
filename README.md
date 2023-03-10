# E-commerce Database Management (SQL)



## Basic Structure

We will create a simple e-commerce database for this project. Here is the database schema:

![ecommerce database schema drawio](https://user-images.githubusercontent.com/19198181/224200102-fcddd717-efaa-4f0e-9a92-da25e0f7dded.png)

ER diagram:

![e-commerce database ER diagram drawio](https://user-images.githubusercontent.com/19198181/224200190-e44f9543-d10d-49a5-bba5-ecba2e33d91b.png)


# #Creating Tables
    
CREATE TABLE Categories (
  Category_id INT(4) NOT NULL,
  Category_name VARCHAR(20) NOT NULL,
  PRIMARY KEY(Category_id)
);

![image](https://user-images.githubusercontent.com/19198181/224228651-51fdf069-b1d3-480e-9d6d-18b3c6c2ca7d.png)

CREATE TABLE Products (
  Product_id VARCHAR(4) NOT NULL,
  Product_vaiant_id INT(6) NOT NULL,
  Product_name VARCHAR(20) NOT NULL,
  Product_price VARCHAR(20) NOT NULL,
  Product_rating VARCHAR(10),   
  Category_id INT(4) NOT NULL,
  PRIMARY KEY (Product_id),
  FOREIGN KEY (Category_id) REFERENCES Categories(Category_id)
);
    
![image](https://user-images.githubusercontent.com/19198181/224204882-af101ec7-f140-4b16-839e-e40affa778c2.png)


CREATE TABLE Sellers (
  Seller_id VARCHAR(4) NOT NULL,
  Seller_name VARCHAR(20) NOT NULL,
  Seller_email VARCHAR(20) NOT NULL,
  Seller_phone VARCHAR(10) NOT NULL,   
  Product_id VARCHAR(4) NOT NULL,
  PRIMARY KEY (Seller_id)
  FOREIGN KEY (Product_id) REFERENCES Products(Product_id)
 );
    
![image](https://user-images.githubusercontent.com/19198181/224205285-001a8118-1944-4380-8663-1c8bcad90d27.png)


CREATE TABLE Customer (
  Customer_id VARCHAR(4) NOT NULL,
  Customer_first_name VARCHAR(10) NOT NULL,
  Customer_last_name VARCHAR(10) NOT NULL,
  Customer_phone VARCHAR(10) NOT NULL,
  Customer_email NUMBER(15) NOT NULL,
  PRIMARY KEY (Customer_id),
 );
   
![image](https://user-images.githubusercontent.com/19198181/224205724-440115cf-0df7-4139-bd97-2e945355d8cd.png)


CREATE TABLE Carts (
  Cart_id VARCHAR(4) NOT NULL,
  Product_quantity INT NOT NULL,
  Product_id VARCHAR(4) NOT NULL,
  Cart_total_amount FLOAT,
  PRIMARY KEY(Cart_id),
  FOREIGN KEY(Product_id) REFERENCES Products(Product_id)
);


![image](https://user-images.githubusercontent.com/19198181/224206544-cbb2b99e-9953-40c8-8328-e102e1d68602.png)

CREATE TABLE Orders (
  Order_id VARCHAR(10) NOT NULL,
  Order_date DATE	NOT NULL,
  Order_status VARCHAR NOT NULL,
  Order_amount FLOAT,
  Product_id VARCHAR(4) NOT NULL,
  Customer_id VARCHAR(4) NOT NULL,
  PRIMARY KEY(Order_id),
  FOREIGN KEY (Product_id) REFERENCES Products(Product_id),
  FOREIGN KEY (Customer_id) REFERENCES Customers(Customer_id)
);

![image](https://user-images.githubusercontent.com/19198181/224207323-82b87641-1987-4c8e-b624-d927c526243d.png)

CREATE TABLE Payments (
  Payment_id INT(6) NOT NULL,
  Payment_date DATE NOT NULL,
  Payment_amount FLOAT NOT NULL,
  Payment_method VARCHAR (10) NOT NULL,
  Payment_status VARCHAR (10) NOT NULL,
  Order_id VARCHAR(10) NOT NULL,
  Cart_id VARCHAR(4) NOT NULL,
  PRIMARY KEY (Payment_id),
  FOREIGN KEY (Order_id) REFERENCES Orders(Order_id),
  FOREIGN KEY (Cart_id) REFERENCES Carts(Cart_id)
 );

![image](https://user-images.githubusercontent.com/19198181/224208392-ff41ff93-8741-42f3-afca-b9564e99b10f.png)

CREATE TABLE Deliveries (
  Delivery_id CHAR(6) NOT NULL,
  Delivery_date DATE NOT NULL,
  Delivery_address VARCHAR (30) NOT NULL,
  Delivery_status VARHCHAR (10) NOT NULL,
  Order_id VARCHAR(10) NOT NULL,
  PRIMARY KEY (Delivery_id),
  FOREIGN KEY (Order_id) REFERENCES Orders(Order_id)
);
 
 
![image](https://user-images.githubusercontent.com/19198181/224210475-e731f416-864f-40bc-8828-b4a38da841aa.png)

 

# #Inserting Values

INSERT INTO Categories Values (9001, 'Home appliances');
INSERT INTO Categories Values (9002, 'Personal Care');
INSERT INTO Categories Values (9003, 'Sports');
INSERT INTO Categories Values (9004, 'Medicines');
INSERT INTO Categories Values (9005, 'Toys');


![image](https://user-images.githubusercontent.com/19198181/224220643-2751cc28-1196-4676-8cb4-83969e6a234c.png)


INSERT INTO Products Values ('P001',101,'LG REFREGERATOR 100L','20000','4.5',9001);
INSERT INTO Products Values ('P002',102,'PHILIPS TRIMMER T5','2000','4.1',9002);
INSERT INTO Products Values ('P003',103,'THE NORTH FACE SHOE LEATHER','14999','4.8',9003);
INSERT INTO Products Values ('P004',104,'VIT D 1 STRIP','200','4.9',9004);
INSERT INTO Products Values ('P005',105,'TALKING CACTUS','899','3.9',9005);

![image](https://user-images.githubusercontent.com/19198181/224228796-48753810-9e9b-4552-aedd-9109ef164ae1.png)
