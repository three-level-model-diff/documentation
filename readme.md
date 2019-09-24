# Table of content

* [Mechanic operations](https://github.com/three-level-model-diff/documentation#1-mechanical-operations)
* [Structural operations](https://github.com/three-level-model-diff/documentation#2-structural-operations)
* [Semantic operations]()

# 1. Mechanical operations
There are only two mechanical operations: INS and DEL. 
Mechanical operations act EXCLUSIVELY at string level: markup operations are still expressed as INS and DEL.

## 1.1 Insertion (INS)

Insertion of a string of characters (markup included)

```
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

Removal of a string of characters (markup included)
```
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

Modification of punctuation only.

```
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

Change of a single word without changing the overall meaning (change or a spell fix). All inserts/replace are within a single word.

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

Substitution of an entire single word.

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

Insert of a string made of more words (markup excluded)

```
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
delete of a string of more words (markup excluded)
```
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
Replace of a string of more words (markup excluded)
```
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

## 2.2. Markup operations

The markup operations are operations over more various markup nodes. Sometimes only the markup is modified, or even the text close to the markup. Each operations has been paired with the inverse.

### 2.2.1. NOOP

In the markup languages syntax NOOPs are mechanical modification without any real effect. For instance changes in attribute orders or adding/removing whitespaces in a text node. 

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
Insert of one or more nodes in the document (eventually also text before/after nodes)
```
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
Delete of one or more nodes in the document (eventually also text before/after nodes)
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
Move of one or more nodes from a place to another within the document. The operations MUST NOT be close in time. It is a move onlt if the DEL and the INS content are equal but the position are different.

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

Nesting of one or more nodes with another one. The content does not change, but it changes of a single level

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
Delete of a single node with promotion of its content at the same level of the removed node. The content does not change, it goes up of a level.
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

The union of two same-type sibling nodes. The joint node take the characteristics of the first of the two nodes. The one of the second node are lost.

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

The separation of a node into two same-type sibling nodes. Both nodes take the caracteristics of the joint node.
```
{ 
  "id": "structural-00018",
  "op": "SPLIT", 
  "old": "First[...]paragraph.",
  "by": "Fabio Vitali",
  "timestamp": "2018-03-10T07:25:23.891Z", 
  "items": [{ 
        "id" : "edit-00073",
        "op":"INS", 
        "pos": 512, 
        "content": "</p><p>" 
  }]
}
```
### 2.2.6. Replace

The substitution of a node with another one without changing the content. Where appropriate the attributes of the old node are preserved. The position and the node MUST be the same.

```
{ 
  "id": "structural-00030",
  "op": "REPLACE", 
  "old": "<li>The content of this list item</li>",
  "by": "Fabio Vitali",
  "timestamp": "2018-03-10T07:25:23.891Z", 
  "items": [{ 
        "id" : "edit-00076",
        "op":"DEL", 
        "pos": 623, 
        "content": "<li>" 
  },{ 
        "id" : "edit-00077",
        "op":"DEL", 
        "pos": 645, 
        "content": "</li>" 
  },{ 
        "id" : "edit-00078",
        "op":"INS", 
        "pos": 623, 
        "content": "<p>" 
  },{ 
        "id" : "edit-00079",
        "op":"INS", 
        "pos": 645, 
        "content": "</p>" 
  }]
}
```

# 3. Semantic operations

Semantic operations are all the (sequences of) operations in which it is easy to give an immediate and comprehensible meaning for a human beings. The distinction is intuitive, intrinsecally imprecise. So, it subjective to interpretations. Moreover, it is not that simply to determine a definitive and precise list of useable categories.

The majority of structural operations have a simple meaning, so it is meaningless to group them in overstructures. For this reason, the semantic characterization will be used only few times for grouping.

## 3.1. Colorazione semantica di operazioni strutturali

### 3.1.1. Fix

The Fixes are a group structural operations that solve an error. It can be either a typo, structural, or conceptual.

```
{
  "id": "semantic-00001",
  "op": "FIX",
  "new": "Some words are better than others",
  "old": "Some words is better than others",
  "items": { 
    "id": "structural-00033",
    "op": "WORDREPLACE",
    "by": "Fabio Vitali",
    "timestamp": "2018-10-10T07:25:23.891Z", 
    "items": [{ 
      "id" : "edit-00083",
      "op":"DEL", 
      "pos": 215, 
      "content": "is" 
    },{ 
      "id" : "edit-00084",
      "op":"INS", 
      "pos": 215, 
      "content": "are" 
    }]
  }
}
```
```
{
  "id": "semantic-00002",
  "op": "FIX",
  "new": "<p>The content of this list item</p>",
  "old": "<li>The content of this list item</li>",
  "items": { 
    "id": "structural-00034",
    "op": "REPLACE", 
    "by": "Fabio Vitali",
    "timestamp": "2018-03-10T07:25:23.891Z", 
    "items": [{ 
      "id" : "edit-00085",
      "op":"DEL", 
      "pos": 623, 
      "content": "<li>" 
    },{ 
      "id" : "edit-00086",
      "op":"DEL", 
      "pos": 645, 
      "content": "</li>" 
    },{ 
      "id" : "edit-00087",
      "op":"INS", 
      "pos": 623, 
      "content": "<p>" 
    },{ 
      "id" : "edit-00088",
      "op":"INS", 
      "pos": 645, 
      "content": "</p>" 
    }]
  }
}
```

### 3.1.2. Style

Style modifications are stylistic changes in aspect and/or content withotu changing the meaning. It can be a change in markup, or the substitution of a word with a synonym.

```
{
  "id": "semantic-00003",
  "op": "STYLE",
  "new": "<b>some text</b>",
  "old": "some text",
  "items":{ 
    "id": "structural-00024",
    "op": "WRAP", 
    "by": "Fabio Vitali",
    "timestamp": "2018-10-10T07:26:23.891Z", 
    "items": [{
        "id" : "edit-00089",
        "op":"INS", 
        "pos": 235, 
        "content": "<b>" 
    },{ 
        "id" : "edit-00090",
        "op":"INS", 
        "pos": 255, 
        "content": "</b>" 
    }]
  }
}
```

```
{
  "id": "semantic-00005",
  "op": "STYLE",
  "new": "John, Jack, and Bob",
  "old": "John, Jack and Bob",
  "items": { 
    "id": "structural-00026",
    "op": "PUNCTUATION", 
    "by": "Fabio Vitali",
    "timestamp": "2018-03-10T07:28:28.891Z", 
    "items": [{ 
      "id" : "edit-00093",
      "op":"INS", 
      "pos": 623, 
      "content": "," 
    }]
  }
}
```

### 3.1.3. Meaning

This category is reserved to the only operations that change concretely the meaning of the text, such as "Today is a good day" and "Today is not a good day".

```
{
  "id": "semantic-00006",
  "op": "MEANING",
  "new": "Oggi non è una bella giornata",
  "old": "Oggi è una bella giornata",
  "items":{ 
    "id": "structural-00027",
    "op": "TEXTINSERT", 
    "by": "Fabio Vitali",
    "timestamp": "2018-10-10T07:31:23.891Z", 
    "items": [{
        "id" : "edit-00094",
        "op":"INS", 
        "pos": 312, 
        "content": "non " 
    }]
  }
}
```

