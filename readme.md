# Table of content

[Mechanic operations](https://github.com/three-level-model-diff/documentation#1-mechanical-operations)
[Structural operations](https://github.com/three-level-model-diff/documentation#2-structural-operations)
[Semantic operations]()

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

The operation at structural level are sequence of one or more mechanical operations.

## 2.1 Operations on text

Operation on text are within the same markup node. 

### 2.1.1. Punctuation

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

### 2.1.2 Wordchange

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

## 2.2. Operazioni sul markup

### 2.2.1. NOOP

```
Non-relevant change within markup 
{ 
  "id": "structural-10017",
  "op": "NOOP",
  "by": "Fabio Vitali",
  "timestamp": "2018-03-10T07:25:23.891Z", 
  "items": [{ 
        "id" : "edit-10060",
        "op":"DEL", 
        "pos": 215, 
        "content": "<p id='x45' class='test'>" 
  },{ 
        "id" : "edit-00060",
        "op":"INS", 
        "pos": 215, 
        "content": "<p class='test' id='x45'>"  
  }]
}
```
```
Non-relevant change within text 
{ 
  "id": "structural-10018",
  "op": "NOOP", 
  "by": "Fabio Vitali",
  "timestamp": "2018-03-10T07:25:23.891Z", 
  "items": [{ 
        "id" : "edit-10061",
        "op":"INS", 
        "pos": 255, 
        "content": "\n   " 
  }]
}
```

### 2.2.2. Insert / Delete

```
Insert of one or more nodes in the document (eventually also text before/after nodes)
{ 
  "id": "structural-00017",
  "op": "INSERT",
  "new": "Some text [...] more text",
  "by": "Fabio Vitali",
  "timestamp": "2018-03-10T07:25:23.891Z", 
  "items": [{ 
        "id" : "edit-00060",
        "op":"INS", 
        "pos": 215, 
        "content": "<p>Some text</p><p>Some more text</p>" 
  }]
}
```
```
{ 
  "id": "structural-00019",
  "op": "INSERT", 
  "new": "for instance [...] all are new.",
  "by": "Fabio Vitali",
  "timestamp": "2018-03-10T07:25:23.891Z", 
  "items": [{ 
        "id" : "edit-00062",
        "op":"INS", 
        "pos": 275, 
        "content": "for instance: </p><p>Some text</p><p>Some more text</p><p>These all are new." 
  }]
}
```
```

Eliminazione di uno o più nodi nel documento, più, eventualmente, del testo prima e/o dopo ai nodi
{ 
  "id": "structural-00018",
  "op": "DELETE", 
  "old": "Some text [...] I don't like",
  "by": "Fabio Vitali",
  "timestamp": "2018-03-10T07:25:23.891Z", 
  "items": [{ 
        "id" : "edit-00061",
        "op":"DEL", 
        "pos": 255, 
        "content": "<p>Some text to throw away</p><p>Some more text I don't like</p>" 
  }]
}
```
```
{ 
  "id": "structural-00020",
  "op": "DELETE", 
  "old": "for instance: [...] must go.",
  "by": "Fabio Vitali",
  "timestamp": "2018-03-10T07:25:23.891Z", 
  "items": [{ 
        "id" : "edit-00063",
        "op":"DEL", 
        "pos": 307, 
        "content": "for instance: </p><p>Some text</p><p>Some more text</p><p>These all must go." 
  }]
}
```
### 2.2.3. Move

```
{ 
  "id": "structural-00021",
  "op": "MOVE", 
  "old": "Some text that goes away",
  "by": "Fabio Vitali",
  "timestamp": "2018-03-10T07:25:23.891Z", 
  "items": [{ 
        "id" : "edit-00064",
        "op":"DEL", 
        "pos": 215, 
        "content": "<p>Some text that goes away</p>" 
  },{ 
        "id" : "edit-00065",
        "op":"INS", 
        "pos": 247, 
        "content": "<p>Some text that goes away</p>" 
  }]
}
```

### 2.2.4. Wrap / Unwrap

```
{ 
  "id": "structural-00022",
  "op": "WRAP", 
  "old": "the content of the node",
  "by": "Fabio Vitali",
  "timestamp": "2018-03-10T07:25:23.891Z", 
  "items": [{ 
        "id" : "edit-00065",
        "op":"INS", 
        "pos": 535, 
        "content": "<i>" 
  },{ 
        "id" : "edit-00066",
        "op":"INS", 
        "pos": 540, 
        "content": "</i>" 
  }]
}
```
```
{ 
  "id": "structural-00023",
  "op": "UNWRAP", 
  "old": "<i>the content of the node</i>",
  "by": "Fabio Vitali",
  "timestamp": "2018-03-10T07:25:23.891Z", 
  "items": [{ 
        "id" : "edit-00067",
        "op":"DEL", 
        "pos": 535, 
        "content": "<i>" 
  },{ 
        "id" : "edit-00068",
        "op":"DEL", 
        "pos": 540, 
        "content": "</i>" 
  }]
}
```

### 2.2.5. Join / Split

```
{ 
  "id": "structural-00026",
  "op": "JOIN", 
  "old": "First[...]paragraph.",
  "by": "Fabio Vitali",
  "timestamp": "2018-03-10T07:25:23.891Z", 
  "items": [{ 
        "id" : "edit-00072",
        "op":"DEL", 
        "pos": 512, 
        "content": "</p><p>" 
  }]
}
```

### 2.2.6. Replace
