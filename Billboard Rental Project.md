
new script of uuid 
```
-- Enable UUID extension
CREATE EXTENSION IF NOT EXISTS "uuid-ossp";

-- Create roles table
CREATE TABLE roles (
    role_id UUID PRIMARY KEY DEFAULT uuid_generate_v4(),
    role_name VARCHAR(50) UNIQUE NOT NULL
);

-- Insert default roles into roles table
INSERT INTO roles (role_name) VALUES 
('User'),
('Admin'),
('Owner');

-- Create documents table
CREATE TABLE documents (
    document_id UUID PRIMARY KEY DEFAULT uuid_generate_v4(),
    document TEXT NOT NULL
);

-- Create users table
CREATE TABLE users (
    user_id UUID PRIMARY KEY DEFAULT uuid_generate_v4(),
    email VARCHAR(255) UNIQUE NOT NULL,
    password VARCHAR(255) NOT NULL,
    firstname VARCHAR(100),
    lastname VARCHAR(100),
    phoneno VARCHAR(15),
    company_name VARCHAR(255),
    is_verified BOOLEAN DEFAULT FALSE,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    role_id UUID NOT NULL,
    document_id UUID,
    CONSTRAINT fk_role FOREIGN KEY (role_id) REFERENCES roles (role_id) ON DELETE CASCADE,
    CONSTRAINT fk_document FOREIGN KEY (document_id) REFERENCES documents (document_id) ON DELETE SET NULL
);

-- Create billboard table
CREATE TABLE billboard (
    billboard_id UUID PRIMARY KEY DEFAULT uuid_generate_v4(),
    size VARCHAR(50) NOT NULL,
    location TEXT NOT NULL,
    billboard_type VARCHAR(50) NOT NULL,
    price NUMERIC(10, 2) NOT NULL,
    available BOOLEAN DEFAULT TRUE,
    amenities TEXT,
    b_img TEXT,
    b_review TEXT,
    b_description TEXT,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    owner_id UUID NOT NULL,
    CONSTRAINT fk_owner FOREIGN KEY (owner_id) REFERENCES users (user_id) ON DELETE CASCADE
);

-- Create booking table
CREATE TABLE booking (
    booking_id UUID PRIMARY KEY DEFAULT uuid_generate_v4(),
    billboard_id UUID NOT NULL,
    user_id UUID NOT NULL,
    start_date DATE NOT NULL,
    end_date DATE NOT NULL,
    offered_price NUMERIC(10, 2) NOT NULL,
    status VARCHAR(10) DEFAULT 'pending',
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    CONSTRAINT fk_billboard FOREIGN KEY (billboard_id) REFERENCES billboard (billboard_id) ON DELETE CASCADE,
    CONSTRAINT fk_user FOREIGN KEY (user_id) REFERENCES users (user_id) ON DELETE CASCADE
);

-- Trigger function to update updated_at column (remains the same)
CREATE OR REPLACE FUNCTION update_updated_at_column()
RETURNS TRIGGER AS $$
BEGIN
    NEW.updated_at = CURRENT_TIMESTAMP;
    RETURN NEW;
END;
$$ LANGUAGE plpgsql;

-- Triggers (remain the same)
CREATE TRIGGER set_updated_at_users
BEFORE UPDATE ON users
FOR EACH ROW
EXECUTE FUNCTION update_updated_at_column();

CREATE TRIGGER set_updated_at_billboard
BEFORE UPDATE ON billboard
FOR EACH ROW
EXECUTE FUNCTION update_updated_at_column();

CREATE TRIGGER set_updated_at_booking
BEFORE UPDATE ON booking
FOR EACH ROW
EXECUTE FUNCTION update_updated_at_column();
```

