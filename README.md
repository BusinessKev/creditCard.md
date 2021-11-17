Database Credit Card 
# creditCard.md
[![](https://mermaid.ink/img/eyJjb2RlIjoiZXJEaWFncmFtXG5cbiAgICBVc2VyIHx8IC0tIG97IENyZWRpdENhcmQgOiBoYXNcbiAgICBDcmVkaXRDYXJkIHx8IC0tIG97IFB1cmNoYXNlIDogd2FzX3VzZWRcbiAgICBQdXJjaGFzZSB8fCAtLSB8eyBJbnZlbnRvcnlJdGVtIDogaGFzXG4gICAgSW52ZW50b3J5SXRlbSB8fCAtLSB8fCBJdGVtVHlwZSA6IGhhc1xuXG5cbiAgICBVc2VyIHtcbiAgICAgICAgc3RyaW5nIHVzZXJOYW1lXG4gICAgICAgIHN0cmluZyBlbWFpbCBcbiAgICB9XG5cbiAgICBDcmVkaXRDYXJkIHtcbiAgICAgICAgc3RyaW5nIG51bWJlclxuICAgIH1cblxuICAgIFB1cmNoYXNlIHtcbiAgICAgICAgZGF0ZSBkYXRlXG4gICAgfVxuICAgICUlIGlQaG9uZSAxMiwgaVBob25lIDZzXG5cbiAgICBJdGVtVHlwZSB7XG4gICAgICAgIHN0cmluZyB0eXBlIFxuICAgIH1cblxuICAgIEludmVudG9yeUl0ZW0ge1xuICAgICAgICBzdHJpbmcgbmFtZVxuICAgIH0iLCJtZXJtYWlkIjp7fSwidXBkYXRlRWRpdG9yIjpmYWxzZX0)](https://mermaid-js.github.io/mermaid-live-editor/#/edit/eyJjb2RlIjoiZXJEaWFncmFtXG5cbiAgICBVc2VyIHx8IC0tIG97IENyZWRpdENhcmQgOiBoYXNcbiAgICBDcmVkaXRDYXJkIHx8IC0tIG97IFB1cmNoYXNlIDogd2FzX3VzZWRcbiAgICBQdXJjaGFzZSB8fCAtLSB8eyBJbnZlbnRvcnlJdGVtIDogaGFzXG4gICAgSW52ZW50b3J5SXRlbSB8fCAtLSB8fCBJdGVtVHlwZSA6IGhhc1xuXG5cbiAgICBVc2VyIHtcbiAgICAgICAgc3RyaW5nIHVzZXJOYW1lXG4gICAgICAgIHN0cmluZyBlbWFpbCBcbiAgICB9XG5cbiAgICBDcmVkaXRDYXJkIHtcbiAgICAgICAgc3RyaW5nIG51bWJlclxuICAgIH1cblxuICAgIFB1cmNoYXNlIHtcbiAgICAgICAgZGF0ZSBkYXRlXG4gICAgfVxuICAgICUlIGlQaG9uZSAxMiwgaVBob25lIDZzXG5cbiAgICBJdGVtVHlwZSB7XG4gICAgICAgIHN0cmluZyB0eXBlIFxuICAgIH1cblxuICAgIEludmVudG9yeUl0ZW0ge1xuICAgICAgICBzdHJpbmcgbmFtZVxuICAgIH0iLCJtZXJtYWlkIjp7fSwidXBkYXRlRWRpdG9yIjpmYWxzZX0)

# SQLite code
```SQL
create table users (
        user_id integer primary key,
        user_name text not null unique,
        email text not null unique
)
```
```SQL
INSERT INTO users 
        (user_name, email)
VALUES
        ('janed', 'jane@fastmail.de'),
        ('janes', 'jane@email.me'),
        ('james', 'james@hello.me'),
        ('hansd', 'hans@one.de'),
        ('iistv', 'istvan@two.us');
```
```SQL
CREATE table credit_cards (
        credit_card_id INTEGER PRIMARY KEY,
        credit_card_number TEXT NOT NULL UNIQUE 
                CHECK (length(credit_card_number) = 16),
        user_id INTEGER NOT NULL,
        FOREIGN KEY(user_id) REFERENCES users(user_id)
)
```
```SQL
INSERT INTO credit_cards 
   (credit_card_number, user_id)
VALUES
    ('0000111122223333', 1),
    ('1111222233334444', 2),
    ('2222333344445555', 3),
    ('3333444455556666', 4),
    ('4444555566667777', 5);
```
```SQL
CREATE table purchases (
        purchase_id INTEGER PRIMARY KEY,
        purchase_date DATE,
        credit_card_id INTEGER NOT NULL,
        FOREIGN KEY(credit_card_id) REFERENCES credit_cards(credit_card_id)
)
```
```SQL
INSERT INTO purchases 
   (purchase_date, credit_card_id)
VALUES
    ('2021-02-04', 1),
    ('2021-02-06', 2),
    ('2021-02-10', 3),
    ('2021-02-15', 4),
    ('2021-02-18', 5);
```
```SQL
CREATE table inventory_items (
        inventory_items_id INTEGER PRIMARY KEY,
        inventory_items_name TEXT NOT NULL,
        purchase_id INTEGER NOT NULL,
        FOREIGN KEY(purchase_id) REFERENCES purchases(purchase_id)
)
```
```SQL
INSERT INTO inventory_items
   (inventory_items_name, purchase_id)
VALUES
    ('iPhone6', 1),
    ('MacBookPro', 2),
    ('Spoon', 3),
    ('Flash Light', 4),
    ('Watch', 5);
```
```SQL
CREATE table numbers (
        number_id integer primary key,
        number integer not null unique,
        is_even integer not null
);
```
```SQL
INSERT INTO 
        numbers (number, is_even)
VALUES
        (0, 1),
        (1, 0),
        (2, 1),
        (3, 0),
        (4, 1),
        (5, 0),
        (6, 1),
        (7, 0),
        (8, 1),
        (9, 0);
```
# query
```SQL
SELECT user_name, email, credit_card_number 
FROM credit_cards
JOIN users USING (user_id);
```
```SQL
select user_name, email, credit_card_number, purchase_date, inventory_items_name from inventory_items
join purchases using (purchase_id)
join credit_cards using (credit_card_id)
join users using (user_id);
```
or another way
```SQL
create table answer_one as
select user_name, email, credit_card_number, purchase_date, inventory_item_name from credit_cards
join users using (user_id)
join purchases using(credit_card_id)
join inventory_items using (purchase_id);
```
