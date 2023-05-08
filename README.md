Download Link: https://assignmentchef.com/product/solved-step-1-business-layer-functionality
<br>
STEP 1: Business Layer Functionality

1. Open Microsoft Visual Studio.NET.

2. Click the ASP.NET website named PayrollSystem to open it.

3. Create a new class called <strong>clsBusinessLayer</strong>.

4. Add the following code in the <strong>clsBusinessLayer</strong> class:

<strong>// **** Add the following at the top of the class file,</strong>

<strong>// Add your comments here</strong>

<strong>using</strong> <strong>System</strong><strong>.</strong><strong>Net</strong><strong>.</strong><strong>Mail</strong><strong>;</strong>

<strong>//**** Add the following code inside the body of public class clsBusinessLayer ****</strong>

<strong>public</strong> <strong>static</strong> <strong>bool</strong> <strong>SendEmail</strong><strong>(</strong><strong>string</strong> <strong>Sender</strong><strong>,</strong> <strong>string</strong> <strong>Recipient</strong><strong>,</strong> <strong>string</strong><strong> bcc</strong><strong>,</strong> <strong>string</strong><strong> cc</strong><strong>,</strong>

<strong>string</strong> <strong>Subject</strong><strong>,</strong> <strong>string</strong> <strong>Body</strong><strong>)</strong>

<strong>{</strong>

<strong>try</strong> <strong>{</strong>

<strong>// Add your comments here</strong>

<strong>MailMessage</strong> <strong>MyMailMessage</strong> <strong>=</strong> <strong>new</strong> <strong>MailMessage</strong><strong>();</strong>

<strong>// Add your comments here</strong>

<strong>MyMailMessage</strong><strong>.</strong><strong>From</strong> <strong>=</strong> <strong>new</strong> <strong>MailAddress</strong><strong>(</strong><strong>Sender</strong><strong>);</strong>

<strong>// Add your comments here</strong>

<strong>MyMailMessage</strong><strong>.</strong><strong>To</strong><strong>.</strong><strong>Add</strong><strong>(</strong><strong>new</strong> <strong>MailAddress</strong><strong>(</strong><strong>Recipient</strong><strong>));</strong>

<strong>// Add your comments here</strong>

<strong>if</strong> <strong>(</strong><strong>bcc </strong><strong>!=</strong> <strong>null</strong> <strong>&amp;&amp;</strong><strong> bcc </strong><strong>!=</strong> <strong>string</strong><strong>.</strong><strong>Empty</strong><strong>)</strong> <strong>{</strong>

<strong>// Add your comments here</strong>

<strong>MyMailMessage</strong><strong>.</strong><strong>Bcc</strong><strong>.</strong><strong>Add</strong><strong>(</strong><strong>new</strong> <strong>MailAddress</strong><strong>(</strong><strong>bcc</strong><strong>));</strong>

<strong>}</strong>

<strong>// Add your comments here</strong>

<strong>if</strong> <strong>(</strong><strong>cc </strong><strong>!=</strong> <strong>null</strong> <strong>&amp;&amp;</strong><strong> cc </strong><strong>!=</strong> <strong>string</strong><strong>.</strong><strong>Empty</strong><strong>)</strong> <strong>{</strong>

<strong>// Add your comments here</strong>

<strong>MyMailMessage</strong><strong>.</strong><strong>CC</strong><strong>.</strong><strong>Add</strong><strong>(</strong><strong>new</strong> <strong>MailAddress</strong><strong>(</strong><strong>cc</strong><strong>));</strong>

<strong>}</strong>

<strong>// Add your comments here</strong>

<strong>MyMailMessage</strong><strong>.</strong><strong>Subject</strong> <strong>=</strong> <strong>Subject</strong><strong>;</strong>

<strong>// Add your comments here</strong>

<strong>MyMailMessage</strong><strong>.</strong><strong>Body</strong> <strong>=</strong> <strong>Body</strong><strong>;</strong>

<strong>// Add your comments here</strong>

<strong>MyMailMessage</strong><strong>.</strong><strong>IsBodyHtml</strong> <strong>=</strong> <strong>true</strong><strong>;</strong>

<strong>// Add your comments here</strong>

<strong>MyMailMessage</strong><strong>.</strong><strong>Priority</strong> <strong>=</strong> <strong>MailPriority</strong><strong>.</strong><strong>Normal</strong><strong>;</strong>

<strong>// Add your comments here</strong>

<strong>SmtpClient</strong> <strong>MySmtpClient</strong> <strong>=</strong> <strong>new</strong> <strong>SmtpClient</strong><strong>(</strong><strong>“localhost”</strong><strong>);</strong>

<strong>//SMTP Port = 25;</strong>

<strong>//Generic IP host = “127.0.0.1”;</strong>

<strong>// Add your comments here</strong>

<strong>MySmtpClient</strong><strong>.</strong><strong>Send</strong><strong>(</strong><strong>MyMailMessage</strong><strong>);</strong>

<strong>// Add your comments here</strong>

<strong>return</strong> <strong>true</strong><strong>;</strong>

<strong>}</strong> <strong>catch</strong> <strong>(</strong><strong>Exception</strong><strong> ex</strong><strong>)</strong> <strong>{</strong>

<strong>// Add your comments here</strong>

<strong>return</strong> <strong>false</strong><strong>;</strong>

<strong>}</strong>

<strong>}</strong><strong>     </strong>

