# API Documentation

## Overview

This document describes the data structure and usage patterns for the Open Hymnal JSON Database.

## Data Schema

### Hymn Object Structure

```json
{
  "id": "string (required)",
  "title": "string (required)",
  "author": "string (optional)",
  "lyrics": "array (required)",
  "metadata": "object (required)"
}
```

### Detailed Field Descriptions

#### `id` (string, required)
- **Format**: `kebab-case-title` or `church-name-hymn-number`
- **Example**: `"amazing-grace"` or `"watchman-001"`
- **Purpose**: Unique identifier for each hymn

#### `title` (string, required)
- **Format**: Title case
- **Example**: `"Amazing Grace"`
- **Purpose**: Display name of the hymn

#### `author` (string, optional)
- **Format**: "First Last" or "Unknown"
- **Example**: `"John Newton"` or `"Unknown"`
- **Purpose**: Original hymn author/composer

#### `lyrics` (array, required)
- **Structure**: Array of verse objects
- **Example**:
```json
"lyrics": [
  {
    "verse": 1,
    "content": "Amazing grace how sweet the sound\nThat saved a wretch like me",
    "type": "verse"
  },
  {
    "content": "Twas grace that taught my heart to fear\nAnd grace my fears relieved",
    "type": "chorus"
  }
]
```

#### `metadata` (object, required)
- **Structure**: Contains hymn metadata
- **Example**:
```json
"metadata": {
  "church": "Watchman Church",
  "language": "en",
  "category": "worship",
  "year": 2023,
  "hymn_number": "001",
  "key": "G",
  "tempo": "moderate",
  "theme": ["grace", "salvation"],
  "scripture_reference": "Ephesians 2:8-9"
}
```

##### Metadata Fields:
- `church` (string, required): Source church name
- `language` (string, required): ISO language code (e.g., "en", "es", "fr")
- `category` (string, required): One of: "worship", "praise", "prayer", "communion", "easter", "christmas", "funeral", "wedding"
- `year` (number, optional): Year added to collection
- `hymn_number` (string, optional): Original hymn book number
- `key` (string, optional): Musical key
- `tempo` (string, optional): "slow", "moderate", "fast"
- `theme` (array, optional): Array of theme tags
- `scripture_reference` (string, optional): Related Bible verse

## Usage Examples

### JavaScript/Node.js

```javascript
const fs = require('fs');

// Load hymn collection
const hymns = JSON.parse(fs.readFileSync('hymns/watchman/watchman-hymns.json', 'utf8'));

// Find hymn by title
const findHymnByTitle = (title) => {
  return hymns.find(hymn => 
    hymn.title.toLowerCase().includes(title.toLowerCase())
  );
};

// Filter by category
const getHymnsByCategory = (category) => {
  return hymns.filter(hymn => hymn.metadata.category === category);
};

// Get all hymns with chorus
const getHymnsWithChorus = () => {
  return hymns.filter(hymn => hymn.chorus);
};

// Search by theme
const searchByTheme = (theme) => {
  return hymns.filter(hymn => 
    hymn.metadata.theme && hymn.metadata.theme.includes(theme)
  );
};
```

### Python

```python
import json

# Load hymn collection
with open('hymns/watchman/watchman-hymns.json', 'r') as f:
    hymns = json.load(f)

# Find hymn by ID
def find_hymn_by_id(hymn_id):
    return next((hymn for hymn in hymns if hymn['id'] == hymn_id), None)

# Get formatted lyrics
def get_formatted_lyrics(hymn):
    lyrics = []
    
    for verse in hymn['verses']:
        lyrics.append(f"Verse {verse['number']}:")
        lyrics.append(verse['lyrics'])
        
        # Add chorus after each verse if exists
        if 'chorus' in hymn:
            lyrics.append("\nChorus:")
            lyrics.append(hymn['chorus']['lyrics'])
        
        lyrics.append("")  # Empty line between verses
    
    return "\n".join(lyrics)

# Filter by language
def get_hymns_by_language(language_code):
    return [hymn for hymn in hymns if hymn['metadata']['language'] == language_code]
```

### React/React Native

```javascript
import React, { useState, useEffect } from 'react';
import hymnsData from '../hymns/watchman/watchman-hymns.json';

const HymnBook = () => {
  const [hymns, setHymns] = useState([]);
  const [searchTerm, setSearchTerm] = useState('');
  const [selectedCategory, setSelectedCategory] = useState('all');

  useEffect(() => {
    setHymns(hymnsData);
  }, []);

  const filteredHymns = hymns.filter(hymn => {
    const matchesSearch = hymn.title.toLowerCase().includes(searchTerm.toLowerCase());
    const matchesCategory = selectedCategory === 'all' || hymn.metadata.category === selectedCategory;
    return matchesSearch && matchesCategory;
  });

  return (
    <div>
      <input 
        type="text" 
        placeholder="Search hymns..."
        value={searchTerm}
        onChange={(e) => setSearchTerm(e.target.value)}
      />
      
      <select 
        value={selectedCategory}
        onChange={(e) => setSelectedCategory(e.target.value)}
      >
        <option value="all">All Categories</option>
        <option value="worship">Worship</option>
        <option value="praise">Praise</option>
        <option value="prayer">Prayer</option>
      </select>

      {filteredHymns.map(hymn => (
        <div key={hymn.id}>
          <h3>{hymn.title}</h3>
          <p>By: {hymn.author}</p>
          <p>Category: {hymn.metadata.category}</p>
        </div>
      ))}
    </div>
  );
};
```

## File Organization

### Single Church Collection
```
hymns/
└── church-name/
    └── church-name-hymns.json
```

### Multiple Files (for large collections)
```
hymns/
└── church-name/
    ├── worship-hymns.json
    ├── praise-hymns.json
    ├── seasonal-hymns.json
    └── index.json  // Contains references to all files
```

## Validation

### JSON Schema (for validation tools)
```json
{
  "$schema": "http://json-schema.org/draft-07/schema#",
  "type": "array",
  "items": {
    "type": "object",
    "required": ["id", "title", "lyrics", "metadata"],
    "properties": {
      "id": { "type": "string" },
      "title": { "type": "string" },
      "author": { "type": "string" },
      "verses": {
        "type": "array",
        "items": {
          "type": "object",
          "required": ["number", "lyrics"],
          "properties": {
            "number": { "type": "number" },
            "lyrics": { "type": "string" }
          }
        }
      },
      "chorus": {
        "type": "object",
        "properties": {
          "lyrics": { "type": "string" }
        }
      },
      "metadata": {
        "type": "object",
        "required": ["church", "language", "category"],
        "properties": {
          "church": { "type": "string" },
          "language": { "type": "string" },
          "category": { "type": "string" },
          "year": { "type": "number" },
          "hymn_number": { "type": "string" },
          "key": { "type": "string" },
          "tempo": { "type": "string" },
          "theme": { "type": "array", "items": { "type": "string" } },
          "scripture_reference": { "type": "string" }
        }
      }
    }
  }
}
```

## Error Handling

### Common Issues
- **Missing required fields**: Ensure all required fields are present
- **Invalid JSON**: Validate JSON syntax before submitting
- **Duplicate IDs**: Each hymn must have a unique ID
- **Malformed verses**: Verses must be properly numbered and contain lyrics

### Best Practices
- Always validate JSON before committing
- Use consistent formatting for titles and authors
- Include meaningful metadata
- Test with actual usage scenarios
