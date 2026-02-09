# SQL Cheatsheet for QA

> **Quick reference for common SQL queries used in testing**

---

## 🔍 Basic SELECT Queries

### Get All Data from Table
```sql
SELECT * FROM users;
```

### Get Specific Columns
```sql
SELECT first_name, last_name, email FROM users;
```

### Get Unique Values
```sql
SELECT DISTINCT status FROM orders;
```

### Limit Results
```sql
SELECT * FROM users LIMIT 10;
```

---

## 🎯 WHERE Clause (Filtering)

### Exact Match
```sql
SELECT * FROM orders WHERE order_id = 'ORD-001';
```

### Numeric Comparison
```sql
SELECT * FROM products WHERE price > 500;
SELECT * FROM products WHERE price >= 100 AND price <= 1000;
```

### Text Matching (Case-Insensitive)
```sql
SELECT * FROM users WHERE email LIKE '%@gmail.com';
SELECT * FROM users WHERE first_name LIKE 'John%';  -- Starts with John
SELECT * FROM users WHERE last_name LIKE '%son';    -- Ends with son
```

### Multiple Conditions
```sql
-- AND: Both must be true
SELECT * FROM users 
WHERE status = 'active' AND country = 'Thailand';

-- OR: At least one must be true
SELECT * FROM users 
WHERE status = 'active' OR status = 'pending';

-- IN: Match any value in list
SELECT * FROM orders 
WHERE status IN ('pending', 'processing', 'shipped');
```

### NULL Checks
```sql
SELECT * FROM users WHERE phone IS NULL;
SELECT * FROM users WHERE phone IS NOT NULL;
```

### Date Filtering
```sql
SELECT * FROM orders WHERE created_at > '2026-01-01';
SELECT * FROM orders WHERE created_at BETWEEN '2026-01-01' AND '2026-01-31';
```

---

## 📊 Sorting & Grouping

### ORDER BY (Sorting)
```sql
-- Ascending (oldest to newest)
SELECT * FROM users ORDER BY created_at ASC;

-- Descending (newest to oldest)
SELECT * FROM users ORDER BY created_at DESC;

-- Multiple columns
SELECT * FROM users ORDER BY country ASC, created_at DESC;
```

### COUNT Records
```sql
-- Count all rows
SELECT COUNT(*) FROM users;

-- Count non-null values
SELECT COUNT(email) FROM users;

-- Count with condition
SELECT COUNT(*) FROM orders WHERE status = 'completed';
```

### GROUP BY
```sql
-- Count users by status
SELECT status, COUNT(*) as total
FROM users
GROUP BY status;

-- Sum orders by customer
SELECT user_id, SUM(total_amount) as total_spent
FROM orders
GROUP BY user_id;
```

---

## 🔗 JOINs (Combining Tables)

### INNER JOIN (Only Matching Records)
```sql
SELECT u.email, o.order_id, o.total_amount
FROM users u
INNER JOIN orders o ON u.user_id = o.user_id;
```

### LEFT JOIN (All from Left, Matching from Right)
```sql
-- Get all users, even those without orders
SELECT u.email, o.order_id, o.total_amount
FROM users u
LEFT JOIN orders o ON u.user_id = o.user_id;
```

### Multiple JOINs
```sql
SELECT 
    u.email,
    o.order_id,
    oi.product_name,
    oi.quantity
FROM users u
INNER JOIN orders o ON u.user_id = o.user_id
INNER JOIN order_items oi ON o.order_id = oi.order_id;
```

---

## ✅ Common QA Verification Queries

### Verify User Registration
```sql
-- Check if user exists
SELECT * FROM users 
WHERE email = 'test@example.com';

-- Check user details
SELECT user_id, email, status, created_at 
FROM users 
WHERE email = 'test@example.com';
```

### Verify Order Creation
```sql
-- Get latest order for user
SELECT * FROM orders 
WHERE user_id = 123 
ORDER BY created_at DESC 
LIMIT 1;

-- Verify order total matches items
SELECT 
    o.order_id,
    o.total_amount,
    SUM(oi.price * oi.quantity) as calculated_total
FROM orders o
INNER JOIN order_items oi ON o.order_id = oi.order_id
WHERE o.order_id = 'ORD-001'
GROUP BY o.order_id, o.total_amount;
```

### Verify Payment Status
```sql
SELECT 
    o.order_id,
    o.status as order_status,
    p.status as payment_status,
    p.amount
FROM orders o
LEFT JOIN payments p ON o.order_id = p.order_id
WHERE o.order_id = 'ORD-001';
```

