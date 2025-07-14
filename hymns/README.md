# Hymns Collection

This directory contains the hymn database organized by church/denomination and language.

## 📁 Directory Structure

```
hymns/
├── watchman/
│   └── watchman-hymns.json
├── example-multilingual/
│   ├── spanish/
│   │   └── himnos-espanol.json
│   ├── french/
│   │   └── hymnes-francais.json
│   └── portuguese/
│       └── hinos-portugues.json
└── traditional/
    └── classic-hymns.json
```

## 📊 Current Statistics

| Church/Collection | Hymns Count | Language | Last Updated |
|------------------|-------------|----------|--------------|
| Watchman         | 300         | English  | 2025-01-17   |
| Methodist        | 0           | English  | -            |
| Baptist          | 0           | English  | -            |
| Traditional      | 0           | English  | -            |

## 🔍 JSON File Standards

### File Naming Convention
- Use lowercase with hyphens: `church-name-hymns.json`
- For multilingual: `hymns-[language-code].json`
- For specific collections: `[collection-name]-hymns.json`


## 📋 Metadata Guidelines

### Required Fields
- `id`: Unique identifier (use format: `church-hymn-number` or `church-title-slug`)
- `title`: Full hymn title
- `author`: Author/composer name (use "Unknown" if not available)
- `lyrics`: Array of verse objects with number and lyrics
- `metadata.church`: Source church/denomination
- `metadata.language`: ISO 639-1 language code

### Optional Fields
- `chorus`: Chorus/refrain object with lyrics
- `bridge`: Bridge section lyrics
- `metadata.year`: Year written/published
- `metadata.hymnbook_number`: Number in source hymnbook
- `metadata.category`: Category (worship, praise, communion, etc.)
- `metadata.themes`: Array of themes/topics
- `metadata.scripture_reference`: Related Bible verses
- `metadata.key`: Musical key
- `metadata.tempo`: Tempo marking
- `metadata.copyright`: Copyright information

## 🏷️ Category Guidelines

Use these standardized categories in `metadata.category`:

- `worship` - General worship songs
- `praise` - Praise and adoration
- `communion` - Communion/Lord's Supper
- `baptism` - Baptism songs
- `christmas` - Christmas hymns
- `easter` - Easter hymns
- `funeral` - Funeral/memorial songs
- `wedding` - Wedding songs
- `thanksgiving` - Thanksgiving hymns
- `missions` - Missionary songs
- `children` - Children's songs
- `prayer` - Prayer songs
- `salvation` - Salvation themes
- `discipleship` - Christian living/discipleship

## 🌍 Language Codes

Use ISO 639-1 language codes:

- `en` - English
- `es` - Spanish
- `fr` - French
- `de` - German
- `pt` - Portuguese
- `it` - Italian
- `zh` - Chinese
- `ko` - Korean
- `ja` - Japanese
- `ar` - Arabic
- `hi` - Hindi
- `sw` - Swahili

## ✅ Quality Checklist

Before submitting hymns, ensure:

- [ ] JSON is valid and properly formatted
- [ ] All required fields are present
- [ ] Lyrics are complete and accurate
- [ ] Author attribution is correct
- [ ] File follows naming convention
- [ ] Metadata is complete and accurate
- [ ] No duplicate hymns within the same collection
- [ ] Copyright considerations are respected

## 📝 Adding New Collections

### For New Churches/Denominations:
1. Create a new folder: `/hymns/[church-name]/`
2. Add hymns file: `[church-name]-hymns.json`
3. Update the statistics table above
4. Submit pull request with collection details

### For Multilingual Collections:
1. Use existing church folder or create new one
2. Add language subfolder if needed
3. Use appropriate language code in filename
4. Include `"language": "[code]"` in metadata

## 🔧 Validation Tools

You can validate your JSON files using:
- Online JSON validators
- `jsonlint` command-line tool

## 🤝 Contributing Guidelines

1. **One hymn per object** in the JSON array
2. **Consistent formatting** - use proper indentation
3. **Complete information** - fill all available fields
4. **Accurate lyrics** - double-check for typos
5. **Proper attribution** - credit authors correctly
6. **Respect copyright** - only include hymns you have rights to use

## 📞 Need Help?

- Check the main [CONTRIBUTING.md](../CONTRIBUTING.md) file
- Open an issue for questions
- Review existing hymn files for examples
- Join the GitHub Discussions for community help

## 🎵 Example Hymn Files

Check these files for reference:
- `/hymns/watchman/watchman-hymns.json` - Complete example
