# Bookshelf API

Project ini dikembangkan untuk memenuhi Submission [Kelas Belajar Membuat Aplikasi Back-End untuk Pemula](https://www.dicoding.com/academies/261/) dari Dicoding. Project ini dibangun menggunakan Hapi Framework.

Pengujian Bookshelf API menggunakan berkas Postman Collection dan Environment yang telah disediakan oleh Dicoding. Berkas tersebut tersedia pada branch `api-docs` dalam direktori [BookshelfAPITestCollectionAndEnvironment](./BookshelfAPITestCollectionAndEnvironment).

## Add A Book

**HTTP Request**  `POST`  `/books`

**Request Body**
```json
{
  "name": "Judul Buku",
  "year": 2022,
  "author": "Nama Penulis",
  "summary": "Rangkuman",
  "publisher": "Nama Penerbit",
  "pageCount": 200,
  "readPage": 100,
  "reading": true
}
```

**Response**

<details>
  <summary>HTTP/1.1 201 Created</summary>

```json
{
  "status": "success",
  "message": "Buku berhasil ditambahkan",
  "data": {
    "bookId": "V09YExygSUYogwWJ"
  }
}
```

</details>

**Error Response**


<details>
  <summary>HTTP/1.1 400 Bad Request </summary>
  
```json
{
  "status": "fail",
  "message": "Gagal menambahkan buku. Mohon isi nama buku"
}
```
</details>


<details>
  <summary>HTTP/1.1 400 Bad Request</summary>
  
```json
{
  "status": "fail",
  "message": "Gagal menambahkan buku. readPage tidak boleh lebih besar dari pageCount"
}
```
</details>

<details>
  <summary>HTTP/1.1 500 Internal Server Error</summary>
  
```json
{
  "status": "error",
  "message": "Buku gagal ditambahkan"
}
```
</details>

## Get All Books

**HTTP Request**  `GET`  `/books`

**Query Parameter**
|Parameter|Description                  |
|---------|-----------------------------|
|name     |Search term for book's title |
|reading  |Value 0 or 1                 |
|finished |Value 0 or 1                 |

**Response**

<details>
  <summary>HTTP/1.1 200 OK</summary>

```json
{
  "status": "success",
  "data": {
    "books": [
      {
        "id": "V09YExygSUYogwWJ",
        "name": "Buku A",
        "publisher": "Nama Penerbit"
      },
      {
        "id": "V09YExygSUYogwYZ",
        "name": "Buku B",
        "publisher": "Nama Penerbit"
      }
    ]
  }
}
```
</details>

<details>
  <summary>HTTP/1.1 200 OK</summary>
  
```json
{
  "status": "success",
  "data": {
    "books": []
  }
}
```
</details>

## Get A Spesific Book

**HTTP Request**  `GET`  `/books/{id}`

**URL Parameter**

|Parameter  | Description                      |
|-----------|----------------------------------|
|id         | The `id` of the book to retrieve |

**Response**

<details>
  <summary>HTTP/1.1 200 OK</summary>
  
```json
{
  "status": "success",
  "data": {
    "note": {
      "id": "V09YExygSUYogwWJ",
      "name": "Judul Buku",
      "year": 2022,
      "author": "Nama Penulis",
      "summary": "Rangkuman",
      "publisher": "Nama Penerbit",
      "pageCount": 200,
      "readPage": 100,
      "reading": true,
      "finished": false,
      "insertedAt": "2020-12-23T23:00:00.686Z",
      "updatedAt": "2020-12-23T23:00:00.686Z"
    }
  }
}
```
</details>

**Error Response**

<details>
  <summary>HTTP/1.1 404 Not Found</summary>
  
```json
{
  "status": "fail",
  "message": "Buku tidak ditemukan"
}
```
</details>

## Update Book

**HTTP Request**  `PUT` `/books/{id}`

**URL Parameter**

|Parameter  | Description                    |
|-----------|--------------------------------|
|id         | The `id` of the book to update |

**Request Body**
```json
{
  "name": "Judul Buku",
  "year": 2022,
  "author": "Nama Penulis",
  "summary": "Rangkuman",
  "publisher": "Nama Penerbit",
  "pageCount": 200,
  "readPage": 100,
  "reading": true
}
```

**Response**

<details>
  <summary>HTTP/1.1 200 OK</summary>
  
```json
{
  "status": "success",
  "message": "Buku berhasil diperbarui"
}
```
</details>

**Error Response**


<details>
  <summary>HTTP/1.1 400 Bad Request </summary>
  
```json
{
  "status": "fail",
  "message": "Gagal memperbarui buku. Mohon isi nama buku"
}
```
</details>


<details>
  <summary>HTTP/1.1 400 Bad Request</summary>
  
```json
{
  "status": "fail",
  "message": "Gagal memperbarui buku. readPage tidak boleh lebih besar dari pageCount"
}
```
</details>

<details>
  <summary>HTTP/1.1 404 Not Found</summary>
  
```json
{
  "status": "fail",
  "message": "Gagal memperbarui buku. Id tidak ditemukan"
}
```
</details>

## Delete Book

**HTTP Request**  `DELETE` `/books/{id}`

**URL Parameter**

|Parameter  | Description                    |
|-----------|--------------------------------|
|id         | The `id` of the book to delete |

**Response**

<details>
  <summary>HTTP/1.1 200 OK</summary>
  
```json
{
  "status": "success",
  "message": "Buku berhasil dihapus"
}
```
</details>

**Error Response**

<details>
  <summary>HTTP/1.1 404 Not Found</summary>
  
```json
{
  "status": "fail",
  "message": "Buku gagal dihapus. Id tidak ditemukan"
}
```
</details>
