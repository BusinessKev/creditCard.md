# creditCard.md
[![](https://mermaid.ink/img/eyJjb2RlIjoiZXJEaWFncmFtXG4gICAgJSUgYSBwZXJzb24gY2FuIGhhdmUgMCBvciBtYW55IGNyZWRpdCBjYXJkc1xuICAgIFBlcnNvbiB8fCAtLSBveyBDcmVkaXRDYXJkOiBoYXNcbiAgICBDcmVkaXRDYXJkIHx8IC0tIG97IFB1cmNoYXNlOiBwdXJjaGFzZWRcbiAgICBQdXJjaGFzZSB8eyAtLSB8eyBJdGVtIDogaGFzICBcblxuICAgIFBlcnNvbntcbiAgICBzdHJpbmcgbmFtZVxuICAgIHN0cmluZyBlbWFpbFxuICAgIHN0cmluZyBwaG9uZU51bWJlclxuICAgIHN0cmluZyBiaXJ0aGRheVxufVxuICAgIENyZWRpdENhcmR7XG4gICAgc3RyaW5nIGNyZWRpdENhcmROdW1iZXJcbiAgICBzdHJpbmcgRXhwaWFyeURhdGVcbiAgICBpbnQgQ1ZDTnVtYmVyXG4gICAgc3RyaW5nIENhcmRIb2xkZXJOYW1lXG59XG4gICAgUHVyY2hhc2V7XG4gICAgYm9vbCBpc1B1cmNoYXNlZFxuICAgIGludCBxdWFudGl0eVxuICAgIHN0cmluZyBQdXJjaGFzZURhdGVcbiAgICBzdHJpbmcgc2hpcHBpbmdEYXRlXG59XG4gICAgSXRlbXtcbiAgICBzdHJpbmcgbmFtZSBcbiAgICBpbnQgcHJpY2UgXG4gICAgc3RyaW5nIGRlc2NyaWJ0aW9uXG59IiwibWVybWFpZCI6eyJ0aGVtZSI6ImRlZmF1bHQifSwidXBkYXRlRWRpdG9yIjpmYWxzZX0)](https://mermaid-js.github.io/mermaid-live-editor/#/edit/eyJjb2RlIjoiZXJEaWFncmFtXG4gICAgJSUgYSBwZXJzb24gY2FuIGhhdmUgMCBvciBtYW55IGNyZWRpdCBjYXJkc1xuICAgIFBlcnNvbiB8fCAtLSBveyBDcmVkaXRDYXJkOiBoYXNcbiAgICBDcmVkaXRDYXJkIHx8IC0tIG97IFB1cmNoYXNlOiBwdXJjaGFzZWRcbiAgICBQdXJjaGFzZSB8eyAtLSB8eyBJdGVtIDogaGFzICBcblxuICAgIFBlcnNvbntcbiAgICBzdHJpbmcgbmFtZVxuICAgIHN0cmluZyBlbWFpbFxuICAgIHN0cmluZyBwaG9uZU51bWJlclxuICAgIHN0cmluZyBiaXJ0aGRheVxufVxuICAgIENyZWRpdENhcmR7XG4gICAgc3RyaW5nIGNyZWRpdENhcmROdW1iZXJcbiAgICBzdHJpbmcgRXhwaWFyeURhdGVcbiAgICBpbnQgQ1ZDTnVtYmVyXG4gICAgc3RyaW5nIENhcmRIb2xkZXJOYW1lXG59XG4gICAgUHVyY2hhc2V7XG4gICAgYm9vbCBpc1B1cmNoYXNlZFxuICAgIGludCBxdWFudGl0eVxuICAgIHN0cmluZyBQdXJjaGFzZURhdGVcbiAgICBzdHJpbmcgc2hpcHBpbmdEYXRlXG59XG4gICAgSXRlbXtcbiAgICBzdHJpbmcgbmFtZSBcbiAgICBpbnQgcHJpY2UgXG4gICAgc3RyaW5nIGRlc2NyaWJ0aW9uXG59IiwibWVybWFpZCI6eyJ0aGVtZSI6ImRlZmF1bHQifSwidXBkYXRlRWRpdG9yIjpmYWxzZX0)
# SQLite code
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
```SQL
select user_name, email, credit_card_number, purchase_date, inventory_items_name from inventory_items
join purchases using (purchase_id)
join credit_cards using (credit_card_id)
join users using (user_id)
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
