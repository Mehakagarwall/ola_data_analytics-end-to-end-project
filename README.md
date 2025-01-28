# ola_data_analytics
## SQL Questions:

1. Retrieve all successful bookings:
2. Find the average ride distance for each vehicle type:
3. Get the total number of cancelled rides by customers:
4. List the top 5 customers who booked the highest number of rides:
5. Get the number of rides cancelled by drivers due to personal and car-related issues:
6. Find the maximum and minimum driver ratings for Prime Sedan bookings:
7. Retrieve all rides where payment was made using UPI:
8. Find the average customer rating per vehicle type:
9. Calculate the total booking value of rides completed successfully:
10. List all incomplete rides along with the reason:

## Power BI Questions:

1. Ride Volume Over Time
2. Booking Status Breakdown
3. Top 5 Vehicle Types by Ride Distance
4. Average Customer Ratings by Vehicle Type
5. cancelled Rides Reasons
6. Revenue by Payment Method
7. Top 5 Customers by Total Booking Value
8. Ride Distance Distribution Per Day
9. Driver Ratings Distribution
10. Customer vs. Driver Ratings

#1. Retrieve all successful bookings:

    Create View Successful_Bookings As
    SELECT * FROM bookings
    WHERE Booking_Status = 'Success';

#2. Find the average ride distance for each vehicle type:

    Create View ride_distance_for_each_vehicle As
    SELECT Vehicle_Type, AVG(Ride_Distance)
    as avg_distance FROM bookings
    GROUP BY Vehicle_Type;

#3. Get the total number of cancelled rides by customers:

    Create View cancelled_rides_by_customers As
    SELECT COUNT(*) FROM bookings
    WHERE Booking_Status = 'cancelled by Customer';

#4. List the top 5 customers who booked the highest number of rides:

    Create View Top_5_Customers As
    SELECT Customer_ID, COUNT(Booking_ID) as total_rides
    FROM bookings
    GROUP BY Customer_ID
    ORDER BY total_rides DESC LIMIT 5;

 #5. Get the number of rides cancelled by drivers due to personal and car-related issues:
 
    Create View Rides_cancelled_by_Drivers_P_C_Issues As
    SELECT COUNT(*) FROM bookings
    WHERE cancelled_Rides_by_Driver = 'Personal & Car related issue';  

#6. Find the maximum and minimum driver ratings for Prime Sedan bookings:

    Create View Max_Min_Driver_Rating As
    SELECT MAX(Driver_Ratings) as max_rating,
    MIN(Driver_Ratings) as min_rating
    FROM bookings WHERE Vehicle_Type = 'Prime Sedan';

#7. Retrieve all rides where payment was made using UPI:

    Create View UPI_Payment As
    SELECT * FROM bookings
    WHERE Payment_Method = 'UPI';

#8. Find the average customer rating per vehicle type:

    Create View AVG_Cust_Rating As
    SELECT Vehicle_Type, AVG(Customer_Rating) as avg_customer_rating
    FROM bookings
    GROUP BY Vehicle_Type;

#9. Calculate the total booking value of rides completed successfully:

    Create View total_successful_ride_value As
    SELECT SUM(Booking_Value) as total_successful_ride_value
    FROM bookings
    WHERE Booking_Status = 'Success';

#10. List all incomplete rides along with the reason:

    Create View Incomplete_Rides_Reason As
    SELECT Booking_ID, Incomplete_Rides_Reason
    FROM bookings
    WHERE Incomplete_Rides = 'Yes';

# For the Power BI the qiestions where divide into 5 views
## 1.Overall
- Ride Volume Over Time
- Booking Status Breakdown
  
  ![image](https://github.com/user-attachments/assets/934f75d9-5d2c-487f-a2e1-7d88181a2863)

  
## 2. Vehicle Type
- Top 5 Vehicle Types by Ride Distance

  ![image](https://github.com/user-attachments/assets/b30f8ef3-e976-491a-ae6b-8dcb2fede14a)

## 3. Revenue
- Revenue by Payment Method
- Top 5 Customers by Total Booking Value
- Ride Distance Distribution Per Day

  ![image](https://github.com/user-attachments/assets/93af417f-7aa2-4fb1-9ad9-59bd6523ed76)

## 4. Cancellation
- Cancelled Rides Reasons (Customer)
- cancelled Rides Reasons(Drivers)

  ![image](https://github.com/user-attachments/assets/36d313f9-050d-4f05-9685-6b169c624226)

## 5. Ratings
- Driver Ratings
- Customer Ratings

![image](https://github.com/user-attachments/assets/a8c602ca-be14-4f68-832b-b8ba0f62539b)















