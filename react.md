Sure, I can provide you with a simple React project structure along with code for each file based on the provided specifications. Here's how the file structure could look:

```
my-react-app/
  ├── src/
  │   ├── components/
  │   │   ├── Card.js
  │   │   ├── CommentCard.js
  │   │   ├── Post.js
  │   │   ├── PostList.js
  │   │   └── NewPostForm.js
  │   ├── pages/
  │   │   ├── LandingPage.js
  │   │   ├── PostDetailPage.js
  │   │   └── NewPostPage.js
  │   ├── App.js
  │   ├── index.js
  │   └── index.css
  ├── public/
  │   └── index.html
  ├── package.json
  └── README.md
```

Now, let's create the code for each file:

1. **App.js**:

```javascript
import React from 'react';
import { BrowserRouter as Router, Switch, Route } from 'react-router-dom';
import LandingPage from './pages/LandingPage';
import PostDetailPage from './pages/PostDetailPage';
import NewPostPage from './pages/NewPostPage';

function App() {
  return (
    <Router>
      <div className="App">
        <Switch>
          <Route path="/" exact component={LandingPage} />
          <Route path="/post/:postId" component={PostDetailPage} />
          <Route path="/new-post" component={NewPostPage} />
        </Switch>
      </div>
    </Router>
  );
}

export default App;
```

2. **LandingPage.js**:

```javascript
import React from 'react';
import PostList from '../components/PostList';

function LandingPage() {
  return (
    <div>
      <h1>Landing Page</h1>
      <PostList />
    </div>
  );
}

export default LandingPage;
```

3. **PostDetailPage.js**:

```javascript
import React from 'react';
import { useParams } from 'react-router-dom';
import CommentList from '../components/CommentList';

function PostDetailPage() {
  const { postId } = useParams();

  return (
    <div>
      <h1>Post Detail Page</h1>
      <h2>Comments for Post {postId}</h2>
      <CommentList postId={postId} />
    </div>
  );
}

export default PostDetailPage;
```

4. **NewPostPage.js**:

```javascript
import React from 'react';
import NewPostForm from '../components/NewPostForm';

function NewPostPage() {
  return (
    <div>
      <h1>New Post</h1>
      <NewPostForm />
    </div>
  );
}

export default NewPostPage;
```

5. **PostList.js**:

```javascript
import React, { useEffect, useState } from 'react';
import { Link } from 'react-router-dom';
import Card from './Card';
import axios from 'axios';

function PostList() {
  const [posts, setPosts] = useState([]);

  useEffect(() => {
    axios.get('https://jsonplaceholder.typicode.com/posts')
      .then(response => setPosts(response.data))
      .catch(error => console.error(error));
  }, []);

  return (
    <div>
      <h2>Posts</h2>
      <div className="post-list">
        {posts.map(post => (
          <Link key={post.id} to={`/post/${post.id}`}>
            <Card title={post.title} body={`${post.userId} - ${post.body}`} />
          </Link>
        ))}
      </div>
    </div>
  );
}

export default PostList;
```

6. **Card.js**:

```javascript
import React from 'react';

function Card({ title, body }) {
  return (
    <div className="card">
      <h3>{title}</h3>
      <p>{body}</p>
    </div>
  );
}

export default Card;
```

7. **CommentList.js**:

```javascript
import React, { useEffect, useState } from 'react';
import axios from 'axios';

function CommentList({ postId }) {
  const [comments, setComments] = useState([]);

  useEffect(() => {
    axios.get(`https://jsonplaceholder.typicode.com/posts/${postId}/comments`)
      .then(response => setComments(response.data))
      .catch(error => console.error(error));
  }, [postId]);

  return (
    <div className="comment-list">
      {comments.map(comment => (
        <div key={comment.id}>
          <h4>{comment.name}</h4>
          <p>{comment.body}</p>
        </div>
      ))}
    </div>
  );
}

export default CommentList;
```

8. **NewPostForm.js**:

```javascript
import React, { useState } from 'react';
import axios from 'axios';

function NewPostForm() {
  const [title, setTitle] = useState('');
  const [body, setBody] = useState('');

  const handleSubmit = (e) => {
    e.preventDefault();
    const data = { title, body, userId: 1 }; // Assuming userId is hardcoded to 1 for simplicity
    axios.post('https://jsonplaceholder.typicode.com/posts', data)
      .then(response => {
        console.log(response.data);
        // Redirect or handle success
      })
      .catch(error => console.error(error));
  };

  return (
    <form onSubmit={handleSubmit}>
      <div>
        <label>Title:</label>
        <input type="text" value={title} onChange={(e) => setTitle(e.target.value)} />
      </div>
      <div>
        <label>Body:</label>
        <textarea value={body} onChange={(e) => setBody(e.target.value)} />
      </div>
      <button type="submit">Submit</button>
    </form>
  );
}

export default NewPostForm;
```

This structure and code should fulfill the requirements you provided. Make sure to install the necessary dependencies like React, React Router, and Axios before running this application. You can do so by running `npm install` or `yarn install` in the root directory of your project.