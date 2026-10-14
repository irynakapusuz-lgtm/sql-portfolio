- **How can one restrict access to certain columns of a database table?**

In Postgre we can not restrict access to certain columns directly but we can create a view that shows only the allowed columns, and then give users access to the view instead of the real table. We can create a view showing only allowed columns with CREATE VIEW command, remove access to the real table with REVOKE ALL, give users access to the view instead with GRANT command.

- **What is the difference between user identification and user authentication?**

Identification is the process where a user declares themselves (by entering username, email, swiping ID card etc.) It answers question ‘Who are you?’

Authentication is the process where the system verifies that the user is truly who they claim to be. During identification phase user sends an identifier like ID or email. And during authentication phase the system demands credentials linked to that identifier (like password). It answers question ‘How can you prove that?’ If credentials are matched the system shows identity is s authenticated.

- **What are the recommended authentication protocols for PostgreSQL?**

PostgreSQL supports a variety of authentication methods, including password authentication, certificate-based authentication, and external authentication via LDAP or Kerberos. By default, PostgreSQL requires users to authenticate using a password. Also PostgreSQL provides a robust authorization system that allows database administrators to control access to various database objects, including tables, views, and functions. Types :

SCRAM-SHA-256 (Modern Password Authentication) — strong password authentication highly recommended for most production systems according to documentation.

SSL/TLS Certificate Authentication (Client Certificates) — client-side certificates instead of passwords; for enterprise systems, internal networks, and sensitive data.

Kerberos / GSSAPI — Kerberos tickets instead of passwords; recommended for Enterprise Environments.

LDAP Authentication – recommended when managing many users at scale.

- **What is proxy authentication in PostgreSQL and what is it for? Why does it make the previously discussed role-based access control easier to implement?**

Proxy authentication in PostgreSQL allows a user or application to connect using one account but operate as another role. It separates authentication from authorization. This makes role-based access control easier to implement because Users don’t need their own database accounts, permissions are managed entirely through roles, there is no need to share or manage many passwords, Easy to audit and control. All this gives clearer logging and simpler permission tracking.