Listen

STEP 2: Integration

5. Open the <strong>frmLogin</strong> Web form code behind the file and add the following code to the body of the<strong> if (dsUserLogin.tblUserLogin.Count &lt; 1)</strong> statement, just above the return statement:

<strong>// Add your comments here</strong>

<strong>// Add your comments here</strong>

<strong>if</strong> <strong>(</strong><strong>clsBusinessLayer</strong><strong>.</strong><strong>SendEmail</strong><strong>(</strong><strong>,</strong>

<strong>, “”, “”, “Login Incorrect”,</strong>

<strong>“The login failed for UserName: “</strong> <strong>+</strong> <strong>Login1</strong><strong>.</strong><strong>UserName</strong> <strong>+</strong>

<strong>” Password: “</strong> <strong>+</strong> <strong>Login1</strong><strong>.</strong><strong>Password</strong><strong>))</strong>

<strong>{</strong>

<strong>Login1</strong><strong>.</strong><strong>FailureText</strong> <strong>=</strong> <strong>Login1</strong><strong>.</strong><strong>FailureText</strong> <strong>+</strong>

<strong>” Your incorrect login information was sent to <a href="/cdn-cgi/l/email-protection" class="__cf_email__" data-cfemail="71035f5f03310314121418071403151e1c10181f5f121e1c">[email protected]</a>”</strong><strong>;</strong>

<strong>}</strong>

NOTE: Change the  and  to your e-mail and someone else’s e-mail for testing.

6. <strong>Optional:</strong> Perform this step only if you are doing this lab using Visual Studio installed on your own computer and you have administrative rights on your computer. If you are doing this lab using the iLab (Citrix) server, or if you do not have access to IIS, skip to Step 8.

7. In previous versions of Windows, the <strong>SMTP</strong> server was built into <strong>IIS.</strong> Now we will need to get a separate one. On the Microsoft Codeplex site is an SMTP server called <strong>smtp4dev</strong>, specifically designed for development environments. Pages 652–653 in the text discuss how to download and use smtp4dev. The site is<strong> http://smtp4dev.codeplex.com</strong>. Click on Downloads. Another example is <strong>Papercut</strong>, downloadable at:<strong> http://papercut.codeplex.com/</strong> You can use either smtp server.

Test the e-mail by logging in as someone other than Mickey or Minnie. You should receive an email to the SMTP client.

