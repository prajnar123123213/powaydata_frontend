---
layout: tailwindd
title: Restaurant Explore 
search_exclude: true
permalink: /yelp/
---


<h1> Basic Restaurant Suggestions </h1>

<div>
  <ul>
    <li><a href="#restaurant-suggestions">Restaurant Suggestions</a></li>
    <li><a href="#post-section">Post What You Think!</a></li>
  </ul>
</div>

<p>Here are some of our favorite restaurant recommendations with interactive map views!</p>

<br>

<style>
    .restaurant-row {
        display: flex;
        justify-content: space-between;
        gap: 20px;
        padding: 20px;
    }

    .restaurant-item {
        width: 100%;
        text-align: center;
    }
      
    .restaurant-item iframe {
    width: 100%;
    height: 350px;
    border: 0;
    margin-bottom: 10px;
    }

    .restaurant-item h4 {
        font-size: 1.5em;
        font-weight: bold;
        color: #826b64;
    }
</style>

<br>

<div class="restaurant-row">
    <div class="restaurant-item">
        <h4>
          Born and Raised
        </h4>
        <iframe src="https://www.google.com/maps/embed?pb=!1m18!1m12!1m3!1d3356.546647161299!2d-117.17098792488046!3d32.72467248666027!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0x80d954b217aa2be3%3A0x188bc33bb9e0971!2sBorn%20and%20Raised!5e0!3m2!1sen!2sus!4v1736533938660!5m2!1sen!2sus" width="500" height="450" style="border:0;" allowfullscreen="" loading="lazy" referrerpolicy="no-referrer-when-downgrade"></iframe>
    </div>
    <div class="restaurant-item">
        <h4>
          Addison
        </h4>
        <iframe src="https://www.google.com/maps/embed?pb=!1m18!1m12!1m3!1d3348.35706065467!2d-117.20164512487125!3d32.94158117555873!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0x80dc07c1e6c857ad%3A0xd7c4bde7169b097c!2sADDISON!5e0!3m2!1sen!2sus!4v1736534254851!5m2!1sen!2sus" width="500" height="450" style="border:0;" allowfullscreen="" loading="lazy" referrerpolicy="no-referrer-when-downgrade"></iframe>
    </div>
</div>

<br>

<div class="restaurant-row">
    <div class="restaurant-item">
        <h4>
          Herb and Wood
        </h4>
        <iframe src="https://www.google.com/maps/embed?pb=!1m18!1m12!1m3!1d3356.446270357157!2d-117.17357932488038!3d32.72733878652402!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0x80d954b376b6f2db%3A0xfe5b4b34708c2dfb!2sHerb%20%26%20Wood!5e0!3m2!1sen!2sus!4v1736534411122!5m2!1sen!2sus" width="300" height="450" style="border:0;" allowfullscreen="" loading="lazy" referrerpolicy="no-referrer-when-downgrade"></iframe>
    </div>
    <div class="restaurant-item">
        <h4>
          Juniper and Ivy
        </h4>
        <iframe src="https://www.google.com/maps/embed?pb=!1m18!1m12!1m3!1d3356.441741314478!2d-117.17376312488034!3d32.72745908651807!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0x80d954b37ab64153%3A0x5bead8a029c74f5!2sJuniper%20and%20Ivy!5e0!3m2!1sen!2sus!4v1736534832854!5m2!1sen!2sus" width="300" height="450" style="border:0;" allowfullscreen="" loading="lazy" referrerpolicy="no-referrer-when-downgrade"></iframe>
    </div>
</div>

<br>


<script>
    const API_KEY = 'e956342f5c504b1685b5f81826a61c9b';
    const BASE_URL = 'https://api.spoonacular.com/food/menuItems/search';

    async function getRestaurant() {
      const foodType = document.getElementById("foodType").value;
      const url = `${BASE_URL}?apiKey=${API_KEY}&query=${encodeURIComponent(foodType)}&number=5`;
      const outputCard = document.getElementById("restaurantOutput");
      const outputBody = outputCard.querySelector(".card-body");

      try {
        const response = await fetch(url);
        if (!response.ok) {
          throw new Error(`Error: ${response.status} - ${response.statusText}`);
        }

        const data = await response.json();
        const restaurants = data.menuItems;

        if (restaurants.length === 0) {
          throw new Error('No restaurants found for the selected food type.');
        }

        const randomRestaurant = restaurants[Math.floor(Math.random() * restaurants.length)];

        outputBody.innerHTML = `
          <h5 class="card-title">Recommended ${foodType} Restaurant:</h5>
          <p class="card-text fw-bold">${randomRestaurant.title}</p>
          <img src="${randomRestaurant.image}" class="img-fluid rounded mt-3" alt="${randomRestaurant.title}">
        `;
        outputCard.classList.remove("d-none");
      } catch (error) {
        outputBody.innerHTML = `<p class="text-danger">${error.message}</p>`;
        outputCard.classList.remove("d-none");
      }
    }
</script>
<script src="https://cdn.jsdelivr.net/npm/bootstrap@5.3.3/dist/js/bootstrap.bundle.min.js"></script>

<br>