### Check Duplicate Records
```sql
-- Find duplicate emails
SELECT email, COUNT(*) as count
FROM users
GROUP BY email
HAVING COUNT(*) > 1;
```

### Get Latest Records
```sql
-- Latest 5 users
SELECT * FROM users 
ORDER BY created_at DESC 
LIMIT 5;

-- Today's registrations
SELECT * FROM users 
WHERE DATE(created_at) = CURDATE();
```

---

## 🧪 Testing Specific Scenarios

### Test Account Cleanup
```sql
-- Find test accounts
SELECT * FROM users 
WHERE email LIKE '%test%' OR email LIKE '%qa%';

-- Delete test data (use with caution!)
DELETE FROM users 
WHERE email LIKE '%@testmail.com';
```

### Verify Data Integrity
```sql
-- Orders without users (orphaned records)
SELECT o.* 
FROM orders o
LEFT JOIN users u ON o.user_id = u.user_id
WHERE u.user_id IS NULL;

-- Check for invalid statuses
SELECT * FROM orders 
WHERE status NOT IN ('pending', 'processing', 'completed', 'cancelled');
```

### Performance Testing Data
```sql
-- Count records by date
SELECT DATE(created_at) as date, COUNT(*) as total
FROM orders
GROUP BY DATE(created_at)
ORDER BY date DESC;

-- Find large orders
SELECT * FROM orders 
WHERE total_amount > 10000
ORDER BY total_amount DESC;
```

---

## 📈 Aggregate Functions

```sql
-- SUM
SELECT SUM(total_amount) as total_revenue FROM orders;

-- AVG
SELECT AVG(price) as average_price FROM products;

-- MIN / MAX
SELECT MIN(price) as cheapest, MAX(price) as most_expensive 
FROM products;

-- Multiple aggregates
SELECT 
    COUNT(*) as total_orders,
    SUM(total_amount) as total_revenue,
    AVG(total_amount) as average_order_value
FROM orders
WHERE status = 'completed';
```

---

## 🔐 Quick Tips for QA

### Before Testing
```sql
-- Check current state
SELECT * FROM users WHERE email = 'test@example.com';
```

### After Action (e.g., Create User)
```sql
-- Verify new record
SELECT * FROM users 
WHERE email = 'test@example.com' 
ORDER BY created_at DESC LIMIT 1;
```

### Compare UI vs Database
```sql
-- Get exact values to compare with UI
SELECT 
    email,
    first_name,
    last_name,
    status,
    created_at
FROM users 
WHERE user_id = 123;
```

---

## ⚠️ Safety Tips

✅ **Always use WHERE clause with DELETE/UPDATE**
```sql
-- ❌ DANGEROUS - Deletes everything!
DELETE FROM users;

-- ✅ SAFE - Deletes specific record
DELETE FROM users WHERE email = 'test@example.com';
```

✅ **Test with SELECT first**
```sql
-- First, check what will be affected
SELECT * FROM users WHERE email LIKE '%test%';

-- Then, if correct, delete
DELETE FROM users WHERE email LIKE '%test%';
```

✅ **Use transactions in test environment**
```sql
BEGIN;
DELETE FROM test_users WHERE created_at < '2026-01-01';
-- Check results
SELECT COUNT(*) FROM test_users;
-- If good: COMMIT; If bad: ROLLBACK;
```

---

## 🎓 Practice Scenarios

### Scenario 1: User Registration Verification
```sql
-- 1. Check if email already exists (should be 0)
SELECT COUNT(*) FROM users WHERE email = 'newuser@test.com';

-- 2. After registration, verify user created
SELECT * FROM users WHERE email = 'newuser@test.com';

-- 3. Verify status is correct
SELECT status FROM users WHERE email = 'newuser@test.com';
-- Expected: 'active' or 'pending'
```

### Scenario 2: Order Flow Verification
```sql
-- 1. Verify order created
SELECT * FROM orders WHERE user_id = 123 ORDER BY created_at DESC LIMIT 1;

-- 2. Verify order items
SELECT * FROM order_items WHERE order_id = 'ORD-001';

-- 3. Verify total calculation
SELECT 
    o.order_id,
    o.total_amount as recorded_total,
    SUM(oi.price * oi.quantity) as calculated_total
FROM orders o
INNER JOIN order_items oi ON o.order_id = oi.order_id
WHERE o.order_id = 'ORD-001'
GROUP BY o.order_id, o.total_amount;
```

---

**Pro Tip:** Always bookmark this cheatsheet for quick reference during testing! 🚀