8. We have a security hole in our Web application. If you start the Web application by going to the login page, you can bypass the login page by simply typing the name of a form in the URL (try it). There is some limited protection because of the check that we are doing for the user role, but it still allows a user to get to pages that we don’t want them to get to unless the role is set properly. Add a security check in the <strong>Page_Load</strong> of each sensitive page (Manage Users, Add New Employee, View User Activity, Edit Employees), check for the Session role item with a value of<strong> A,</strong> and, if the user is accessing these pages without the proper permissions, <strong>redirect</strong> back to the <strong>frmLogin.aspx</strong> page. For example:

<strong>if</strong> <strong>(</strong><strong>Session</strong><strong>[</strong><strong>“SecurityLevel”</strong><strong>]</strong> <strong>!=</strong> <strong>“A”</strong><strong>)</strong>

<strong>{</strong>

<strong>Response</strong><strong>.</strong><strong>Redirect</strong><strong>(</strong><strong>“frmLogin.aspx”</strong><strong>);</strong>

<strong>}</strong>

9. This still leaves the possibility of a person bypassing the login page. We will fix that by using<strong> forms authentication</strong>. Add the following to the <strong>web.config</strong> file before the &lt;/system.web&gt; tag.

<strong>&lt;authentication</strong> <strong>mode</strong><strong>=</strong><strong>“Forms”</strong><strong>&gt;</strong>

<strong>&lt;forms</strong> <strong>loginUrl</strong><strong>=</strong><strong>“frmLogin.aspx”</strong> <strong>/&gt;</strong>

<strong>&lt;/authentication&gt;</strong>

<strong>&lt;authorization</strong> <strong>&gt;</strong>

<strong>&lt;deny</strong> <strong>users</strong><strong>=</strong><strong>“?”</strong> <strong>/&gt;</strong>

<strong>&lt;/authorization&gt;</strong>

10. This will redirect users to the login page if they have not yet gone through it for login. This process will use a <strong>cookie</strong> – when the user successfully logs in, a cookie is set that allows the user to go to other pages. If that cookie is not set, then the user is redirected to the login page if they try to go to any other page. Add the cookie code by adding this code in the frmLogin.aspx C# code after each place that you have <strong>e.Authenticated = true</strong>:

<strong>FormsAuthentication</strong><strong>.</strong><strong>RedirectFromLoginPage</strong><strong>(</strong><strong>Login1</strong><strong>.</strong><strong>UserName</strong><strong>,</strong> <strong>false</strong><strong>);</strong>

If you receive an error when you enter this in the code, right click on the line and choose <strong>Resolve-&gt;Using System.Web.Security</strong>

11. <strong>Hints:</strong>

Make sure you reestablish your database connection if you copied the files from a previous lab. Also, make sure to update the web.config file with the database connection string.

Update any DataSource controls that you added with the new payroll database location.

When you manually try to go to a second page by skipping the login page, a cookie is set specifying the name of the page you were attempting to visit. Once you log in successfully, ASP.Net will automatically attempt to navigate back to that page. You can reset the cookie so that the next page is frmMain, as expected, by typing that page in the URL for the browser before logging in.

<strong>Submit Final Lab (includes all previous lab assignments).</strong>

<strong>STEP 3: Test And Submit</strong>

12. Run your project. When you try to log in, enter a username that is not Mickey or Minnie (i.e., a username that is not found in tblUserLogin). An e-mail should be sent to the  e-mail address.

13. Test that frmMain reconfigures properly based on user role. Make sure that the user cannot bypass the login page.

Once you have verified that everything works, save your website, zip up all files, and submit them in the Dropbox.

NOTE: E-mails may be blocked due to firewalls, antivirus software, or even Internet service providers that turned SMTP off because of some known security issues. If the code works (does not produce an error when submitting), you will get full credit for this project even if no e-mail message is actuallySTEP 1: Business Layer Functionality

1. Open Microsoft Visual Studio.NET.

2. Click the ASP.NET website named PayrollSystem to open it.

3. Create a new class called <strong>clsBusinessLayer</strong>.

4. Add the following code in the <strong>clsBusinessLayer</strong> class:

<strong>// **** Add the following at the top of the class file,</strong>