## Insert Demo Values
```
BEGIN; -- Start transaction

-- Insert roles (if not exists)
INSERT INTO roles (role_name)
SELECT 'User' WHERE NOT EXISTS (SELECT 1 FROM roles WHERE role_name = 'User')
UNION ALL
SELECT 'Admin' WHERE NOT EXISTS (SELECT 1 FROM roles WHERE role_name = 'Admin')
UNION ALL
SELECT 'Owner' WHERE NOT EXISTS (SELECT 1 FROM roles WHERE role_name = 'Owner');

-- Insert documents
WITH docs AS (
  INSERT INTO documents (document)
  VALUES 
  ('Drivers License: John Doe'),
  ('Business Registration: Billboard Co')
  RETURNING document_id, document
)
SELECT * FROM docs; -- Store document IDs

-- Insert users
WITH user_data AS (
  INSERT INTO users (email, password, firstname, lastname, role_id, document_id)
  VALUES
  (
    'admin@example.com', 
    'hashed_admin_pwd',  -- Replace with real hash
    'Admin',
    'User',
    (SELECT role_id FROM roles WHERE role_name = 'Admin'),
    NULL
  ),
  (
    'owner@example.com',
    'hashed_owner_pwd',
    'John',
    'Doe',
    (SELECT role_id FROM roles WHERE role_name = 'Owner'),
    (SELECT document_id FROM documents WHERE document LIKE 'Business Registration%')
  ),
  (
    'user@example.com',
    'hashed_user_pwd',
    'Regular',
    'User',
    (SELECT role_id FROM roles WHERE role_name = 'User'),
    (SELECT document_id FROM documents WHERE document LIKE 'Drivers License%')
  )
  RETURNING user_id, email
)
SELECT * FROM user_data; -- Store user IDs

-- Insert billboards
WITH billboards AS (
  INSERT INTO billboard (size, location, billboard_type, price, owner_id, b_description)
  VALUES
  (
    '10x20', 
    'Times Square, NYC', 
    'Digital', 
    5000.00,
    (SELECT user_id FROM users WHERE email = 'owner@example.com'),
    'Premium digital billboard in high-traffic area'
  ),
  (
    '8x16',
    'Sunset Blvd, LA',
    'Static',
    2500.00,
    (SELECT user_id FROM users WHERE email = 'owner@example.com'),
    'Traditional billboard with vinyl printing'
  )
  RETURNING billboard_id, location
)
SELECT * FROM billboards; -- Store billboard IDs

-- Insert bookings
INSERT INTO booking (billboard_id, user_id, start_date, end_date, offered_price, status)
SELECT 
  b.billboard_id,
  u.user_id,
  dates.start_date::DATE,
  dates.end_date::DATE,
  dates.price,
  dates.status
FROM (
  VALUES
    ('Times Square%', 'user@example.com', '2023-11-01', '2023-11-30', 5500.00, 'confirmed'),
    ('Sunset Blvd%', 'user@example.com', '2023-12-01', '2024-01-31', 3000.00, 'pending')
) AS dates(location_pattern, email, start_date, end_date, price, status)
JOIN billboard b ON b.location LIKE dates.location_pattern
JOIN users u ON u.email = dates.email;

COMMIT; -- Commit transaction

-- Verification Queries
SELECT * FROM roles;
SELECT * FROM documents;
SELECT * FROM users;
SELECT * FROM billboard;
SELECT * FROM booking;
```


