CREATE DATABASE hotelreservation;
USE hotelreservation;
SELECT * FROM `hotel reservations`;

-- Display the first 10 bookings
SELECT 
    BOOKING_ID
FROM
    `HOTEL RESERVATIONS`
LIMIT 10;
-- Find the average room price by market segment type
SELECT
    MARKET_SEGMENT_TYPE,
    ROUND(AVG(AVG_PRICE_PER_ROOM), 2) AS avg_price_per_room
FROM
    `HOTEL RESERVATIONS`
GROUP BY
    MARKET_SEGMENT_TYPE;
-- Find the top 5 most expensive bookings.
SELECT 
    BOOKING_ID, AVG_PRICE_PER_ROOM
FROM
    `HOTEL RESERVATIONS`
ORDER BY AVG_PRICE_PER_ROOM DESC
LIMIT 5;
-- Find the most commonly booked room type.
SELECT 
    ROOM_TYPE_RESERVED, COUNT(*) AS BOOKED_TYPE
FROM
    `HOTEL RESERVATIONS`
GROUP BY ROOM_TYPE_RESERVED
ORDER BY BOOKED_TYPE DESC
LIMIT 1;
-- Show monthly booking trends by year.
SELECT 
    ARRIVAL_YEAR, ARRIVAL_MONTH, COUNT(*) AS booking_trends
FROM
    `HOTEL RESERVATIONS`
GROUP BY ARRIVAL_YEAR , ARRIVAL_MONTH
ORDER BY ARRIVAL_YEAR , ARRIVAL_MONTH;
-- Identify months with the highest cancellation counts
SELECT 
    ARRIVAL_MONTH, BOOKING_STATUS, COUNT(*) AS booking_trends
FROM
    `HOTEL RESERVATIONS`
WHERE
    BOOKING_STATUS = 'Not_Cancelled'
GROUP BY ARRIVAL_MONTH , BOOKING_STATUS
ORDER BY BOOKING_STATUS;
-- Calculate running total of bookings by month.
SELECT 
    ARRIVAL_MONTH, COUNT(*) AS TOTAL_OF_BOOKINGS
FROM
    `HOTEL RESERVATIONS`
GROUP BY ARRIVAL_MONTH
ORDER BY ARRIVAL_MONTH;
-- Compare average room prices between online and offline segments.
SELECT 
    MARKET_SEGMENT_TYPE,
    ROUND(AVG(AVG_PRICE_PER_ROOM),2) AS average_room_prices
FROM
    `HOTEL RESERVATIONS`
WHERE
    MARKET_SEGMENT_TYPE IN ('ONLINE' , 'OFFLINE')
GROUP BY MARKET_SEGMENT_TYPE;
-- Detect seasonality trends in bookings.
SELECT 
    ARRIVAL_YEAR, ARRIVAL_MONTH, COUNT(*) AS TOTAL_BOOKINGS
FROM
    `HOTEL RESERVATIONS`
GROUP BY ARRIVAL_YEAR , ARRIVAL_MONTH
ORDER BY ARRIVAL_YEAR , ARRIVAL_MONTH;
-- Find room types with highest cancellation rates.
SELECT 
    ROOM_TYPE_RESERVED,
    COUNT(*) AS TOTAL_BOOKINGS,
    SUM(CASE
        WHEN BOOKING_STATUS = 'CANCELED' THEN 1
        ELSE 0
    END) AS CANCELLED_BOOKINGS,
    ROUND(SUM(CASE
                WHEN BOOKING_STATUS = 'CANCELED' THEN 1
                ELSE 0
            END) * 1.0 / COUNT(*),
            2) AS CANCELLATION_RATE
FROM
    `HOTEL RESERVATIONS`
GROUP BY ROOM_TYPE_RESERVED
ORDER BY CANCELLATION_RATE DESC
LIMIT 1;
-- Calculate the average lead time for repeated vs non-repeated guests.
SELECT
  CASE 
    WHEN repeated_guest = 1 THEN 'Repeated Guest'
    ELSE 'Non-Repeated Guest'
  END AS guest_type,
  ROUND(AVG(lead_time),2) AS avg_lead_time
FROM `HOTEL RESERVATIONS`
GROUP BY repeated_guest;
-- Use a CASE statement to categorize bookings into:Low price Medium price High price
SELECT 
    CASE
        WHEN AVG_PRICE_PER_ROOM BETWEEN 0 AND 90 THEN 'LOW  PRICE'
        WHEN AVG_PRICE_PER_ROOM BETWEEN 91 AND 170 THEN 'MEDIUM PRICE'
        ELSE 'HIGH PRICE'
    END AS CATEGORIZE_BOOKING,
    BOOKING_ID,
    AVG_PRICE_PER_ROOM
FROM
    `HOTEL RESERVATIONS`;
-- Retrieve bookings where: booking status is Not Canceled,average price per room > 120,lead time < 30    
SELECT 
    *
FROM
    `HOTEL RESERVATIONS`
WHERE
    BOOKING_STATUS = 'NOT_CANCELLED'
        AND AVG_PRICE_PER_ROOM > 120
        AND LEAD_TIME < 30;
-- Show bookings with more than 2 adults
SELECT BOOKING_ID,NO_OF_ADULTS FROM `HOTEL RESERVATIONS` WHERE NO_OF_ADULTS>2;
