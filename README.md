# 🔐 Password Protected Image Encryption & Decryption

A **100% offline, frontend-only** solution to encrypt and decrypt images with password protection. No backend, no internet connection required, and no data leaves your computer.

---

## ✨ Features

- **Military-grade encryption**: AES-256-GCM algorithm
- **Key derivation**: PBKDF2 with 100,000 iterations prevents brute-force attacks
- **Unique security**: Different salt for each password, even identical passwords create different encrypted files
- **Offline-first**: Download and use anywhere without internet
- **No backend**: Everything runs in your browser using WebCrypto API
- **Open anywhere**: Encrypted files can be opened in any browser, anytime
- **User-friendly**: Simple, clean interface with password strength indicator

---

## 📁 Files Included

1. **encrypt-image.html** - Encrypt your photos with a password
2. **open-image.html** - Decrypt and view password-protected images
3. **README.md** - This file

---

## 🚀 How to Use

### Step 1: Encrypt an Image

1. Open **encrypt-image.html** in your web browser
2. Click "📷 Select Image" and choose a photo
3. Enter a strong password (6+ characters)
4. Confirm the password
5. (Optional) Give the encrypted file a custom name
6. Click "🔐 Encrypt & Download"
7. Your encrypted file (`.pwimg`) will be downloaded

**Example:**
- Original file: `vacation.jpg` (2 MB)
- Encrypted file: `vacation.pwimg` (2 MB) ← Safe to share!

### Step 2: Decrypt an Image

1. Open **open-image.html** in your web browser (or any browser, on any computer)
2. Click "📁 Select .pwimg File" and choose your encrypted image
3. Enter the password you used during encryption
4. Click "🔓 Decrypt & View"
5. Your decrypted image appears
6. Click "⬇️ Download Image" to save the original, or "📋 Copy to Clipboard" to copy it

---

## 🔒 Security Details

### Encryption Method
- **Algorithm**: AES-256-GCM (authenticated encryption)
- **Key Derivation**: PBKDF2 with SHA-256, 100,000 iterations
- **IV Length**: 12 bytes (random per encryption)
- **Salt Length**: 16 bytes (random per encryption)

### Why It's Secure
1. **Unique salt per password** → Different passwords create entirely different encrypted files
2. **PBKDF2 with 100,000 iterations** → Resists brute-force attacks (slow by design)
3. **AES-256-GCM** → Military-grade encryption with authentication (detects tampering)
4. **Random IV** → Same image encrypted twice produces different files

### File Format
```
[Magic: "PWIMG"] [Version: 1] [Salt: 16 bytes] [IV: 12 bytes] [Encrypted Image Data]
```

---

## 💻 Browser Compatibility

Works on all modern browsers that support WebCrypto API:
- ✅ Chrome/Edge 37+
- ✅ Firefox 34+
- ✅ Safari 11+
- ✅ Opera 24+
- ❌ Internet Explorer (not supported)

---

## 🛡️ Privacy & Safety

✓ **Zero data sent to servers** - Everything happens on your computer  
✓ **No cookies or tracking** - Your data is your own  
✓ **Open source algorithm** - Uses standard WebCrypto API  
✓ **Offline mode** - Disconnect internet and still works  
✓ **Safe to share** - Encrypted files are unreadable without password  

---

## 📋 Password Tips

For maximum security:
- Use at least 12 characters
- Mix uppercase, lowercase, numbers, and symbols: `P@ssw0rd!2024`
- Avoid dictionary words
- Use a unique password for each image
- Store passwords securely (password manager)

**Password Strength Indicator:**
- **Weak**: Short, single type of character
- **Fair**: 8+ chars or mixed types
- **Good**: 12+ chars with numbers/letters/symbols
- **Strong**: 12+ chars with all character types
- **Very Strong**: 16+ chars with all character types

---

## ⚡ Quick Start (3 Steps)

### Encrypt
```
1. Open encrypt-image.html
2. Select image → Enter password → Click "Encrypt & Download"
3. Get: my-photo.pwimg
```

### Decrypt
```
1. Open open-image.html (anywhere, anytime)
2. Select my-photo.pwimg → Enter password → Click "Decrypt & View"
3. See your image!
```

---

## ❓ FAQ

**Q: What if I forget the password?**  
A: The encryption is so strong that even with today's technology, it's impossible to decrypt without the correct password. Store it securely!

**Q: Can I share the .pwimg files?**  
A: Yes! They're completely safe to share on email, cloud storage, or messaging apps. Only someone with the password can open them.

**Q: Does the website collect my data?**  
A: No. These are standalone HTML files. They never connect to the internet. Open the file directly in your browser.

**Q: Can I edit the encrypted image?**  
A: No, you must decrypt it first. Then edit the original image and re-encrypt it if needed.

**Q: What if the file gets corrupted?**  
A: The decryptor will show an error. The file integrity is verified during decryption. Keep backups of important encrypted files.

**Q: Can I use on mobile?**  
A: Yes! Works on mobile browsers (Chrome, Safari, Firefox on iOS/Android).

**Q: Is the encryption reversible?**  
A: No, but you have the original image. The encrypted file is only meant for storage and transfer.

---

## 🔧 Technical Stack

- **Language**: Vanilla JavaScript (no frameworks)
- **Encryption**: WebCrypto API (built into browsers)
- **No external dependencies**: Zero npm packages required
- **No backend**: Pure client-side processing

---

## 📦 File Size

- encrypt-image.html: ~8 KB
- open-image.html: ~10 KB
- Total: ~18 KB
- **No external libraries to download**

---

## ✅ What Happens When You Encrypt

1. ✓ Your password is read
2. ✓ A random 16-byte salt is generated
3. ✓ Your password + salt → 256-bit encryption key (using PBKDF2)
4. ✓ A random 12-byte IV is generated
5. ✓ Image is encrypted with AES-256-GCM
6. ✓ Magic header + salt + IV + encrypted data → .pwimg file
7. ✓ File is downloaded to your computer
8. ✓ **Everything is deleted from browser memory** ✓

---

## ✅ What Happens When You Decrypt

1. ✓ You upload the .pwimg file
2. ✓ You enter the password
3. ✓ Magic header is verified
4. ✓ Salt is extracted from file
5. ✓ Your password + extracted salt → same 256-bit key (using PBKDF2)
6. ✓ IV is extracted from file
7. ✓ Image is decrypted with AES-256-GCM
8. ✓ If password is wrong, decryption fails (security feature)
9. ✓ Decrypted image is displayed in browser

---

## 🎯 Use Cases

- **Private photos**: Protect personal/family photos
- **Confidential documents**: Encrypt scanned documents
- **Backup security**: Encrypt sensitive backups
- **Safe cloud storage**: Upload encrypted to cloud without worrying
- **Secure sharing**: Send via email/messaging without exposure
- **Long-term archival**: Encrypted files remain secure for years

---

## 📝 License

Public Domain - Use freely for any purpose.

---

## 🤝 Support

No support needed! These are standalone files. If you encounter issues:
1. Clear browser cache and try again
2. Try a different browser
3. Check file format (must be .pwimg for decryption)
4. Ensure password is correct (case-sensitive)

---

**Created with ❤️ for privacy**

🔐 Your data. Your password. Your control.
