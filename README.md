Advanced GeoIP Recon is a Python-based security scanning tool that provides deep reconnaissance capabilities against a target domain. It integrates multiple security assessment techniques into one automated workflow, making it ideal for security researchers, penetration testers, and system administrators.

The tool performs:

🌍 Geolocation tracking using multiple IP intelligence APIs

🔍 Subdomain enumeration through certificate transparency and DNS queries

📁 Comprehensive directory and file discovery (150+ paths)

🔒 SSL/TLS certificate analysis

📸 Automated webpage screenshots

🗺️ Interactive threat mapping with Folium

📊 Detailed reporting with structured output

✨ Features
Core Capabilities
Feature	Description
Geolocation Intelligence	IP address tracking, city/country location, ISP identification, timezone detection
Subdomain Discovery	Multi-source enumeration (crt.sh, HackerTarget, common subdomains)
Exposed Directory Scanning	150+ predefined sensitive paths (admin, backup, config, logs, APIs)
SSL/TLS Analysis	Certificate validation, issuer information, expiration checking
Automated Screenshots	Headless browser capture using Selenium WebDriver
Interactive Threat Map	Visual representation with subdomain markers and connection lines
Comprehensive Reporting	Detailed text reports with all findings
Multi-API Redundancy	Failover between multiple GeoIP services
Security Assessment Categories
text
📁 Administrative Panels     - /admin, /dashboard, /cpanel
💾 Backup Files             - /backup.zip, /backup.sql
⚙️ Configuration Files      - /config.php, /.env, /web.config
🗄️ Database Access          - /db, /mysql, /postgresql
👨‍💻 Development Artifacts    - /.git, /composer.json
📊 Log Files                - /error.log, /access.log
🔌 API Endpoints            - /api, /graphql, /swagger
📤 File Upload Directories  - /uploads, /media
🔐 Security Paths           - /auth, /login, /oauth
📦 Prerequisites
System Requirements
Python 3.8+

Windows/Linux/MacOS

Chrome Browser (for screenshot functionality)

ChromeDriver (matching Chrome version)

Required Python Packages
bash
requests>=2.26.0
folium>=0.12.1
selenium>=4.0.0
beautifulsoup4>=4.10.0
🚀 Installation
Step 1: Clone Repository
bash
git clone https://github.com/yourusername/advanced-geoip-recon.git
cd advanced-geoip-recon
Step 2: Install Dependencies
bash
pip install -r requirements.txt
Step 3: Setup ChromeDriver
Windows: Download ChromeDriver and place in C:\Windows\System32\

Linux: sudo apt-get install chromium-chromedriver

MacOS: brew install chromedriver

Step 4: Configure Output Directory
Modify the base path in the script:

python
self.base_path = "C:\\Users\\YourName\\Desktop\\ScanResults"
💻 Usage
Basic Command
bash
python AdvancedGeoIPRecon.py
Interactive Input
bash
🌐 GeoIP + URL Recon Module - الإصدار المتقدم
============================================================
🎯 أدخل الـ URL (مثال: example.com): example.com
Programmatic Usage
python
from AdvancedGeoIPRecon import AdvancedGeoIPRecon

scanner = AdvancedGeoIPRecon()
scanner.run_full_scan("https://target-domain.com")
📁 Output Structure
All results are saved in the specified directory:

text
ScanResults/
├── screenshot_[timestamp].png          # Webpage screenshot
├── threat_map_[timestamp].html         # Interactive threat map
├── scan_report_[timestamp].txt         # Detailed scan report
└── [all discovered files tracked]
🧩 Core Modules
1. Geolocation Intelligence (get_geoip_info)
Multi-API Strategy: Attempts multiple geo-services (ipapi.co, ip-api.com, geolocation-db.com)

Information Extracted:

IP Address & Location

City, Region, Country

Coordinates (Latitude/Longitude)

ISP & Timezone

2. Subdomain Enumeration (subdomain_enumeration)
python
Sources Used:
- crt.sh Certificate Transparency Logs
- HackerTarget DNS API
- Common Subdomain Dictionary (20+ entries)
- DNS Resolution Validation
3. Directory Scanning (check_exposed_directories)
python
Categories Included:
- Administrative: /admin, /dashboard, /wp-admin
- Backups: /backup.zip, /backup.sql, /dump.sql
- Configurations: /.env, /config.php, /settings.json
- Development: /.git, /.svn, /composer.json
- Logs: /error.log, /access.log
- APIs: /api, /graphql, /swagger
- 150+ total paths scanned
4. SSL/TLS Analysis (check_ssl_tls)
Certificate Validation

