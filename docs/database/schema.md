# Database Schema

## Table Definitions

### users Table

Table for managing user information

| Column     | Type            | NULL | Key  | Default    | Extra         |
|------------|-----------------|------|------|------------|---------------|
| id         | bigint         | NO   | PRI  | NULL       | auto_increment|
| username   | varchar(30)    | YES  | UNI  | NULL       |               |
| email      | varchar(80)    | YES  | UNI  | NULL       |               |
| first_name | varchar(40)    | YES  |      | NULL       |               |
| last_name  | varchar(40)    | YES  |      | NULL       |               |
| created_at | datetime(6)    | NO   |      | NULL       |               |
| updated_at | datetime(6)    | NO   |      | NULL       |               |

#### Indexes
- PRIMARY KEY (id)
- UNIQUE INDEX (email)
- UNIQUE INDEX (username)

### tasks Table

Table for managing task information

| Column      | Type            | NULL | Key  | Default    | Extra         |
|-------------|-----------------|------|------|------------|---------------|
| id          | bigint         | NO   | PRI  | NULL       | auto_increment|
| title       | varchar(30)    | YES  |      | NULL       |               |
| description | varchar(255)   | YES  |      | NULL       |               |
| due_date    | date           | YES  |      | NULL       |               |
| status      | varchar(10)    | YES  |      | NULL       |               |
| owner_id    | bigint         | YES  | MUL  | NULL       |               |
| created_at  | datetime(6)    | NO   |      | NULL       |               |
| updated_at  | datetime(6)    | NO   |      | NULL       |               |

#### Indexes
- PRIMARY KEY (id)
- INDEX (owner_id)

#### Foreign Key Constraints
- FOREIGN KEY (owner_id) REFERENCES users(id)

## Database Support

### MySQL
- The schema definition above is based on MySQL's `describe` command output
- Character Set: utf8mb4
- Collation: utf8mb4_unicode_ci

### PostgreSQL
- The schema definition above is based on PostgreSQL's `\d` command output
- Character Set: UTF8
- Collation: Default

## Notes
- The same schema structure is maintained across both databases
- Timestamp types are slightly different but functionally equivalent
- Indexes and foreign key constraints maintain the same structure in both databases 