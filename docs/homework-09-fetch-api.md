# 📓 Journal API

This is a simple API to save and manage journals. Your task is to learn how to use `fetch()` to talk to this API.

---

## 📚 What is an API?

Think of an API like a waiter in a restaurant:
- You (the customer) ask the waiter for food
- The waiter goes to the kitchen and brings your food back
- The API works the same way - you ask for data, and it brings it back!

---

## 🔧 Before You Start

The domain name that will be used is: `https://ddd05aafa0b5.ngrok-free.app`

---

## 📖 Learn About `fetch()` First

Before doing the exercises, you need to understand `fetch()`. 

**Learn from these resources:**
- 📺 [JavaScript Fetch API - YouTube (Web Dev Simplified)](https://www.youtube.com/watch?v=cuEtnrL9-H0)
- 📖 [MDN Web Docs - Using Fetch](https://developer.mozilla.org/en-US/docs/Web/API/Fetch_API/Using_Fetch)
- 📖 [JavaScript.info - Fetch](https://javascript.info/fetch)

---

## 🎯 API Endpoints

| Action | Method | URL | What it does |
|--------|--------|-----|--------------|
| Create | POST | `/journal` | Add a new journal |
| Read All | GET | `/journal` | Get all journals |
| Read One | GET | `/journal/:id` | Get one journal by ID |
| Update | PUT | `/journal/:id` | Change a journal |
| Delete | DELETE | `/journal/:id` | Remove a journal |

---

## 📦 Data Shape

### What is a Journal?

A journal is an object with these properties:

```json
{
  "id": "string (required, must be unique)",
  "total": "number (total amount)",
  "entries": [
    {
      "no": "number (entry number)",
      "account": "string (account code)",
      "debit": "number (amount)",
      "credit": "number (amount)",
      "date": "string (YYYY-MM-DD)"
    }
  ]
}
```

**Example:**
```json
{
  "id": "3aebdcf0-100f-4ee3-b350-2c0ff2aa7d5b",
  "total": 420,
  "entries": [
    {
      "no": 1,
      "account": "3150",
      "debit": 420,
      "credit": 0,
      "date": "2025-11-03"
    },
    {
      "no": 2,
      "account": "5400",
      "debit": 0,
      "credit": 420,
      "date": "2025-11-03"
    }
  ]
}
```
**Remember:** In accounting, total debit must equal total credit!
---

## 📝 Tasks

### Task 1: Get All Journals

**Your Task:** Write code to get all journals from the API

**Endpoint:** `GET /journal`

**What you will receive:** An array of journal objects
```json
[
  { "id": "...", "total": ..., "entries": [...] },
  { "id": "...", "total": ..., "entries": [...] }
]
```

**💡 Hints:**
- GET is the default method in fetch
- You only need the URL
- Don't forget to convert the response to JSON

---

### Task 2: Create a New Journal

**Your Task:** Write code to create a new journal

**Endpoint:** `POST /journal`

**What you need to send:** A journal object with `id`, `total`, and `entries`
```json
{
  "id": "your-unique-id",
  "total": ...,
  "entries": [
    { "no": 1, "account": "...", "debit": ..., "credit": ..., "date": "..." },
    { "no": 2, "account": "...", "debit": ..., "credit": ..., "date": "..." }
  ]
}
```

**What you will receive:** The created journal object

**💡 Hints:**
- You need to specify `method: 'POST'`
- You need to tell the API you're sending JSON (think about headers)
- You need to convert your object to a string before sending
- Look up: `JSON.stringify()`

---

### Task 3: Get One Journal by ID

**Your Task:** Write code to get a specific journal using its ID

**Endpoint:** `GET /journal/:id`

(Replace `:id` with the actual ID, like `/journal/1`)

**What you will receive:** One journal object
```json
{
  "id": "...",
  "total": ...,
  "entries": [
    { "no": 1, "account": "...", "debit": ..., "credit": ..., "date": "..." }
  ]
}
```

**💡 Hints:**
- The ID goes in the URL, not in the body
- Use template strings to build the URL: `` `http://.../${variable}` ``
- What happens if the ID doesn't exist? Check `response.ok`

---

### Task 4: Update a Journal

**Your Task:** Write code to update an existing journal

**Endpoint:** `PUT /journal/:id`

**What you need to send:** The updated data
```json
{
 "total": ...,
  "entries": [
    { "no": 1, "account": "...", "debit": ..., "credit": ..., "date": "..." },
    { "no": 2, "account": "...", "debit": ..., "credit": ..., "date": "..." }
  ]
}
```

**What you will receive:** The updated journal object

**💡 Hints:**
- Similar to POST, but use `method: 'PUT'`
- The ID goes in the URL
- The new data goes in the body
- The journal must exist first!

---

### Task 5: Delete a Journal

**Your Task:** Write code to delete a journal

**Endpoint:** `DELETE /journal/:id`

**What you will receive:** The deleted journal object

**💡 Hints:**
- Use `method: 'DELETE'`
- You only need the URL with the ID
- No body is needed
- Be careful! Deleted data is gone forever!

---

## 📋 Quick Reference

| HTTP Method | When to Use | Need Body? | Need Headers? |
|-------------|-------------|------------|---------------|
| GET | Read data | ❌ No | ❌ No |
| POST | Create data | ✅ Yes | ✅ Yes |
| PUT | Update data | ✅ Yes | ✅ Yes |
| DELETE | Delete data | ❌ No | ❌ No |

---

## ❓ Error Codes You Might See

| Code | What it Means |
|------|---------------|
| 200 | Success! Everything is OK |
| 201 | Created! New data was saved |
| 400 | Bad request - something is missing |
| 404 | Not found - the ID doesn't exist |
| 409 | Conflict - this ID is already used |
| 500 | Server error - check if server is running |

---

## 🏆 Challenge Yourself

After you finish the basic exercises:

1. **Create 3 journals** with different IDs
2. **Get all journals** and display them nicely
3. **Update one** of them
4. **Delete one** of them
5. **Build a function** that does all of these in order

---

## 📚 More Learning Resources

**Understanding Fetch:**
- [MDN - Fetch API](https://developer.mozilla.org/en-US/docs/Web/API/Fetch_API)
- [freeCodeCamp - Fetch Tutorial](https://www.freecodecamp.org/news/how-to-make-api-calls-with-fetch/)

**Understanding JSON:**
- [MDN - Working with JSON](https://developer.mozilla.org/en-US/docs/Learn/JavaScript/Objects/JSON)
- [W3Schools - JSON](https://www.w3schools.com/js/js_json_intro.asp)

**Understanding async/await (advanced):**
- [JavaScript.info - Async/Await](https://javascript.info/async-await)

**Understanding HTTP Methods:**
- [MDN - HTTP Methods](https://developer.mozilla.org/en-US/docs/Web/HTTP/Methods)

---

## 💡 General Tips

1. **Open browser console** - Press F12 to see your logs and errors
2. **Start with GET** - It's the easiest, no body needed
3. **Read error messages** - They tell you what's wrong
4. **Test one thing at a time** - Don't write everything at once
5. **Use `console.log()`** - Print values to see what you have

---

## ✅ How to Know You Succeeded

- [ ] Task 1: You can see all journals in the console
- [ ] Task 2: New journal appears when you GET all journals
- [ ] Task 3: You can get one specific journal
- [ ] Task 4: Journal data changes after update
- [ ] Task 5: Journal is gone after delete

---

Good luck! 🚀

Remember: **Struggling is part of learning.** If you're stuck, read the resources, try different things, and don't give up!
