### Database Setup 

#### Installation 

Installation of sqlite 
`sudo yum update`
`sudo yum install sqlite`

Verify installation:
`sqlite3 --version`
`sqlite3 .help`

![sqlite3 install](/screenshots/sqlite3_install.png)

#### Configuration 
` Create Authors Table: 
```sql
CREATE TABLE Author (
    user_id INTEGER PRIMARY KEY,
    username VARCHAR(255) UNIQUE NOT NULL,
    email VARCHAR(255) UNIQUE NOT NULL,
    password VARCHAR(255) NOT NULL,
    bio TEXT,
    profile_picture VARCHAR(255)
);
```

- Create BlogEntry Table: 
```sql
CREATE TABLE BlogEntry (
    post_id INT PRIMARY KEY,
    user_id INT,
    title TEXT,
    subtitle TEXT,
    blurb TEXT,
    content TEXT,
    time_created DATETIME,
    time_updated DATETIME,
    is_published BOOLEAN,
    FOREIGN KEY (user_id) REFERENCES Author(user_id)
);
```

### Blog Entries 

#### Entry Creation 

- Insert Authors:
```sql
INSERT INTO Author (user_id, username, email, password, bio, profile_picture)
VALUES (1, 'Arthur cheng', 'artcheng@uw.edum', 'temp_password', 'Bio', 'http://example.com/profile.jpg');
```

- Insert BlogEntry
```sql
INSERT INTO BlogEntry (post_id, user_id, title, subtitle, blurb, content, time_created, time_updated, is_published)
VALUES (1, 1, 'My First Blog Post', 'An Introduction', 'This is a brief summary of my first blog post.', 'This is the main content of my first blog post. It contains detailed information about the topic.', CURRENT_TIMESTAMP, CURRENT_TIMESTAMP, TRUE);
```

#### Data Integrity & Validation

- Table Structure:
![table structure](/screenshots/table_structure.png)


- Tables Contents
![table contents](/screenshots/table_contents.png)