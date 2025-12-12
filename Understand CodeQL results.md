In previous units, you created a database and scanned the extracted file from your code. Now you can view the results and determine if there are security vulnerabilities to address.

# View code-scanning results from CodeQL analysis

Interpreted query results are automatically displayed in the source code in the CodeQL extension for Visual Studio Code. Output results that the CodeQL CLI generates can be in many formats for use with various tools.

You can control how analysis results are displayed in source code by modifying a query's ``select`` statement. You can make the results clear and easy for other users to understand while developing the query. When you write your own queries in the query console or in the CodeQL extension for Visual Studio Code, there are no constraints on what can be selected. 

If you want to use a query to create alerts in Github code scanning or generate valid analysis results by using the CodeQL CLI, you need to make the ``select`` statement report results in the required format.