<strong>// Add your comments here</strong>

<strong>using</strong> <strong>System</strong><strong>.</strong><strong>Net</strong><strong>.</strong><strong>Mail</strong><strong>;</strong>

<strong>//**** Add the following code inside the body of public class clsBusinessLayer ****</strong>

<strong>public</strong> <strong>static</strong> <strong>bool</strong> <strong>SendEmail</strong><strong>(</strong><strong>string</strong> <strong>Sender</strong><strong>,</strong> <strong>string</strong> <strong>Recipient</strong><strong>,</strong> <strong>string</strong><strong> bcc</strong><strong>,</strong> <strong>string</strong><strong> cc</strong><strong>,</strong>

<strong>string</strong> <strong>Subject</strong><strong>,</strong> <strong>string</strong> <strong>Body</strong><strong>)</strong>

<strong>{</strong>

<strong>try</strong> <strong>{</strong>

<strong>// Add your comments here</strong>

<strong>MailMessage</strong> <strong>MyMailMessage</strong> <strong>=</strong> <strong>new</strong> <strong>MailMessage</strong><strong>();</strong>

<strong>// Add your comments here</strong>

<strong>MyMailMessage</strong><strong>.</strong><strong>From</strong> <strong>=</strong> <strong>new</strong> <strong>MailAddress</strong><strong>(</strong><strong>Sender</strong><strong>);</strong>

<strong>// Add your comments here</strong>

<strong>MyMailMessage</strong><strong>.</strong><strong>To</strong><strong>.</strong><strong>Add</strong><strong>(</strong><strong>new</strong> <strong>MailAddress</strong><strong>(</strong><strong>Recipient</strong><strong>));</strong>

<strong>// Add your comments here</strong>

<strong>if</strong> <strong>(</strong><strong>bcc </strong><strong>!=</strong> <strong>null</strong> <strong>&amp;&amp;</strong><strong> bcc </strong><strong>!=</strong> <strong>string</strong><strong>.</strong><strong>Empty</strong><strong>)</strong> <strong>{</strong>

<strong>// Add your comments here</strong>

<strong>MyMailMessage</strong><strong>.</strong><strong>Bcc</strong><strong>.</strong><strong>Add</strong><strong>(</strong><strong>new</strong> <strong>MailAddress</strong><strong>(</strong><strong>bcc</strong><strong>));</strong>

<strong>}</strong>

<strong>// Add your comments here</strong>

<strong>if</strong> <strong>(</strong><strong>cc </strong><strong>!=</strong> <strong>null</strong> <strong>&amp;&amp;</strong><strong> cc </strong><strong>!=</strong> <strong>string</strong><strong>.</strong><strong>Empty</strong><strong>)</strong> <strong>{</strong>

<strong>// Add your comments here</strong>

<strong>MyMailMessage</strong><strong>.</strong><strong>CC</strong><strong>.</strong><strong>Add</strong><strong>(</strong><strong>new</strong> <strong>MailAddress</strong><strong>(</strong><strong>cc</strong><strong>));</strong>

<strong>}</strong>

<strong>// Add your comments here</strong>

<strong>MyMailMessage</strong><strong>.</strong><strong>Subject</strong> <strong>=</strong> <strong>Subject</strong><strong>;</strong>

<strong>// Add your comments here</strong>

<strong>MyMailMessage</strong><strong>.</strong><strong>Body</strong> <strong>=</strong> <strong>Body</strong><strong>;</strong>

<strong>// Add your comments here</strong>

<strong>MyMailMessage</strong><strong>.</strong><strong>IsBodyHtml</strong> <strong>=</strong> <strong>true</strong><strong>;</strong>

<strong>// Add your comments here</strong>

<strong>MyMailMessage</strong><strong>.</strong><strong>Priority</strong> <strong>=</strong> <strong>MailPriority</strong><strong>.</strong><strong>Normal</strong><strong>;</strong>

<strong>// Add your comments here</strong>

<strong>SmtpClient</strong> <strong>MySmtpClient</strong> <strong>=</strong> <strong>new</strong> <strong>SmtpClient</strong><strong>(</strong><strong>“localhost”</strong><strong>);</strong>

<strong>//SMTP Port = 25;</strong>

<strong>//Generic IP host = “127.0.0.1”;</strong>

<strong>// Add your comments here</strong>

<strong>MySmtpClient</strong><strong>.</strong><strong>Send</strong><strong>(</strong><strong>MyMailMessage</strong><strong>);</strong>

<strong>// Add your comments here</strong>

<strong>return</strong> <strong>true</strong><strong>;</strong>

<strong>}</strong> <strong>catch</strong> <strong>(</strong><strong>Exception</strong><strong> ex</strong><strong>)</strong> <strong>{</strong>

<strong>// Add your comments here</strong>

<strong>return</strong> <strong>false</strong><strong>;</strong>

<strong>}</strong>

<strong>}</strong><strong>     </strong>

