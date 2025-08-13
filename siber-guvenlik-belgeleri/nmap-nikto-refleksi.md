# 🧠 Siber Güvenlik Refleksi: Apache ve CUPS Üzerinde Nmap & Nikto Test Süreci  
## 🧠 Cybersecurity Reflex: Nmap & Nikto Testing on Apache and CUPS

> 🇹🇷 Bu belge, Ubuntu VM üzerinde çalışan Apache ve CUPS servislerine yönelik temel sızma testlerini, port taramalarını ve yapılandırma analizlerini içermektedir.  
Her test bir üretim refleksi, her yorum bir dijital kimlik adımıdır.

> 🇬🇧 This document presents basic penetration tests, port scans, and configuration analysis on Apache and CUPS running on Ubuntu VM.  
Each test is a production reflex, each interpretation a step toward digital identity.

---

## 🔍 Test Süreci / Testing Process

### ✅ Nmap Taramaları

- `nmap -sS -Pn -p- 127.0.0.1` → Full SYN scan across all ports  
- `nmap -sV -p 80,631 127.0.0.1` → Service and version detection for Apache & CUPS  
- `nmap -sC -p 80,631 127.0.0.1` → Default script scan: headers, SSL, robots.txt  
- `nmap --script http-headers -p 80 127.0.0.1` → HTTP header analysis  
- `nmap --script ssl-cert -p 443 127.0.0.1` → SSL certificate check (port closed)

### ✅ Nikto Analizi / Nikto Analysis

- `nikto -h http://127.0.0.1` → Apache configuration audit  
- Tespitler / Findings:
  - `Server: Apache/2.4.58 (Ubuntu)` → Version disclosure  
  - `ETag inode leak` → Filesystem metadata exposure  
  - `X-Frame-Options header missing` → Clickjacking risk  
  - `Allowed Methods: HEAD, GET, POST, OPTIONS` → Potential info leakage  
  - `OSVDB-561: /server-status` → Configuration endpoint exposed

---

## 📘 Teknik Yorum / Technical Reflection

> 🇹🇷 Apache yapılandırması OWASP yönergelerine göre güncellenmelidir.  
Güvenlik başlıkları eklenmeli, sürüm bilgisi gizlenmeli, dizin listesi kapatılmalıdır.

> 🇬🇧 Apache configuration should be updated according to OWASP guidelines.  
Security headers must be added, version info hidden, and directory listing disabled.

---

## 📣 Katkı Çağrısı / Contribution Call

> 🇹🇷 Bu belgeyi birlikte geliştirebiliriz. Testlerinizi, yorumlarınızı ve düzeltmelerinizi paylaşın.  
Toplulukla üretmek, teknik kimliğimizi güçlendirir.

> 🇬🇧 Let’s improve this document together. Share your tests, insights, and suggestions.  
Producing with the community strengthens our technical identity.

---

## 🧠 Üretici Notu / Creator’s Note

> 🇹🇷 Bu belge, teknik üretimin sadece komut değil; muhakeme, karakter ve toplulukla gelişen bir süreç olduğunu gösterir.  
Her test bir refleks, her yorum bir kimlik adımıdır.

> 🇬🇧 This document shows that technical production is not just about commands, but about reasoning, character, and community.  
Each test is a reflex, each interpretation a step toward identity.

---

## 🏷️ Etiketler / Tags

`#cybersecurity` `#pentest` `#linux` `#apache` `#nmap` `#nikto`  
`#documentation` `#opensource` `#reflection` `#community` `#bilingual`

---

## 📅 Test Tarihi / Test Date

- 🇹🇷 13 Ağustos 2025 – Ubuntu VM üzerinde gerçek zamanlı test ortamı  
- 🇬🇧 August 13, 2025 – Real-time testing on Ubuntu VM
