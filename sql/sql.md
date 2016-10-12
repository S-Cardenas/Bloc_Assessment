##**Question**
Hey mentor,

Thanks for the lecture yesterday, it really helped me get motivated again. I've been working through this assignment about databases and I'm confused about "SQL injection." What does that mean and how does it work? How do I prevent it in my apps?

Thanks!

-Student

##**Response**

As you've seen as you work through your database assignments, SQL can be used to retrieve and MODIFY database
data. SQL is usually used to display information from a web page. Normally, the user inputs search values by typing text into the web page and the web page sends a request to it's database to make a query. Because SQL
statements are text only, it becomes very easy to dynamically change SQL statements with a bit of computer code and provide the user with the specified information.

In the following example, a user typed in their SocialSecurityNumber into a website and this was sent to the backend to make a database query:

```
txtSSN = getRequestString("SocialSecurityNumber");
txtSQL = "SELECT * FROM Users WHERE SocialSecurityNumber = " + txtSSN;
```

A SQL injection is a method where a malicious string of text can be submitted and therefore inject SQL commands
into an SQL statement. Injected SQL commands could potentially permanently modify a database and ultimately compromise the security of a web app. This is not good!!

Imagine now that instead of the user typing in an actual SSN they submitted the text:
`"45278965'); DROP TABLE Users;--"`

This would result in the following commands being run in SQL and your entire user database being effectively
deleted:

```
txtSSN = getRequestString("45278965'); DROP TABLE Users;--");
txtSQL = "SELECT * FROM Users WHERE SocialSecurityNumber = " + txtSSN;
database.sql(textSQL) ## SELECT * FROM Users WHERE SocialSecurityNumber = 45278965'); DROP TABLE Users;--
```

It can be very simple to send malicious SQL commands into a website's database. Fortunately, most of the toolkits that we use nowadays, such as Django and Ruby on Rails, have built in methods to guard against this
malicious activity.

If you need any further clarification or if you would like me to elobarte on how Rails and Django safeguard against this don't hesitate to ask.

Best regards,

Stefan
