markdown# Missing Persons Registry - Thai-Cambodia Conflict
## ប្រព័ន្ធកត់ត្រាអ្នកបាត់ខ្លួនពីជម្លោះថៃ-កម្ពុជា

A memorial website dedicated to documenting and remembering those who went missing during the Thai-Cambodia conflicts and related historical events. This system allows families and communities to register missing persons information to preserve their memory and assist in potential search efforts.

## 🌐 Live Demo
**Website:** [https://khmerlost.netlify.app](https://khmerlost.netlify.app)

## 📋 Features

### Core Functionality
- **Missing Persons Registry** - Add up to 10 missing persons per submission
- **Real-time Database** - Powered by Firebase Firestore with live updates
- **Photo Upload** - Store photos in Firebase Cloud Storage
- **Search & Filter** - Find records by name, province, or status
- **Pagination** - Display 50, 100, 500 records or view all
- **Mobile Responsive** - Works on all devices

### Data Fields
- Full Name (Required)
- Age at time of disappearance
- Gender
- Province/District
- Contact Information (Phone & Email)
- Photo
- Year of disappearance
- Status (Missing in war, Captured, Escaped, etc.)
- Contributor information

### User Interface
- **Khmer Language** - Full interface in Cambodian
- **Memorial Theme** - Respectful dark theme appropriate for the subject
- **Real-time Counter** - Live count of total missing persons
- **Connection Status** - Firebase connection indicator

## 🛠️ Technology Stack

### Frontend
- **HTML5** - Semantic markup
- **CSS3** - Modern styling with Flexbox/Grid
- **Vanilla JavaScript** - No external frameworks
- **Google Fonts** - Noto Sans Khmer for proper text rendering

### Backend & Database
- **Firebase Firestore** - NoSQL real-time database
- **Firebase Storage** - Cloud storage for photos
- **Firebase Hosting** - Static site hosting option

### Hosting & Analytics
- **Netlify** - Primary hosting platform
- **Google Analytics** - User behavior tracking
- **GitHub** - Source code repository

## 🚀 Deployment

### Prerequisites
- Firebase Project with Firestore and Storage enabled
- Google Analytics property (optional)
- Netlify or Firebase Hosting account

### Quick Deploy to Netlify
1. Fork this repository
2. Create Firebase project and get config
3. Update `firebaseConfig` in `index.html`
4. Connect repository to Netlify
5. Deploy automatically

### Firebase Setup
1. Create new Firebase project
2. Enable Firestore Database in test mode
3. Enable Storage in test mode
4. Copy configuration to `firebaseConfig` object
5. Configure security rules (see below)

### Security Rules

**Firestore Rules:**
```javascript
rules_version = '2';
service cloud.firestore {
  match /databases/{database}/documents {
    match /missingPersons/{document} {
      allow read: if true;
      allow create: if isValidMissingPerson();
      allow update, delete: if false;
    }
  }
  
  function isValidMissingPerson() {
    return request.resource.data.keys().hasAll(['fullName', 'contributor']) &&
           request.resource.data.fullName is string &&
           request.resource.data.fullName.size() > 0;
  }
}
Storage Rules:
javascriptrules_version = '2';
service firebase.storage {
  match /b/{bucket}/o {
    match /photos/{allPaths=**} {
      allow read: if true;
      allow write: if request.resource.size < 5 * 1024 * 1024 
                   && request.resource.contentType.matches('image/.*');
    }
  }
}
📊 Analytics & Monitoring
The website includes Google Analytics integration to track:

User engagement - Page views, session duration
Demographics - Geographic distribution of users
Usage patterns - Popular features and user flow
Performance metrics - Load times and bounce rates

🔒 Privacy & Ethics
Data Protection

Minimal data collection focused on memorial purposes
No personal data of contributors beyond name
Photos and contact information are optional
GDPR-compliant data handling practices

Ethical Considerations

Respectful presentation of sensitive historical content
Warning messages about the serious nature of the content
Emphasis on memorial and remembrance purpose
Community-driven content moderation

🌍 Internationalization
Currently supports:

Khmer (Cambodian) - Primary language
English - Documentation and technical content

Future language support planned:

Thai
Vietnamese
Additional Southeast Asian languages

🤝 Contributing
How to Contribute

Content: Help verify and add missing persons information
Translation: Assist with additional language support
Development: Submit bug fixes and feature improvements
Documentation: Improve guides and help content

Development Setup
bashgit clone https://github.com/yourusername/cambodia-missing-persons
cd cambodia-missing-persons
# No build process required - open index.html in browser
Code Style

Semantic HTML5
Modern CSS (Flexbox/Grid)
Vanilla JavaScript (ES6+)
Khmer language comments for UI elements

📈 Performance
Optimization Features

Lazy Loading - Images load on demand
Pagination - Efficient data loading
CDN Delivery - Firebase/Netlify global distribution
Caching - Browser and Firebase caching strategies

Scalability

Firebase Firestore - Handles thousands of concurrent users
Real-time Updates - Instant data synchronization
Global Distribution - Works worldwide with minimal latency

📞 Support & Contact
Technical Issues

Create an issue on GitHub
Include browser version and error details
Provide steps to reproduce problems

Content & Historical Information

Contact via website form
Email: [contact information]
Respectful inquiries only

📜 License
This project is licensed under the MIT License - see the LICENSE file for details.
Additional Terms

Content must be used respectfully and ethically
Commercial use requires permission
Historical accuracy is encouraged but not guaranteed
Community guidelines must be followed

🙏 Acknowledgments

Families and survivors who share their stories
Historical researchers providing context
Open source community for technical foundations
Firebase and Netlify for hosting infrastructure

🕊️ Memorial Statement
This website serves as a digital memorial to honor those who went missing during conflicts in Southeast Asia. Their memory lives on through the courage of those who refuse to let them be forgotten.

Built with respect and remembrance 🕊️
"Peace is the only way to ensure no more Khmer children go missing"
