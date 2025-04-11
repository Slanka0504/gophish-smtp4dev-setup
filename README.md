# gophish-smtp4dev-setup
🕵️ Gophish Phishing Lab using smtp4dev

📌 Project Overview

This project demonstrates a **local phishing simulation lab** using [Gophish](https://github.com/gophish/gophish) as the phishing framework and [smtp4dev](https://github.com/rnwood/smtp4dev) as a dummy SMTP server. It allows safe, offline testing of phishing emails, email templates, tracking metrics, and campaign management — perfect for cybersecurity learners and pentesters.

> 🔒 **Note**: This is strictly for educational and ethical purposes only. Do **not** use this setup against real users or organizations.

---

## 🛠 Tools Used

| Tool      | Description                                      |
|-----------|--------------------------------------------------|
| Gophish   | Open-source phishing simulation framework        |
| smtp4dev  | Fake SMTP server for email testing               |
| Gmail     | (Optional) Used to test tracking on real clients |
| HTML/CSS  | For email and landing page templates             |

---

⚙️ Setup Instructions

1. Clone Gophish

git clone https://github.com/gophish/gophish.git
cd gophish

2. Install smtp4dev

    Download from: smtp4dev Releases

    Run smtp4dev.exe or use Docker:

docker run --rm -it -p 3000:80 -p 25:25 rnwood/smtp4dev

3. Configure Gophish

    Edit config.json inside Gophish folder:

"smtp": {
  "host": "localhost:25",
  "from_address": "test@example.com"
},
"phish_server": {
  "listen_url": "0.0.0.0:80",
  "use_tls": false
},
"admin_server": {
  "listen_url": "127.0.0.1:3333",
  "use_tls": false
}

    Restart Gophish after changes.

4. Create Campaign in Gophish

    Create sending profile using localhost:25

    Use a template with a tracking link:

    <a href="{{.URL}}">Click here to verify</a>

    Assign a group with test emails

    Set URL to your local IP, e.g., http://192.168.1.5

5. Run Campaign

    Gophish sends emails via smtp4dev

    Open smtp4dev in browser: http://localhost:3000

    View emails, click links, track opens/clicks

   // you might not be able to view live tracking metric while using smtp4dev as it is a fake server and doesn't send eamils actual email. You can however see the emails you've sent on the messages section and click on the links. To be able to actually send emails to clients (ethically), you can explore other smtp servers like mailhog, gmail etc.
