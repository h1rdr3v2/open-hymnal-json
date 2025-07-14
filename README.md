# Open Hymnal JSON Database 🎵

**A community-driven collection of church hymns in JSON format for developers and digital worship applications.**

## 🎯 About

While building a mobile hymn book app, I searched extensively for digital hymn collections but found none readily available. This repository was born from that need - starting with 300 hymns from the Watchman church and growing into a comprehensive, open-source hymnal database.

This project aims to provide developers with easy-to-use hymn data for building worship apps, church websites, and digital songbooks.

## 📊 Current Collection

- **300+ hymns** from Watchman church
- **JSON format** for easy integration
- **Structured data** with lyrics, verses, and metadata
- **Growing collection** with community contributions

## 🚀 Quick Start

```bash
git clone https://github.com/h1rdr3v2/open-hymnal-json.git
cd open-hymnal-json
```

### Example Usage

Loading the hymn directly from folder

```javascript
// Load hymn data
const hymns = require('./hymns/watchman/hymns.json');

// Find a specific hymn
const hymn = hymns.find(h => h.title === "Amazing Grace");
console.log(hymn.lyrics);
```

Loading it remotely from this repo
```typescript
// GitHub repository details
const GITHUB_USERNAME = 'h1rdr3v2';
const GITHUB_REPO = 'open-hymnal-json';
const GITHUB_BRANCH = 'main';

const GITHUB_RAW_URL = `https://raw.githubusercontent.com/${GITHUB_USERNAME}/${GITHUB_REPO}/${GITHUB_BRANCH}/watchman/hymns.json`;

async fetchHymnsData(): Promise<Hymn[]> { // For this type check the examples folder 
    try {
        const response = await fetch(`${GITHUB_RAW_URL}?v=${Date.now()}`);
        if (!response.ok) throw new Error('Failed to fetch hymns data');
        return await response.json();
    } catch (error) {
        console.error('Error fetching hymns data:', error);
        throw error;
    }
},

```

## 📁 Data Structure

Each church hymn follows this JSON structure:

```json
{
  "version": "version_no",
  "last_updated": "YYYY-MM-DD",
  "hymns":{
    "id": "unique-identifier",
    "number": "Hymn Number",
    "title": "Hymn Title",
    "author": "Author Name",
    "lyrics": [
      {
        "verse": 1,
        "content": "Verse lyrics here..."
        "verse": "verse or chorus"
      }
    ]
  },
  "metadata": {
    "church": "Church Name",
    "language": "en",
    "category": "worship",
    "year": 2023
  }
}
```

## 🤝 Contributing

We welcome contributions from all churches and denominations! Here's how to help:

### Adding New Hymns

1. **Fork** this repository
2. **Create** a new branch: `git checkout -b add-[church-name]-hymns`
3. **Add** your hymns following the JSON structure above
4. **Organize** hymns in appropriate folders: `/hymns/[church-name]/`
5. **Submit** a pull request with a clear description

### Contribution Guidelines

- ✅ Follow the exact JSON structure
- ✅ Include complete hymn information (title, author, verses, chorus)
- ✅ Ensure lyrics are accurate and properly formatted
- ✅ Add appropriate metadata (church, language, category)
- ✅ One hymn per JSON object in the array
- ✅ Use meaningful file names: `[church-name]-hymns.json`

### Quality Standards

- Lyrics must be complete and accurate
- Proper attribution to authors
- Respect copyright laws
- Include source verification when possible

## 🏗️ Project Structure

```
open-hymnal-json/
├── hymns/
│   ├── watchman/
│   │   └── hymns.json
│   ├── [other-churches]/
│   └── README.md
├── examples/
│   ├── javascript/
│   ├── python/
│   └── mobile-apps/
├── docs/
│   ├── API.md
│   └── CONTRIBUTING.md
├── LICENSE
└── README.md
```

## 🌍 Multi-Language Support

While currently focused on English hymns, we welcome contributions in other languages:

- Use appropriate language codes in metadata (`"language": "es"` for Spanish)
- Organize by language folders when necessary
- Include translation credits when applicable

## 📱 Use Cases

- **Mobile Apps**: Hymn book applications
- **Church Websites**: Digital songbooks
- **Worship Software**: Integration with presentation tools
- **APIs**: Backend services for worship applications
- **Research**: Academic studies on hymnology

## 🎨 Example Integrations

Check out the `/examples` folder for:
- React Native mobile app integration
- Web application examples
- Python script usage
- API endpoint implementations

## 📄 License

This project is open source and available under the [MIT License](LICENSE).

## 🙏 Acknowledgments

- Started with hymns from the Watchman church
- Thanks to all contributors who help expand this collection
- Special recognition to churches sharing their hymnal resources

## 📞 Support

- **Issues**: Report bugs or request features via GitHub Issues
- **Discussions**: Join conversations in GitHub Discussions
- **Pull Requests**: All contributions are reviewed and welcomed

---

**Made with ❤️ for the global church community**

*"Speak to one another with psalms, hymns, and songs from the Spirit" - Ephesians 5:19*
