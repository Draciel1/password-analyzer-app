# password-analyzer-app
🔑 Password Security Analyzer (Single-File HTML/JS)
This project is a modern, dark-themed web application designed to help users determine the security of a password based on two critical factors: Entropy (Randomness) and Exposure (Data Breach Check).

The entire application—including HTML, Tailwind CSS, and JavaScript logic—is contained within a single index.html file, making it highly portable and easy to deploy or integrate.

✨ Key Features
Entropy Calculation: The analyzer measures the cryptographic strength (Randomness Score in Bits) based on the password's length and character complexity (uppercase, lowercase, numbers, symbols). Spaces are explicitly ignored for calculation, enforcing stricter security standards.

Secure Exposure Check (HIBP): The application integrates with the free Have I Been Pwned (HIBP) Pwned Passwords API. It uses the k-Anonymity protocol (sending only the first 5 characters of the SHA-1 hash) to securely check if the exact password has been compromised in a public data breach.

Real-time Downgrade: If a password is found to be exposed in a breach, its status is immediately downgraded to "Weakened" regardless of its high entropy score, and an urgent "ACTION REQUIRED" warning is prominently displayed.

Input Validation: The input field prevents the entry of space characters, reinforcing strong password creation practices.

Design: Utilizes Tailwind CSS for a sleek, mobile-friendly dark user interface with high contrast.

💻 Running the Application
Since the application is a single, self-contained HTML file, deployment and execution are simple:

Download: Clone the repository or simply save the contents of index.html locally.

Run Locally: The file can be opened directly in any modern web browser (Chrome, Firefox, Safari, etc.) by double-clicking it.

Analyze: Users type a password into the input field, and the application instantly provides a real-time analysis of the strength and vulnerability.

Deployment
The application is ideal for hosting on static website services:

GitHub Pages: Upload the index.html file to a public GitHub repository and enable GitHub Pages on the main branch root.

Netlify/Vercel: The file can be drag-and-dropped onto these services for instant deployment.

🛡️ Technical Details
Component

Technology

Role

Structure & UI

HTML5 / Tailwind CSS

Provides the document structure and the responsive, dark-themed styling.

Entropy Logic

Vanilla JavaScript

Calculates the complexity using the formula E=L×log 
2
​
 (S) and determines the strength rating.

Hashing

crypto.subtle.digest('SHA-1') (Browser API)

Generates the cryptographic hash of the password securely within the user's browser environment.

Exposure Check

fetch() to HIBP API

Sends the 5-character hash prefix to api.pwnedpasswords.com/range/ for breach verification.

Privacy

k-Anonymity Protocol

Crucial: The full password or its full hash is never transmitted over the network. Only the first 5 characters of the hash are used for the lookup range.
