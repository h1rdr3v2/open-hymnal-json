# Contributing Guidelines

Thank you for your interest in contributing to the Open Hymnal JSON Database! This guide will help you contribute effectively.

## 🎯 How to Contribute

### Types of Contributions

1. **Adding New Hymns** - Submit hymns from your church or denomination
2. **Improving Documentation** - Help make the project clearer
3. **Bug Fixes** - Fix errors in existing hymns
4. **Feature Requests** - Suggest improvements to the data structure
5. **Translation** - Add hymns in different languages

## 📝 Before You Start

### Prerequisites
- Basic knowledge of JSON format
- Understanding of hymn structure (verses, chorus, etc.)
- Access to accurate hymn texts and attributions

### Setting Up
1. Fork the repository
2. Clone your fork locally
3. Create a new branch for your contribution
4. Make your changes
5. Test your JSON files
6. Submit a pull request

## 🎵 Adding Hymns

### Step 1: Prepare Your Hymns

Collect the following information for each hymn:
- ✅ **Title** (exact spelling)
- ✅ **Author** (if known)
- ✅ **Complete lyrics** (all verses)
- ✅ **Chorus** (if applicable)
- ✅ **Source church/denomination**
- ✅ **Any additional metadata**

### Step 2: Follow the JSON Structure

Use this template for each hymn:

```json
{
  "id": "hymn-unique-id",
  "title": "Hymn Title",
  "author": "Author Name",
  "verses": [
    {
      "number": 1,
      "lyrics": "First verse lyrics here\nSecond line of verse"
    },
    {
      "number": 2,
      "lyrics": "Second verse lyrics here\nSecond line of verse"
    }
  ],
  "chorus": {
    "lyrics": "Chorus lyrics here\nSecond line of chorus"
  },
  "metadata": {
    "church": "Your Church Name",
    "language": "en",
    "category": "worship",
    "year": 2023,
    "hymn_number": "001",
    "theme": ["praise", "worship"],
    "scripture_reference": "Psalm 150:1"
  }
}
```

### Step 3: File Organization

#### For New Churches
Create a new folder structure:
```
hymns/
└── your-church-name/
    └── hymns.json
```

#### For Existing Churches
Add to the existing JSON file or create category-specific files:
```
hymns/
└── existing-church/
    ├── worship-hymns.json
    ├── praise-hymns.json
    └── seasonal-hymns.json
```

### Step 4: Naming Conventions

#### File Names
- Use kebab-case: `methodist-hymns.json`
- Be descriptive: `catholic-latin-hymns.json`
- Include category if specific: `baptist-christmas-hymns.json`

#### Hymn IDs
- Use kebab-case: `amazing-grace`
- Include church prefix if needed: `watchman-001`
- Keep consistent within your collection

#### Folders
- Use kebab-case: `methodist-church`
- Keep church names clear and official

## ✅ Quality Standards

### Lyrics Requirements
- **Accuracy**: Verify lyrics against official sources
- **Completeness**: Include all verses typically sung
- **Formatting**: Use `\n` for line breaks within verses
- **Spelling**: Use proper spelling and punctuation

### Attribution Requirements
- **Author Credit**: Include original author when known
- **Source Credit**: Specify your church/denomination
- **Copyright Respect**: Only include public domain or properly licensed hymns

### JSON Requirements
- **Valid JSON**: Test your JSON in a validator
- **Required Fields**: Include all required fields
- **Consistent Structure**: Follow the exact schema
- **Proper Encoding**: Use UTF-8 encoding

## 🔍 Review Process

### Before Submitting
- [ ] JSON is valid and properly formatted
- [ ] All required fields are included
- [ ] Lyrics are accurate and complete
- [ ] Metadata is properly filled
- [ ] File is in the correct location
- [ ] No duplicate IDs exist

### Pull Request Template
Use this template for your PR description:

```markdown
## 📋 Pull Request Description

**Type of Contribution:** [New Hymns/Bug Fix/Documentation/Other]

**Church/Denomination:** [Your Church Name]

**Number of Hymns Added:** [Number]

**Language:** [English/Spanish/French/Other]

## ✅ Checklist
- [ ] JSON is valid and tested
- [ ] All required fields included
- [ ] Lyrics verified for accuracy
- [ ] Proper attribution included
- [ ] Follows naming conventions
- [ ] No duplicate IDs

## 📝 Additional Notes
[Any special notes about the hymns, sources, or formatting]
```

## 🌍 Multi-Language Contributions

### Language Codes
Use ISO 639-1 language codes:
- English: `"en"`
- Spanish: `"es"`
- French: `"fr"`
- German: `"de"`
- Portuguese: `"pt"`

### Translation Guidelines
- Include original language in metadata if translated
- Credit translator when applicable
- Maintain original meaning and structure
- Use proper cultural context

## 🛠️ Tools and Resources

### JSON Validators
- [JSONLint](https://jsonlint.com/)
- [JSON Formatter](https://jsonformatter.curiousconcept.com/)

### Text Editors
- VS Code with JSON extensions
- Sublime Text with JSON formatting
- Any editor with JSON syntax highlighting

### Testing Your Contribution
```bash
# Validate JSON syntax
python -m json.tool your-hymns.json

# Check file structure
ls -la hymns/your-church/
```

## 🚫 What NOT to Include

### Copyright Issues
- ❌ Recently copyrighted hymns without permission
- ❌ Commercial hymns under active copyright
- ❌ Lyrics from copyrighted songbooks

### Quality Issues
- ❌ Incomplete or partial lyrics
- ❌ Unverified or inaccurate lyrics
- ❌ Improperly formatted JSON
- ❌ Missing required metadata

### Content Issues
- ❌ Duplicate hymns already in the database
- ❌ Non-hymn content (prayers, readings, etc.)
- ❌ Inappropriate or offensive content

## 📞 Getting Help

### Questions?
- Open an issue for questions
- Check existing issues first
- Use clear, descriptive titles

### Issues to Report
- JSON formatting errors
- Incorrect hymn information
- Missing metadata
- Duplicate entries
- Copyright concerns

## 🎉 Recognition

Contributors will be recognized in:
- Repository contributors list
- Annual acknowledgments
- Special mentions for significant contributions

## 📄 Legal

By contributing, you agree that:
- Your contributions are your own work or properly licensed
- You have rights to submit the content
- Your contributions will be available under the project's MIT license
- You respect copyright and intellectual property laws

---

**Thank you for helping build a comprehensive hymnal resource for the global church community!**
