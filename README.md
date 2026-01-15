# 🛡️ Day 1: API Logic & Parameter Manipulation
**Goal:** Understanding how backends interpret data differently than security layers (WAFs).

## 🔬 Research: HTTP Parameter Pollution (HPP)
Maine ye research kiya ki jab hum duplicate parameters (jaise `?id=1&id=2`) bhejte hain, toh alag-alag backend technologies kaise behave karti hain. Isse hum "Technology Fingerprinting" kar sakte hain.

### 📊 Tech Fingerprinting Table
| Backend Tech | Behavior | Security Risk |
| :--- | :--- | :--- |
| **Node.js (Express)** | Returns Array `['1', '2']` | Logic crash or "Type Confusion" bypass. |
| **Python (Flask)** | Takes **First** value `1` | Bypasses filters checking the 2nd value. |
| **PHP / Apache** | Takes **Last** value `2` | Bypasses filters checking the 1st value. |
| **Java (Spring)** | Joins them `1,2` | Bypasses "Exact Match" WAF rules. |

## 🕵️‍♂️ Key Methodology: Information Leakage
* **Discovery:** Broken error messages (500 Internal Server Error) ka use karke database structure map karna.
* **Impact:** Identified **UUID** formats which prevents simple ID guessing (ID Enumeration).

## 🚀 Professional Takeaway
Security sirf "Hacking" nahi hai, balki "Parsing Mismatch" ko samajhna hai. Agar WAF aur Backend ki "Bhasha" (Language) match nahi karti, toh wahi se exploit banta hai.
