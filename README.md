<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>My Bucket List</title>
  <!-- Font Awesome for icons -->
  <link
    rel="stylesheet"
    href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0-beta3/css/all.min.css"
    integrity="sha512-Fo3rlrZj/k7ujTTXRNK1Q2g1GxHzy+5WJe9v6D6q1zYFJ8n/9hox6s3T+2qbfvQHs2Qxoj3BYVj8G6+T9l9TtQ=="
    crossorigin="anonymous"
    referrerpolicy="no-referrer"
  />
  <style>
    /* Global Styles */
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
    }
    body {
      font-family: 'Arial', sans-serif;
      background: #f0f0f0;
      padding: 20px;
      color: #333;
    }
    h1 {
      text-align: center;
      margin-bottom: 20px;
      color: #ff6f61;
    }
    .bucket-list-container {
      max-width: 800px;
      margin: 0 auto;
      background: #fff;
      border-radius: 8px;
      box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
      padding: 20px;
    }
    /* Input form styling */
    .add-item-form {
      display: flex;
      margin-bottom: 20px;
    }
    .add-item-form input[type="text"] {
      flex: 1;
      padding: 10px;
      border: 2px solid #ddd;
      border-radius: 4px;
      font-size: 1em;
    }
    .add-item-form button {
      padding: 10px 20px;
      margin-left: 10px;
      background: #ff6f61;
      color: #fff;
      border: none;
      border-radius: 4px;
      font-size: 1em;
      cursor: pointer;
      transition: background 0.3s ease;
    }
    .add-item-form button:hover {
      background: #e65b50;
    }
    /* Bucket list styling */
    ul {
      list-style: none;
    }
    li {
      display: flex;
      align-items: center;
      padding: 12px;
      border-bottom: 1px solid #e0e0e0;
      transition: background 0.3s ease;
    }
    li:last-child {
      border-bottom: none;
    }
    li:hover {
      background: #f9f9f9;
    }
    li i {
      margin-right: 15px;
      font-size: 1.5em;
    }
    /* Completed tasks styling */
    .completed i {
      color: #28a745; /* Green check */
    }
    .completed span {
      text-decoration: line-through;
      color: #888;
    }
    /* Pending tasks styling */
    .pending i {
      color: #ffc107; /* Golden star */
    }

    /* Media Queries */

    /* For tablets and small desktops */
    @media (max-width: 768px) {
      .bucket-list-container {
        padding: 15px;
      }
      h1 {
        font-size: 1.8em;
      }
      .add-item-form input[type="text"] {
        font-size: 0.95em;
      }
      .add-item-form button {
        font-size: 0.95em;
      }
      li {
        padding: 10px;
      }
      li i {
        font-size: 1.3em;
        margin-right: 10px;
      }
    }

    /* For mobile devices */
    @media (max-width: 600px) {
      .add-item-form {
        flex-direction: column;
      }
      .add-item-form input[type="text"] {
        margin-bottom: 10px;
      }
      .add-item-form button {
        margin-left: 0;
      }
      li {
        flex-direction: column;
        align-items: flex-start;
      }
      li i {
        margin-bottom: 5px;
      }
    }
  </style>
</head>
<body>
  <div class="bucket-list-container">
    <h1>My Bucket List</h1>
    <!-- Input Form to Add New Bucket List Items -->
    <form class="add-item-form" id="bucketForm">
      <input
        type="text"
        id="bucketInput"
        placeholder="Add a new bucket list item..."
        required
      />
      <button type="submit">Add Item</button>
    </form>
    <!-- Bucket List -->
    <ul id="bucketList">
      <!-- Existing Bucket List Items -->
      <li class="completed">
        <i class="fas fa-check-circle"></i>
        <span>Go Skydiving</span>
      </li>
      <li class="pending">
        <i class="fas fa-star"></i>
        <span>Travel to Japan</span>
      </li>
      <li class="pending">
        <i class="fas fa-star"></i>
        <span>Write a Book</span>
      </li>
      <li class="completed">
        <i class="fas fa-check-circle"></i>
        <span>Learn to Play Guitar</span>
      </li>
      <li class="pending">
        <i class="fas fa-star"></i>
        <span>Volunteer Abroad</span>
      </li>
      <li class="pending">
        <i class="fas fa-star"></i>
        <span>Run a Marathon</span>
      </li>
    </ul>
  </div>

  <script>
    // Listen for form submission to add a new bucket list item
    document.getElementById('bucketForm').addEventListener('submit', function(e) {
      e.preventDefault(); // Prevent the form from submitting and refreshing the page
      
      const input = document.getElementById('bucketInput');
      const newItemText = input.value.trim();

      if (newItemText !== "") {
        // Create new list item
        const li = document.createElement('li');
        li.classList.add('pending'); // new items are pending by default

        // Create icon element
        const icon = document.createElement('i');
        icon.className = "fas fa-star"; // pending icon (golden star)

        // Create span element for text
        const span = document.createElement('span');
        span.textContent = newItemText;

        // Append icon and text to list item
        li.appendChild(icon);
        li.appendChild(span);

        // Append the new item to the bucket list
        document.getElementById('bucketList').appendChild(li);

        // Clear the input field
        input.value = "";
      }
    });
  </script>
</body>
</html>