<h1> Post What You Think! </h1>
<div class="container">
    <div class="card shadow-sm">
        <div class="card-body">
            <h2>Select Group and Channel</h2>
            <form id="selectionForm">
                <div class="mb-3">
                    <label for="group_id" class="form-label">Group:</label>
                    <select id="group_id" name="group_id" class="form-select" required>
                        <option value="">Select a group</option>
                    </select>
                </div>
                <div class="mb-3">
                    <label for="channel_id" class="form-label">Channel:</label>
                    <select id="channel_id" name="channel_id" class="form-select" required>
                        <option value="">Select a channel</option>
                    </select>
                </div>
                <button type="submit" class="btn btn-primary">Select</button>
            </form>
        </div>
    </div>
</div>

<!-- Add New Post -->
<div class="container my-5">
    <div class="card shadow-sm">
        <div class="card-body">
            <h2>Add New Post</h2>
            <form id="postForm">
                <div class="mb-3">
                    <label for="title" class="form-label">Title:</label>
                    <input type="text" id="title" name="title" class="form-control" required>
                </div>
                <div class="mb-3">
                    <label for="comment" class="form-label">Comment:</label>
                    <textarea id="comment" name="comment" class="form-control" required></textarea>
                </div>
                <button type="submit" class="btn btn-success">Add Post</button>
            </form>
        </div>
    </div>
</div>
<script type="module">
    import { pythonURI, fetchOptions } from '{{ site.baseurl }}/assets/js/api/config.js';
    async function fetchGroups() {
        try {
            const response = await fetch(`${pythonURI}/api/groups/filter`, {
                ...fetchOptions,
                method: 'POST',
                headers: {
                    'Content-Type': 'application/json'
                },
                body: JSON.stringify({ section_name: "Home Page" })
            });
            if (!response.ok) {
                throw new Error('Failed to fetch groups: ' + response.statusText);
            }
            const groups = await response.json();
            const groupSelect = document.getElementById('group_id');
            groups.forEach(group => {
                const option = document.createElement('option');
                option.value = group.name;
                option.textContent = group.name;
                groupSelect.appendChild(option);
            });
        } catch (error) {
            console.error('Error fetching groups:', error);
        }
    }
    async function fetchChannels(groupName) {
        try {
            const response = await fetch(`${pythonURI}/api/channels/filter`, {
                ...fetchOptions,
                method: 'POST',
                headers: {
                    'Content-Type': 'application/json'
                },
                body: JSON.stringify({ group_name: groupName })
            });
            if (!response.ok) {
                throw new Error('Failed to fetch channels: ' + response.statusText);
            }
            const channels = await response.json();
            const channelSelect = document.getElementById('channel_id');
            channelSelect.innerHTML = '<option value="">Select a channel</option>';
            channels.forEach(channel => {
                const option = document.createElement('option');
                option.value = channel.id;
                option.textContent = channel.name;
                channelSelect.appendChild(option);
            });
        } catch (error) {
            console.error('Error fetching channels:', error);
        }
    }
    document.getElementById('group_id').addEventListener('change', function () {
        const groupName = this.value;
        if (groupName) {
            fetchChannels(groupName);
        } else {
            document.getElementById('channel_id').innerHTML = '<option value="">Select a channel</option>';
        }
    });
    document.getElementById('selectionForm').addEventListener('submit', function (event) {
        event.preventDefault();
        const groupId = document.getElementById('group_id').value;
        const channelId = document.getElementById('channel_id').value;
        if (groupId && channelId) {
            fetchData(channelId);
        } else {
            alert('Please select both group and channel.');
        }
    });
    document.getElementById('postForm').addEventListener('submit', async function (event) {
        event.preventDefault();
        const title = document.getElementById('title').value;
        const comment = document.getElementById('comment').value;
        const channelId = document.getElementById('channel_id').value;
        const postData = {
            title: title,
            comment: comment,
            channel_id: channelId
        };
        try {
            const response = await fetch(`${pythonURI}/api/post`, {
                ...fetchOptions,
                method: 'POST',
                headers: {
                    'Content-Type': 'application/json'
                },
                body: JSON.stringify(postData)
            });
            if (!response.ok) {
                throw new Error('Failed to add post: ' + response.statusText);
            }
            const result = await response.json();
            alert('Post added successfully!');
            document.getElementById('postForm').reset();
            fetchData(channelId);
        } catch (error) {
            console.error('Error adding post:', error);
            alert('Error adding post: ' + error.message);
        }
    });
    async function fetchData(channelId) {
        try {
            const response = await fetch(`${pythonURI}/api/posts/filter`, {
                ...fetchOptions,
                method: 'POST',
                headers: {
                    'Content-Type': 'application/json'
                },
                body: JSON.stringify({ channel_id: channelId })
            });
            if (!response.ok) {
                throw new Error('Failed to fetch posts: ' + response.statusText);
            }
            const postData = await response.json();
            const postCount = postData.length || 0;
            document.getElementById('count').innerHTML = `<h3>Post Count: ${postCount}</h3>`;
            const detailsDiv = document.getElementById('details');
            detailsDiv.innerHTML = '';
            postData.forEach(postItem => {
                const postElement = document.createElement('div');
                postElement.className = 'col mb-4';
                postElement.innerHTML = `
                    <div class="card shadow-sm">
                        <div class="card-body">
                            <h5 class="card-title">${postItem.title}</h5>
                            <p><strong>Channel:</strong> ${postItem.channel_name}</p>
                            <p><strong>User:</strong> ${postItem.user_name}</p>
                            <p>${postItem.comment}</p>
                        </div>
                    </div>
                `;
                detailsDiv.appendChild(postElement);
            });
        } catch (error) {
            console.error('Error fetching data:', error);
        }
    }
    fetchGroups();
</script>