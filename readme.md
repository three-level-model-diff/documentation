# Table of content

# 1. Mechanical operations
There are only two mechanical operations: INS and DEL. 
Mechanical operations act EXCLUSIVELY at string level: markup operations are still expressed as INS and DEL.

## 1.1 Insertion (INS)

```
Insertion of a string of characters (markup included)
{
  "id": "edit-00001",
  "op": "INS",
  "pos": 80,
  "content": "nuovo"
}
{
  "id": "edit-00003",
  "op": "INS",
  "pos": 100,
  "content": "</p><p>"
}
{
  "id": "edit-00005",
  "op": "INS",
  "by": "Fabio Vitali",
  "timestamp": "2018-03-10T07:25:23.891Z", 
  "pos": 120,
  "content": "new content"
}
```
## 1.2 Delete (DEL)

```
Removal of a string of characters (markup included)
{
  "id": "edit-00002",
  "op": "DEL",
  "pos": 90,
  "content": "vecchio"
}
{
  "id": "edit-00004",
  "op": "DEL",
  "pos": 110,
  "content": "part of the first paragraph.<p>Part of "
}
{
  "id": "edit-00006",
  "op": "DEL",
  "by": "Fabio Vitali",
  "timestamp": "2018-03-10T07:25:23.891Z", 
  "pos": 130,
  "content": "old content"
}
```
# 2. Structural operations

## 3.1 Operations on text

### 3.1.1. Punctuation

```
Modification of punctuation only.
{ 
  "id": "structural-00010",
  "op": "PUNCTUATION", 
  "old": "done; therefore",
  "new": "done. Therefore",
  "by": "Fabio Vitali",
  "timestamp": "2018-03-10T07:25:23.891Z", 
  "items": [{ 
        "id" : "edit-00048",
        "op":"DEL", 
        "pos": 123, 
        "content": "; t" 
  },{ 
        "id" : "edit-00049",
        "op":"INS", 
        "pos": 123, 
        "content": ". T" 
  }]
}
```

### 3.1.2 Wordchange

```
Change of a single word without changing the overall meaning (change or a spell fix). All inserts/replace are within a single word.
{ 
  "id": "structural-00011",
  "op": "WORDCHANGE", 
  "old": "giuoco",
  "new": "gioco",
  "by": "Fabio Vitali",
  "timestamp": "2018-03-10T07:25:23.891Z", 
  "items": [{ 
        "id" : "edit-00050",
        "op":"DEL", 
        "pos": 123, 
        "content": "u" 
  }]
}
```
```
{ 
  "id": "structural-00011",
  "op": "WORDCHANGE", 
  "old": "giuoco",
  "new": "gioco",
  "by": "Fabio Vitali",
  "timestamp": "2018-03-10T07:25:23.891Z", 
  "items": [{ 
        "id" : "edit-00050",
        "op":"DEL", 
        "pos": 121, 
        "content": "giuoco" 
  },{ 
        "id" : "edit-00052",
        "op":"INS", 
        "pos": 121, 
        "content": "gioco" 
  }]
}
```
```
{ 
  "id": "structural-00012",
  "op": "WORDCHANGE", 
  "old": "anlyze",
  "new": "analyse",
  "by": "Fabio Vitali",
  "timestamp": "2018-03-10T07:25:23.891Z", 
  "items": [{ 
        "id" : "edit-00051",
        "op":"INS", 
        "pos": 161, 
        "content": "a" 
  },{ 
        "id" : "edit-00052",
        "op":"DEL", 
        "pos": 164, 
        "content": "z" 
  },{ 
        "id" : "edit-00053",
        "op":"INS", 
        "pos": 164, 
        "content": "s" 
  }]
}
```
```
{ 
  "id": "structural-00012",
  "op": "WORDCHANGE", 
  "old": "anlyze",
  "new": "analyse",
  "by": "Fabio Vitali",
  "timestamp": "2018-03-10T07:25:23.891Z", 
  "items": [{ 
        "id" : "edit-00051",
        "op":"DEL", 
        "pos": 159, 
        "content": "anlyze" 
  },{ 
        "id" : "edit-00052",
        "op":"INS", 
        "pos": 159, 
        "content": "analyse" 
  }]
}
```
### 2.1.3 Wordreplace

```
{ 
  "id": "structural-00013",
  "op": "WORDREPLACE", 
  "old": "exclaimed",
  "new": "said",
  "by": "Fabio Vitali",
  "timestamp": "2018-03-10T07:25:23.891Z", 
  "items": [{ 
        "id" : "edit-00054",
        "op":"DEL", 
        "pos": 123, 
        "content": "exclaimed" 
  },{ 
        "id" : "edit-00051",
        "op":"DEL", 
        "pos": 123, 
        "content": "said" 
  }]
}
```
```
{ 
  "id": "structural-00014",
  "op": "WORDREPLACE", 
  "old": "a word",
  "new": "some words",
  "by": "Fabio Vitali",
  "timestamp": "2018-03-10T07:25:23.891Z", 
  "items": [{ 
        "id" : "edit-00055",
        "op":"DEL", 
        "pos": 152, 
        "content": "a" 
  },{ 
        "id" : "edit-00056",
        "op":"INS", 
        "pos": 152, 
        "content": "some" 
  },{ 
        "id" : "edit-00057",
        "op":"INS", 
        "pos": 161, 
        "content": "s" 
  }]
}
```
```
{ 
  "id": "structural-00014",
  "op": "WORDREPLACE", 
  "old": "a word",
  "new": "some words",
  "by": "Fabio Vitali",
  "timestamp": "2018-03-10T07:25:23.891Z", 
  "items": [{ 
        "id" : "edit-00055",
        "op":"DEL", 
        "pos": 152, 
        "content": "a word" 
  },{ 
        "id" : "edit-00056",
        "op":"INS", 
        "pos": 152, 
        "content": "some words" 
  }]
}
```

### 2.1.4 Textinsert / Textdelete

```
Insert of a string made of more words (markup excluded)
{ 
  "id": "structural-00015",
  "op": "TEXTINSERT", 
  "old": "",
  "new": "neither more nor less",
  "by": "Fabio Vitali",
  "timestamp": "2018-03-10T07:25:23.891Z", 
  "items": [{ 
        "id" : "edit-00058",
        "op":"INS", 
        "pos": 175, 
        "content": "neither more nor less" 
  }]
}
```
```
delete of a string of more words (markup excluded)
{ 
  "id": "structural-00016",
  "op": "TEXTDELETE", 
  "old": "and ridiculous",
  "new": "",
  "by": "Fabio Vitali",
  "timestamp": "2018-03-10T07:25:23.891Z", 
  "items": [{ 
        "id" : "edit-00059",
        "op":"DEL", 
        "pos": 152, 
        "content": "and ridiculous " 
  }]
}
```
### 2.1.5. Textreplace
```
Replace of a string of more words (markup excluded)
{ 
  "id": "structural-10015",
  "op": "TEXTREPLACE", 
  "old": "exactly one item",
  "new": "one or more items",
  "by": "Fabio Vitali",
  "timestamp": "2018-03-10T07:25:23.891Z", 
  "items": [{ 
        "id" : "edit-10058",
        "op":"DEL", 
        "pos": 175, 
        "content": "exactly one item" 
  },{ 
        "id" : "edit-10059",
        "op":"INS", 
        "pos": 175, 
        "content": "one or more items" 
  }]
}
```