add gender and locality in users table
```
/*============== EXTENSIONS & CLEANUP ==============*/  
CREATE EXTENSION IF NOT EXISTS "uuid-ossp";  
DROP TABLE IF EXISTS locality;  -- Remove obsolete table  
  
/*============== ENUM TYPE ==============*/  
CREATE TYPE gender_type AS ENUM (  
    'Male',  
    'Female'  
    );  
  
/*============== CORE TABLES ==============*/  
-- Security Roles  
CREATE TABLE roles (  
                       role_id UUID PRIMARY KEY DEFAULT uuid_generate_v4(),  
                       role_name VARCHAR(50) UNIQUE NOT NULL  
);  
  
-- Document Storage  
CREATE TABLE documents (  
                           document_id UUID PRIMARY KEY DEFAULT uuid_generate_v4(),  
                           document TEXT   
);  
  
-- User Accounts  
CREATE TABLE users (  
                       user_id UUID PRIMARY KEY DEFAULT uuid_generate_v4(),  
                       email VARCHAR(255) UNIQUE NOT NULL,  
                       password VARCHAR(255) NOT NULL,  
                       firstname VARCHAR(100),  
                       lastname VARCHAR(100),  
                       gender gender_type,  
                       phoneno VARCHAR(15),  
                       phone_verified BOOLEAN DEFAULT FALSE,  
                       company_name VARCHAR(255),  
                       is_verified BOOLEAN DEFAULT FALSE,  
                       locality VARCHAR(255),  
                       created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,  
                       updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,  
                       role_id UUID NOT NULL REFERENCES roles(role_id) ON DELETE CASCADE,  
                       document_id UUID REFERENCES documents(document_id) ON DELETE SET NULL,  
                       CHECK (phoneno ~ '^\+?[0-9]{10,15}$')  
);  
  
/*============== BILLBOARD SYSTEM ==============*/  
-- Billboard Listings  
CREATE TABLE billboard (  
                           billboard_id UUID PRIMARY KEY DEFAULT uuid_generate_v4(),  
                           size VARCHAR(50) NOT NULL,  
                           location TEXT NOT NULL,  
                           billboard_type VARCHAR(50) NOT NULL,  
                           price NUMERIC(10, 2) NOT NULL,  
                           available BOOLEAN DEFAULT TRUE,  
                           amenities TEXT,  
                           b_img TEXT,  
                           b_review TEXT,  
                           b_description TEXT,  
                           created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,  
                           updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,  
                           owner_id UUID NOT NULL REFERENCES users(user_id) ON DELETE CASCADE  
);  
  
-- Booking System  
CREATE TABLE booking (  
                         booking_id UUID PRIMARY KEY DEFAULT uuid_generate_v4(),  
                         billboard_id UUID NOT NULL REFERENCES billboard(billboard_id) ON DELETE CASCADE,  
                         user_id UUID NOT NULL REFERENCES users(user_id) ON DELETE CASCADE,  
                         start_date DATE NOT NULL,  
                         end_date DATE NOT NULL,  
                         offered_price NUMERIC(10, 2) NOT NULL,  
                         status VARCHAR(10) DEFAULT 'pending',  
                         created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,  
                         updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP  
);  
  
/*============== SYSTEM INITIALIZATION ==============*/  
-- Default Roles  
INSERT INTO roles (role_name) VALUES  
                                  ('User'),  
                                  ('Admin'),  
                                  ('Owner');  
  
/*============== AUTOMATION ==============*/  
-- Universal Update Trigger  
CREATE OR REPLACE FUNCTION update_timestamp()  
    RETURNS TRIGGER AS $$  
BEGIN  
    NEW.updated_at = CURRENT_TIMESTAMP;  
    RETURN NEW;  
END;  
$$ LANGUAGE plpgsql;  
  
-- Apply to All Tables  
CREATE TRIGGER users_update  
    BEFORE UPDATE ON users FOR EACH ROW EXECUTE FUNCTION update_timestamp();  
  
CREATE TRIGGER billboard_update  
    BEFORE UPDATE ON billboard FOR EACH ROW EXECUTE FUNCTION update_timestamp();  
  
CREATE TRIGGER booking_update  
    BEFORE UPDATE ON booking FOR EACH ROW EXECUTE FUNCTION update_timestamp();  
  
/*============== OPTIMIZATION ==============*/  
-- Essential Indexes  
CREATE INDEX users_location_idx ON users(locality);  
CREATE INDEX billboard_price_idx ON billboard(price);  
CREATE INDEX booking_dates_idx ON booking USING BRIN (start_date, end_date);
```
## Updated
```
/*============== EXTENSIONS & CLEANUP ==============*/  
CREATE EXTENSION IF NOT EXISTS "uuid-ossp";  
DROP TABLE IF EXISTS locality;  -- Remove obsolete table  
  
/*============== ENUM TYPE ==============*/  
CREATE TYPE gender_type AS ENUM (  
    'Male',  
    'Female'  
);  
  
/*============== CORE TABLES ==============*/  
-- Security Roles  
CREATE TABLE roles (  
    role_name VARCHAR(50) PRIMARY KEY  
);  
  
-- Document Storage  
CREATE TABLE documents (  
    document_id UUID PRIMARY KEY DEFAULT uuid_generate_v4(),  
    document TEXT   
);  
  
-- User Accounts  
CREATE TABLE users (  
    user_id UUID PRIMARY KEY DEFAULT uuid_generate_v4(),  
    email VARCHAR(255) UNIQUE NOT NULL,  
    password VARCHAR(255) NOT NULL,  
    firstname VARCHAR(100),  
    lastname VARCHAR(100),  
    gender gender_type,  
    phoneno VARCHAR(15),  
    phone_verified BOOLEAN DEFAULT FALSE,  
    company_name VARCHAR(255),  
    is_verified BOOLEAN DEFAULT FALSE,  
    locality VARCHAR(255),  
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,  
    updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,  
    role_name VARCHAR(50) NOT NULL DEFAULT 'Admin' REFERENCES roles(role_name) ON DELETE SET DEFAULT,  
    document_id UUID REFERENCES documents(document_id) ON DELETE SET NULL,  
    CHECK (phoneno ~ '^\+?[0-9]{10,15}$')  
);  
  
/*============== BILLBOARD SYSTEM ==============*/  
-- Billboard Listings  
CREATE TABLE billboard (  
    billboard_id UUID PRIMARY KEY DEFAULT uuid_generate_v4(),  
    size VARCHAR(50) NOT NULL,  
    location TEXT NOT NULL,  
    billboard_type VARCHAR(50) NOT NULL,  
    price NUMERIC(10, 2) NOT NULL,  
    available BOOLEAN DEFAULT TRUE,  
    amenities TEXT,  
    b_img TEXT,  
    b_review TEXT,  
    b_description TEXT,  
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,  
    updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,  
    owner_id UUID NOT NULL REFERENCES users(user_id) ON DELETE CASCADE  
);  
  
-- Booking System  
CREATE TABLE booking (  
    booking_id UUID PRIMARY KEY DEFAULT uuid_generate_v4(),  
    billboard_id UUID NOT NULL REFERENCES billboard(billboard_id) ON DELETE CASCADE,  
    user_id UUID NOT NULL REFERENCES users(user_id) ON DELETE CASCADE,  
    start_date DATE NOT NULL,  
    end_date DATE NOT NULL,  
    offered_price NUMERIC(10, 2) NOT NULL,  
    status VARCHAR(10) DEFAULT 'pending',  
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,  
    updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP  
);  
  
/*============== SYSTEM INITIALIZATION ==============*/  
-- Default Roles  
INSERT INTO roles (role_name) VALUES  
    ('User'),  
    ('Admin'),  
    ('Owner');  
  
/*============== AUTOMATION ==============*/  
-- Universal Update Trigger  
CREATE OR REPLACE FUNCTION update_timestamp()  
    RETURNS TRIGGER AS $$  
BEGIN  
    NEW.updated_at = CURRENT_TIMESTAMP;  
    RETURN NEW;  
END;  
$$ LANGUAGE plpgsql;  
  
-- Apply to All Tables  
CREATE TRIGGER users_update  
    BEFORE UPDATE ON users FOR EACH ROW EXECUTE FUNCTION update_timestamp();  
  
CREATE TRIGGER billboard_update  
    BEFORE UPDATE ON billboard FOR EACH ROW EXECUTE FUNCTION update_timestamp();  
  
CREATE TRIGGER booking_update  
    BEFORE UPDATE ON booking FOR EACH ROW EXECUTE FUNCTION update_timestamp();  
  
/*============== OPTIMIZATION ==============*/  
-- Essential Indexes  
CREATE INDEX users_location_idx ON users(locality);  
CREATE INDEX billboard_price_idx ON billboard(price);  
CREATE INDEX booking_dates_idx ON booking USING BRIN (start_date, end_date);

```
# NEw version removed gendertype enum
```
/*============== EXTENSIONS & CLEANUP ==============*/  
CREATE EXTENSION IF NOT EXISTS "uuid-ossp";  
DROP TABLE IF EXISTS locality;  -- Remove obsolete table  

/*============== CORE TABLES ==============*/  
-- Security Roles  
CREATE TABLE roles (  
    role_name VARCHAR(50) PRIMARY KEY  
);  

-- Document Storage  
CREATE TABLE documents (  
    document_id UUID PRIMARY KEY DEFAULT uuid_generate_v4(),  
    document TEXT   
);  

-- User Accounts  
CREATE TABLE users (  
    user_id UUID PRIMARY KEY DEFAULT uuid_generate_v4(),  
    email VARCHAR(255) UNIQUE NOT NULL,  
    password VARCHAR(255) NOT NULL,  
    firstname VARCHAR(100),  
    lastname VARCHAR(100),  
    gender VARCHAR(50),  -- Changed from enum to VARCHAR
    phoneno VARCHAR(15),  
    phone_verified BOOLEAN DEFAULT FALSE,  
    company_name VARCHAR(255),  
    is_verified BOOLEAN DEFAULT FALSE,  
    locality VARCHAR(255),  
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,  
    updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,  
    role_name VARCHAR(50) NOT NULL DEFAULT 'Admin' REFERENCES roles(role_name) ON DELETE SET DEFAULT,  
    document_id UUID REFERENCES documents(document_id) ON DELETE SET NULL,  
    CHECK (phoneno ~ '^\+?[0-9]{10,15}$')  
);  

/*============== BILLBOARD SYSTEM ==============*/  
-- Billboard Listings  
CREATE TABLE billboard (  
    billboard_id UUID PRIMARY KEY DEFAULT uuid_generate_v4(),  
    size VARCHAR(50) NOT NULL,  
    location TEXT NOT NULL,  
    billboard_type VARCHAR(50) NOT NULL,  
    price NUMERIC(10, 2) NOT NULL,  
    available BOOLEAN DEFAULT TRUE,  
    amenities TEXT,  
    b_img TEXT,  
    b_review TEXT,  
    b_description TEXT,  
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,  
    updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,  
    owner_id UUID NOT NULL REFERENCES users(user_id) ON DELETE CASCADE  
);  

-- Booking System  
CREATE TABLE booking (  
    booking_id UUID PRIMARY KEY DEFAULT uuid_generate_v4(),  
    billboard_id UUID NOT NULL REFERENCES billboard(billboard_id) ON DELETE CASCADE,  
    user_id UUID NOT NULL REFERENCES users(user_id) ON DELETE CASCADE,  
    start_date DATE NOT NULL,  
    end_date DATE NOT NULL,  
    offered_price NUMERIC(10, 2) NOT NULL,  
    status VARCHAR(10) DEFAULT 'pending',  
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,  
    updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP  
);  

/*============== SYSTEM INITIALIZATION ==============*/  
-- Default Roles  
INSERT INTO roles (role_name) VALUES  
    ('User'),  
    ('Admin'),  
    ('Owner');  

/*============== AUTOMATION ==============*/  
-- Universal Update Trigger  
CREATE OR REPLACE FUNCTION update_timestamp()  
    RETURNS TRIGGER AS $$  
BEGIN  
    NEW.updated_at = CURRENT_TIMESTAMP;  
    RETURN NEW;  
END;  
$$ LANGUAGE plpgsql;  

-- Apply to All Tables  
CREATE TRIGGER users_update  
    BEFORE UPDATE ON users FOR EACH ROW EXECUTE FUNCTION update_timestamp();  

CREATE TRIGGER billboard_update  
    BEFORE UPDATE ON billboard FOR EACH ROW EXECUTE FUNCTION update_timestamp();  

CREATE TRIGGER booking_update  
    BEFORE UPDATE ON booking FOR EACH ROW EXECUTE FUNCTION update_timestamp();  

/*============== OPTIMIZATION ==============*/  
-- Essential Indexes  
CREATE INDEX users_location_idx ON users(locality);  
CREATE INDEX billboard_price_idx ON billboard(price);  
CREATE INDEX booking_dates_idx ON booking USING BRIN (start_date, end_date);
```