Listen

STEP 2: Integration

5. Open the <strong>frmLogin</strong> Web form code behind the file and add the following code to the body of the<strong> if (dsUserLogin.tblUserLogin.Count &lt; 1)</strong> statement, just above the return statement:

<strong>// Add your comments here</strong>

<strong>// Add your comments here</strong>

<strong>if</strong> <strong>(</strong><strong>clsBusinessLayer</strong><strong>.</strong><strong>SendEmail</strong><strong>(</strong><strong>,</strong>

<strong>, “”, “”, “Login Incorrect”,</strong>

<strong>“The login failed for UserName: “</strong> <strong>+</strong> <strong>Login1</strong><strong>.</strong><strong>UserName</strong> <strong>+</strong>

<strong>” Password: “</strong> <strong>+</strong> <strong>Login1</strong><strong>.</strong><strong>Password</strong><strong>))</strong>

<strong>{</strong>

<strong>Login1</strong><strong>.</strong><strong>FailureText</strong> <strong>=</strong> <strong>Login1</strong><strong>.</strong><strong>FailureText</strong> <strong>+</strong>

<strong>” Your incorrect login information was sent to <a href="/cdn-cgi/l/email-protection" class="__cf_email__" data-cfemail="cfbde1e1bd8fbdaaacaaa6b9aabdaba0a2aea6a1e1aca0a2">[email protected]</a>”</strong><strong>;</strong>

<strong>}</strong>

NOTE: Change the  and  to your e-mail and someone else’s e-mail for testing.

6. <strong>Optional:</strong> Perform this step only if you are doing this lab using Visual Studio installed on your own computer and you have administrative rights on your computer. If you are doing this lab using the iLab (Citrix) server, or if you do not have access to IIS, skip to Step 8.

7. In previous versions of Windows, the <strong>SMTP</strong> server was built into <strong>IIS.</strong> Now we will need to get a separate one. On the Microsoft Codeplex site is an SMTP server called <strong>smtp4dev</strong>, specifically designed for development environments. Pages 652–653 in the text discuss how to download and use smtp4dev. The site is<strong> http://smtp4dev.codeplex.com</strong>. Click on Downloads. Another example is <strong>Papercut</strong>, downloadable at:<strong> http://papercut.codeplex.com/</strong> You can use either smtp server.

Test the e-mail by logging in as someone other than Mickey or Minnie. You should receive an email to the SMTP client.

8. We have a security hole in our Web application. If you start the Web application by going to the login page, you can bypass the login page by simply typing the name of a form in the URL (try it). There is some limited protection because of the check that we are doing for the user role, but it still allows a user to get to pages that we don’t want them to get to unless the role is set properly. Add a security check in the <strong>Page_Load</strong> of each sensitive page (Manage Users, Add New Employee, View User Activity, Edit Employees), check for the Session role item with a value of<strong> A,</strong> and, if the user is accessing these pages without the proper permissions, <strong>redirect</strong> back to the <strong>frmLogin.aspx</strong> page. For example:

