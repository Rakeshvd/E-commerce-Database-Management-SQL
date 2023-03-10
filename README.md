# E-commerce Database Management (SQL)



## Basic Structure

We will create a simple e-commerce database for this project. Here is the database schema: 

![ecommerce database schema drawio](https://user-images.githubusercontent.com/19198181/224200102-fcddd717-efaa-4f0e-9a92-da25e0f7dded.png)

ER diagram:

![e-commerce database ER diagram drawio](https://user-images.githubusercontent.com/19198181/224200190-e44f9543-d10d-49a5-bba5-ecba2e33d91b.png)


## Creating Tables  

    
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
  FOREIGN KEY (Customer_id) REFERENCES Customer(Customer_id)  
);
  
![image](https://user-images.githubusercontent.com/19198181/224310269-d1b8d66d-4603-4361-bdc7-287f1243143d.png)


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

 

## Inserting Values  

INSERT INTO Categories Values (9001, 'Home appliances');  
INSERT INTO Categories Values (9002, 'Personal Care');  
INSERT INTO Categories Values (9003, 'Sports');  
INSERT INTO Categories Values (9004, 'Medicines');  
INSERT INTO Categories Values (9005, 'Toys');  


![image](https://user-images.githubusercontent.com/19198181/224220643-2751cc28-1196-4676-8cb4-83969e6a234c.png)


INSERT INTO Products Values ('P001',101,'LG REFREGERATOR 100L','20000','4.5',9001);  
INSERT INTO Products Values ('P002',102,'PHILIPS TRIMMER T5','2000','4.1',9002);  
INSERT INTO Products Values ('P003',103,'THE NORTH FACE SHOE LEATHER','14999','4.8 ',9003);  
INSERT INTO Products Values ('P004',104,'VIT D 1 STRIP','200','4.9',9004);  
INSERT INTO Products Values ('P005',105,'TALKING CACTUS','899','3.9',9005);  

![image](https://user-images.githubusercontent.com/19198181/224228796-48753810-9e9b-4552-aedd-9109ef164ae1.png)

INSERT INTO Sellers Values ('S001','SELLER_A','seller_a@ecommerce.com','+919123456789','P001');  
INSERT INTO Sellers Values ('S002','SELLER_B','seller_b@ecommerce.com','+919234567890','P002');  
INSERT INTO Sellers Values ('S003','SELLER_C','seller_c@ecommerce.com','+919345678901','P003');  
INSERT INTO Sellers Values ('S004','SELLER_D','seller_d@ecommerce.com','+919456789012','P004');  
INSERT INTO Sellers Values ('S005','SELLER_E','seller_e@ecommerce.com','+919567890123','P005');  

![image](https://user-images.githubusercontent.com/19198181/224303536-bfde0854-0ca8-4247-abc7-a7f35687cc21.png)
  
INSERT INTO Customer Values ('C001','Abhishek','Singh','+919678901234','Abhishek@gmail.com');  
INSERT INTO Customer Values ('C002','Vivek','Kumar','+919678413233','Vivek@gmail.com');  
INSERT INTO Customer Values ('C003','Drishti','Kumari','+919672142218','Drishti@gmail.com');  
INSERT INTO Customer Values ('C004','Sneha','Agarwal','+919241422678','Sneha@gmail.com');  
INSERT INTO Customer Values ('C005','Singam','G.H.','+919678312342','Singam@gmail.com');  

We accidently defined datatype of Customer_email as number instead of varchar.   
  
Let's alter the data type using:  
ALTER TABLE Customer  
ALTER COLUMN Customer_email varchar(20);  

![image](https://user-images.githubusercontent.com/19198181/224307085-da570d2e-471a-454a-b80b-ef797f26ed19.png)
  
Now let's insert the values for Customer table.  

![image](https://user-images.githubusercontent.com/19198181/224308248-8aa556b9-268c-4fd3-860d-d3771a0dbacd.png)
  

INSERT INTO Carts Values ('CRT1',2,'P001',40000.0);    
INSERT INTO Carts Values ('CRT2',10,'P002',18500.4);    
INSERT INTO Carts Values ('CRT3',1,'P003',13000.0);    
INSERT INTO Carts Values ('CRT4',4,'P004',350.0);  
INSERT INTO Carts Values ('CRT5',5,'P005',500.0);  

![image](https://user-images.githubusercontent.com/19198181/224309039-c247911e-1332-4179-890e-6245a1602bc8.png)  

INSERT INTO Orders Values ('ORDER1','2023-01-01','Delivery pending',40000.0,'P001','C001');  
INSERT INTO Orders Values ('ORDER2','2023-04-02','Shipped',18500.4,'P002','C002');  
INSERT INTO Orders Values ('ORDER3','2023-06-02','Delivered',13000.0,'P003','C003');  
INSERT INTO Orders Values ('ORDER4','2023-02-14','Order confirmed',350.0,'P004','C004');  
INSERT INTO Orders Values ('ORDER5','2023-12-11','Order cancelled',500.0,'P005','C005');  
  
![image](https://user-images.githubusercontent.com/19198181/224310929-59cb270b-f3bc-473a-bf08-69bd62f531f6.png)


INSERT INTO Payments Values ('PAY001','2023-01-01',40000.0,'Credit card', 'Success', 'ORDER1','CRT1');  
INSERT INTO Payments Values ('PAY002','2023-04-02',18500.4,'Debit card', 'Success', 'ORDER2','CRT2');  
INSERT INTO Payments Values ('PAY003','2023-06-02',13000.0,'UPI', 'Failed', 'ORDER3','CRT3');  
INSERT INTO Payments Values ('PAY004','2023-02-18',350.0,'COD', 'Success', 'ORDER4','CRT4');  
INSERT INTO Payments Values ('PAY005','2023-12-11',500.0,'UPI', 'Success', 'ORDER5','CRT5');  

![image](https://user-images.githubusercontent.com/19198181/224311836-ebc5b26a-2d0b-4e3b-8fc0-a241eb51b4d1.png)

INSERT INTO Deliveries Values ('DEL1','2023-01-06','320, abc apartment,Bangalore,560001','Recieved','ORDER1');  
INSERT INTO Deliveries Values ('DEL2','2023-04-06','321, 123 apartment,Bangalore,560002','In-progrees','ORDER2');  
INSERT INTO Deliveries Values ('DEL3','2023-06-12','322, pqr apartment,Bangalore, 560003','In-progrees/Delayed','ORDER3');  
INSERT INTO Deliveries Values ('DEL4','2023-02-22','323, rts apartment,Pune, 231002','Recieved','ORDER4');  
INSERT INTO Deliveries Values ('DEL5','2023-12-15','324, qwerty apartment,Mysore, 553021','Recieved','ORDER5');  
  
![image](https://user-images.githubusercontent.com/19198181/224315690-813d243e-3a0a-4a40-9c19-488bea13f263.png)
  

## Quering Data
**
1. How many orders did we successfully deliver during Mar 2023 to Dec 2023 and what are their order_ids? **  
Select count(order_id), order_id from Orders where Order_status = "Delivered"

![image](https://user-images.githubusercontent.com/19198181/224321893-5505f42d-7f1b-4889-8afa-b7e07244c352.png)

**
2. How many orders got cancelled till date and what was the amount of that order?**  
Select count(Orders.Order_id), Payments.Payment_amount from Orders inner join Payments on Orders.Order_id = Payments.Order_id where Order_status = 'Order cancelled';  

![image](https://user-images.githubusercontent.com/19198181/224323426-adf89e23-8cb5-489d-99da-aaf39ed81fbd.png)


3. Select the customers who have previous shopped for rupees 10000 or more, so we can send a personalized discount code for their next purchase  
Select Customer.Customer_email, Orders.Order_amount from  Customer inner join Orders on Customer.Customer_id = Orders.Customer_id where Order_amount >= 10000;  

![image](https://user-images.githubusercontent.com/19198181/224324253-f1b98155-931f-4023-90d8-7f8823d7a16a.png)  

4. Find out how many orders got delivered outside Bangalore till date  
Select Count(Order_id) from Deliveries where Delivery_address NOT like '%Bangalore%'   

![image](https://user-images.githubusercontent.com/19198181/224344015-a5a59cb3-61e3-4270-bf08-ae2f7ad9838a.png)

5. Order all the products by their price in a descending order  
  
![image](https://user-images.githubusercontent.com/19198181/224345305-461da26f-de7d-405d-a82d-ffcfd27e4c4d.png)  

Notice the order is incorrect. This is because we have defined the datatype of Product_price as float.   
We will need to inform the system to consider the values of Product_price as numbers. This can be done as below:  

SELECT * FROM Products ORDER BY cast(Product_price as float) desc;  

![image](https://user-images.githubusercontent.com/19198181/224345841-fabd988a-429e-41b3-be9d-244cdf5377a5.png)

6. Seller_A has wants to change their email id to seller_new_a@ecommerce.com. Write a query for this.  

Update Sellers  
Set Seller_email= 'seller_new_a@ecommerce.com'  
where Seller_name = "SELLER_A";  
Select * from Sellers;  

![image](https://user-images.githubusercontent.com/19198181/224357227-fcdd897d-91b6-45e7-9a4d-ffad745eb5c4.png)

7. Calculate the total order value for the year 2023  
Select sum(Order_amount) from Orders where Order_status != "Order cancelled" AND Order_status != "Returned"  

![image](https://user-images.githubusercontent.com/19198181/224358468-d941ec60-83f7-4231-8b4c-2ed0af115b01.png)

8. Find out if any sellers are selling any product with product price less than 500 rupees  
SELECT Seller_id, Seller_name, Product_name FROM Sellers INNER JOIN Products on Products.Product_id = Sellers.Product_id
WHERE EXISTS (SELECT Product_name FROM Products where Products.Product_id = Sellers.Product_id AND cast(Product_price as float) < 500);

![image](https://user-images.githubusercontent.com/19198181/224360785-e84a943e-2dd5-4e30-b33e-c5ac12b2d5f1.png)


8. Get all the products sold (order must be successfuly delivered) from 2023-01-01 to 2023-06-01  

SELECT Product_name from Orders inner join Products where Orders.Product_id = Products.Product_id AND Order_status != "Order cancelled" AND Order_status != "Returned" AND Order_date >= '2023-01-01' AND Order_date <= '2023-06-01';  

![image](https://user-images.githubusercontent.com/19198181/224366849-fe300336-b462-491d-be60-0f73b9e6ecfa.png)
  
