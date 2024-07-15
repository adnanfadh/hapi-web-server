# Note API Spec

## Data Structure

```json
{
 "id": "string",
 "title": "string",
 "createdAt": "string",
 "updatedAt": "string",
 "tags": "array of string",
 "body": "string",
}
```
Example : 

```json
{
 "id": "notes-V1StGXR8_Z5jdHi6B-myT",
 "title": "Sejarah JavaScript",
 "createdAt": "2020-12-23T23:00:09.686Z",
 "updatedAt": "2020-12-23T23:00:09.686Z",
 "tags": ["NodeJS", "JavaScript"],
 "body": "JavaScript pertama kali dikembangkan oleh Brendan Eich dari Netscape di bawah nama Mocha, yang nantinya namanya diganti menjadi LiveScript, dan akhirnya menjadi JavaScript. Navigator sebelumnya telah mendukung Java untuk lebih bisa dimanfaatkan para pemrogram yang non-Java.",
},
```
## Create Note

Endpoint : POST /notes

Request Body :

```json
{
 "title": "Judul Catatan",
 "tags": ["Tag 1", "Tag 2"],
 "body": "Konten catatan"
}
```

Response Body (Success) :

```json
{
  "status": "success",
  "message": "Catatan berhasil ditambahkan",
  "data": {
    "noteId": "V09YExygSUYogwWJ"
  }
}
```

Response Body (Failed) : 
```json
{
  "status": "error",
  "message": "Catatan gagal untuk ditambahkan"
}
```

## List Note

Endpoint : Get /notes

Response Body (Success) :

```json
{
  "status": "success",
  "data": {
    "notes": [
      {
        "id":"notes-V1StGXR8_Z5jdHi6B-myT",
        "title":"Catatan 1",
        "createdAt":"2020-12-23T23:00:09.686Z",
        "updatedAt":"2020-12-23T23:00:09.686Z",
        "tags":[
          "Tag 1",
          "Tag 2"
        ],
        "body":"Isi dari catatan 1"
      },
      {
        "id":"notes-V1StGXR8_98apmLk3mm1",
        "title":"Catatan 2",
        "createdAt":"2020-12-23T23:00:09.686Z",
        "updatedAt":"2020-12-23T23:00:09.686Z",
        "tags":[
          "Tag 1",
          "Tag 2"
        ],
        "body":"Isi dari catatan 2"
      }
    ]
  }
}
```

Response Body (Failed) : 
```json
{
  "status": "success",
  "data": {
    "notes": []
  }
}
```

## Get Note

Endpoint : Get /notes/{id}


Response Body (Success) :

```json
{
  "status": "success",
  "data": {
    "note": {
      "id":"notes-V1StGXR8_Z5jdHi6B-myT",
      "title":"Catatan 1",
      "createdAt":"2020-12-23T23:00:09.686Z",
      "updatedAt":"2020-12-23T23:00:09.686Z",
      "tags":[
        "Tag 1",
        "Tag 2"
      ],
      "body":"Isi dari catatan 1"
    }
  }
}
```

Response Body (Failed) : 
```json
{
  "status": "fail",
  "message": "Catatan tidak ditemukan"
}
```

## Update Note

Endpoint : PUT /notes{id}

Request Body :

```json
{
  "title":"Judul Catatan Revisi",
  "tags":[
    "Tag 1",
    "Tag 2"
  ],
  "body":"Konten catatan"
}
```

Response Body (Success) :

```json
{
  "status": "success",
  "message": "Catatan berhasil diperbaharui"
}
```

Response Body (Failed) : 
```json
{
  "status": "fail",
  "message": "Gagal memperbarui catatan. Id catatan tidak ditemukan"
}
```

## Update Note

Endpoint : DELETE /notes{id}

Response Body (Success) :

```json
{
  "status": "success",
  "message": "Catatan berhasil dihapus"
}
```

Response Body (Failed) : 
```json
{
  "status": "fail",
  "message": "Catatan gagal dihapus. Id catatan tidak ditemukan"
}
```
