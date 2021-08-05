# A look through the crossed eyeballs

"Good thing about crossed eyeballs is you get a wide angle, even if it's blurring, it's enough to bring hidden evidence to vision"

~ Nikolay Kadnikov

## HTTP web server

Usually on Port 80, but be sure to check uncommon port too. Web server can be running on other hidden ports

* Check the version of the server
   * If nginx, apache, IIS etc
   * Check vulns online for this version
   * Find exploit / metasploit

<br>

* Read the source code
* Check for creds/hints in comments
* Check robots.txt
* Check for common dirs like /admin /login
* Use URL fuzzers for dirs and .php pages

<br>

* If site allows some kind of user registration and login
    * Check if vulnerable to sql injection
    * Use burpsuite
    * Check POST request params while making account
    * Check how cookies/ PHP session ID are recieved
    * Try to decode manipulate cookies after login
    * See how it works, eg. JWT token

<br>

* If got the admin panel
    * Check source code for hints
    * Can use CEWL for wordlist
    * Use burpsuite intruder
    * Bruteforce
    * SQL injection

<br>

* If admin panel is accessible
    * Search for user creds
    * See if there is some upload vuln
        * Upload PHP webshell
        * Call it from curl
        * Get reverse shell connection on local machine

<br>

* Check for uncommon js
    * Check version
    * Deobsfucate them
    * Understand source code
    * Make exploit

<br>

* If some search box
    * Try SQL injection
    * Dump DBs
    * Get user and pass hash