<strong>if</strong> <strong>(</strong><strong>Session</strong><strong>[</strong><strong>“SecurityLevel”</strong><strong>]</strong> <strong>!=</strong> <strong>“A”</strong><strong>)</strong>

<strong>{</strong>

<strong>Response</strong><strong>.</strong><strong>Redirect</strong><strong>(</strong><strong>“frmLogin.aspx”</strong><strong>);</strong>

<strong>}</strong>

9. This still leaves the possibility of a person bypassing the login page. We will fix that by using<strong> forms authentication</strong>. Add the following to the <strong>web.config</strong> file before the &lt;/system.web&gt; tag.

<strong>&lt;authentication</strong> <strong>mode</strong><strong>=</strong><strong>“Forms”</strong><strong>&gt;</strong>

<strong>&lt;forms</strong> <strong>loginUrl</strong><strong>=</strong><strong>“frmLogin.aspx”</strong> <strong>/&gt;</strong>

<strong>&lt;/authentication&gt;</strong>

<strong>&lt;authorization</strong> <strong>&gt;</strong>

<strong>&lt;deny</strong> <strong>users</strong><strong>=</strong><strong>“?”</strong> <strong>/&gt;</strong>

<strong>&lt;/authorization&gt;</strong>

10. This will redirect users to the login page if they have not yet gone through it for login. This process will use a <strong>cookie</strong> – when the user successfully logs in, a cookie is set that allows the user to go to other pages. If that cookie is not set, then the user is redirected to the login page if they try to go to any other page. Add the cookie code by adding this code in the frmLogin.aspx C# code after each place that you have <strong>e.Authenticated = true</strong>:

<strong>FormsAuthentication</strong><strong>.</strong><strong>RedirectFromLoginPage</strong><strong>(</strong><strong>Login1</strong><strong>.</strong><strong>UserName</strong><strong>,</strong> <strong>false</strong><strong>);</strong>

If you receive an error when you enter this in the code, right click on the line and choose <strong>Resolve-&gt;Using System.Web.Security</strong>

11. <strong>Hints:</strong>

Make sure you reestablish your database connection if you copied the files from a previous lab. Also, make sure to update the web.config file with the database connection string.

Update any DataSource controls that you added with the new payroll database location.

When you manually try to go to a second page by skipping the login page, a cookie is set specifying the name of the page you were attempting to visit. Once you log in successfully, ASP.Net will automatically attempt to navigate back to that page. You can reset the cookie so that the next page is frmMain, as expected, by typing that page in the URL for the browser before logging in.

<strong>Submit Final Lab (includes all previous lab assignments).</strong>

<strong>STEP 3: Test And Submit</strong>

12. Run your project. When you try to log in, enter a username that is not Mickey or Minnie (i.e., a username that is not found in tblUserLogin). An e-mail should be sent to the  e-mail address.

13. Test that frmMain reconfigures properly based on user role. Make sure that the user cannot bypass the login page.

Once you have verified that everything works, save your website, zip up all files, and submit them in the Dropbox.

NOTE: E-mails may be blocked due to firewalls, antivirus software, or even Internet service providers that turned SMTP off because of some known security issues. If the code works (does not produce an error when submitting), you will get full credit for this project even if no e-mail message is actually transmitted. Consult with your instructor before submitting if an error occurs or if no e-mail is generated. It is expected that no e-mail will be sent if you are using the DeVry iLab (Citrix) server for this lab or if you were not able to download and install smtp4dev.

NOTE: Make sure that you include comments in the code provided where specified (where the ” // Add your comments here” is mentioned), including code you wrote, or else a 5-point deduction per item (form, class, function) will be made.

transmitted. Consult with your instructor before submitting if an error occurs or if no e-mail is generated. It is expected that no e-mail will be sent if you are using the DeVry iLab (Citrix) server for this lab or if you were not able to download and install smtp4dev.

NOTE: Make sure that you include comments in the code provided where specified (where the ” // Add your comments here” is mentioned), including code you wrote, or else a 5-point deduction per item (form, class, function) will be made.