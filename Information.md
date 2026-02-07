Here’s your content formatted cleanly in **Markdown** with lists preserved exactly as you wrote them:

---

# Reddit - Community Posts, Video, Audio, Comments, Feeds

### Requires
- caching  
- cdn  
- no need of real time event  

### Stacks
- Fastapi  
- postgresql  
- redis for caching  
- postgres full text search (can scale up using elasticsearch)  
- Object storage s3  
- pythnon  
- post update etc (doubt, use or not to use)  
- celery  
- something for searching (not selected till now)  

---

# Backend
- Python FastAPI  
- DB: PostgreSQL  
- Cache: Redis  
- Background tasks: Celery  
- Object storage: Can use metadata to retreive and store the files in a more easier way by segregating videos, gif, images - Practically used s3, minio + CDN for content  
- Search: MEillissearch  
- Monitoring: Prometheus/Grafana (Have to see what they are)  
- Optional later: Kafka, Elasticsearch  

---

# Reddit: Home

1. Users Profile (EVERY USER HAS A DISTINCT USERNAME AND USER ID (ID NOT VISIBLE TO USER))  
   - Karma  
   - Date joined  
   - All posts (can change visibility)  
   - All comments (can change visibility)  
   - Saved posts and comments  
   - Upvoted posts and comments  
   - Downvoted posts and comments  
   - Avaters  
   - Drafts - not uploaded but is still persistant (for some days ie 14 and limited unfinished comments and media/post)  
   - Reddit coins and awards  
   - Trophies  
   - Reddit premium subscription status  
   - Stored in jsonb (SEE PIC 2) - Unique ID  

   - whoami - gives that @id:reddit.com  

---

2. Subreddits  
   - Sort by:  
     - Top  
     - New  
     - Hot  
     - Rising  
   - Followers/Subscribers  
   - Posts and comments  
   - Public and private subreddits  
   - Admins and moderators - Control with special permissions  
   - Rules and guidelines  
   - Flairs  
   - Banned users  

---

3. Messages  
   - Inbox  
   - Sent messages  
   - Unread messages  
   - Message requests  
   - Archived messages  

---

4. Notifications  
   - Upvotes and downvotes  
   - Replies to posts and comments  
   - Mentions  
   - Post from followed subreddits  

---

5. Posts  
   - Title  
   - Content (text, image, video, link)  
   - Flair  
   - Upvotes and downvotes  
   - Comments  
   - Awards  
   - Share options  
   - Edit and delete options  
   - Post analytics (views, engagement)  
   - Voting options (upvote, downvote, save, hide)  
   - Posts Submission By Users (/user/username/submit)  
   - Posts Submission By Subreddits (/r/subreddit/submit)  

---

6. Comments  
   - Content (Text, image, link, gif)  
   - Upvotes and downvotes  
   - Replies  
   - Edit and delete options  
   - Report options  
   - Save  
   - Share options  

   **Schema:**  
   - id  
   - post_id  
   - author_id  
   - parent_comment_id -- NULL = top-level comment  
   - body  
   - upvotes  
   - downvotes  
   - created_at  

   Comments will not be nested as its visible  

---

7. Search  
   - Search by keywords  
   - Filter by posts, comments, users, subreddits  
   - Sort by relevance, new, top, hot  
   - Advanced search options (date range, specific subreddit, author)  

---

# Proprietary Idea
- Users, posts, subreddits to be stored in SQL  
- Comments to be stored in SQL but nested (comment threads) should be stored in the unstructured data (see the sy)  

---

# Things to Note
- endpoints of all users → `/users/<username>` (username is probably stored like sql (not sure will read bout it))  
- endpoints of all subreddits → `/r/<subreddit>`  
- endpoints of all notifications → `/notifications`  
- endpoint of posts done in subreddits → `r/<subreddit>/1pdxxxx/<Title_of_that_post>` (`<space>` replaced with underscore)  

---    