Issuer Verification

Expiry Detection

Protocol Identification

Subject Alternative Names (SAN)

5. Screenshot Capture (take_screenshot)
Headless Chrome Browser

Full page capture (1920x1080)

Automatic error handling

6. Threat Map Creation (create_threat_map)
python
Visual Elements:
- Main target marker (Red Flag)
- Subdomain markers (Blue Globals)
- Connection lines between assets
- Threat radius circle (5km)
- Interactive tooltips with details
📊 Results & Reporting
Console Output
bash
📍 الموقع الجغرافي: New York, United States
📡 IP: 192.168.1.1
🧭 الإحداثيات: 40.7128, -74.0060
✅ تم العثور على 15 نطاق فرعي
📁 تم فحص 150 مسار، وُجد 5 مسار مكشوف
🔒 الشهادة صادرة من: Let's Encrypt
✅ تم حفظ الصورة في: screenshot_20240215_143022.png
Report File Contents
text
======================================================================
📊 تقرير المسح الأمني الشامل
======================================================================

🎯 الهدف: https://example.com
🕐 وقت المسح: 2024-02-15 14:30:22

📍 معلومات الموقع الجغرافي:
----------------------------------------
  ip: 192.168.1.1
  city: New York
  country: United States
  latitude: 40.7128
  longitude: -74.0060
  isp: Cloudflare

🌐 النطاقات الفرعية (15):
----------------------------------------
  1. www.example.com
  2. mail.example.com
  3. admin.example.com
  ...

📁 الدلائل والملفات المكشوفة (5):
----------------------------------------
  1. /admin (الحالة: 200, الحجم: 2450 bytes)
  2. /backup.zip (الحالة: 200, الحجم: 1048576 bytes)
  ...
🎯 Use Cases
1. Security Auditing
Reconnaissance before penetration testing

Identify exposed sensitive paths

Detect potential attack vectors

2. Infrastructure Assessment
Discover all subdomains and related services

Map organizational assets

Verify SSL/TLS configuration

3. Compliance Testing
Check for exposed sensitive data

Validate security controls

Generate audit-ready reports

4. Competitive Intelligence
Understand competitor infrastructure

Map service providers and locations

Identify technology stacks

🔧 Customization
Add New Paths for Directory Scanning
python
additional_paths = [
    '/custom-admin',
    '/secure-dashboard',
    '/project-backup'
]
directories.extend(additional_paths)
Add New Subdomain Sources
python
# Add securitytrails.com API
url = f"https://api.securitytrails.com/v1/domain/{domain}/subdomains"
headers = {'APIKEY': 'your_api_key'}
response = requests.get(url, headers=headers)
Modify GeoIP API Configuration
python
api_key = "your_api_key"  # For premium APIs
url = f"https://api.ipgeolocation.io/ipgeo?apiKey={api_key}&ip={ip}"
⚠️ Important Notes
Legal Compliance: Only scan domains you own or have explicit permission to test

Rate Limiting: The tool includes timeout mechanisms but be mindful of target server resources

False Positives: Some detected paths may return 200 but not expose sensitive information

Geolocation Accuracy: Location data may vary between APIs and is approximate

Windows Paths: The current path uses Windows-style backslashes - modify for Linux/Mac

🛠️ Troubleshooting
Common Issues
Issue	Solution
ChromeDriver not found	Download matching ChromeDriver and add to PATH
SSL Certificate Errors	Use verify=False in requests (note: not recommended for production)
GeoIP API Rate Limits	Multiple APIs provide redundancy, check internet connection
Permission Denied	Ensure write permissions in output directory
Import Errors	Install missing packages with pip install
Debug Mode
python
import logging
logging.basicConfig(level=logging.DEBUG)
📝 Future Enhancements
API endpoint for integration with security tools

Export to PDF/CSV formats

Additional subdomain enumeration techniques

Real-time monitoring mode

Threat intelligence integration (VirusTotal, Shodan)

Vulnerability scanning integration

Docker containerization

Web-based dashboard

🤝 Contributing
We welcome contributions! Please follow these steps:

Fork the repository

Create a feature branch (git checkout -b feature/AmazingFeature)

Commit changes (git commit -m 'Add AmazingFeature')

Push to branch (git push origin feature/AmazingFeature)

Open a Pull Request

Coding Standards
PEP 8 compliance

Add docstrings for functions

Include error handling

Update documentation

📄 License
This project is licensed under the MIT License - see the LICENSE file for details.

⭐ Support
If you find this tool useful:

⭐ Star the repository

📝 Report issues on GitHub

🔗 Share with security researchers

