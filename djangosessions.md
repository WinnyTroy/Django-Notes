The goal of this is to delegate the tasks of user authentication and registration to Django, yet use **Redis** to share user sessions.  

###Understanding Sessions  

Generally you can choose to manage your python app's session data in one of two ways:  
1. Cookie-based sessions: In this scenario, the session data is not stored in a data store on the backend.  
Instead, it's serialized, signed with a secret key and sent to the client. When the client sends that data back, its integrity is checked for tampering and it is deserialized again on the server.  
2. Storage-based sessions: In this scenario, the session data itself is not sent to the client. Instead, only a small portion is sent(a key) to indicate the identity of the current user, stored on the session store.  

The General Workflow:  
    1. Request page on Flask / Django
    2.Check for sessionID in Redis. If not present:
        a. Go to Login Page
        b. Login to Django/Flask
        c. Store session data in Redis
        d. Get sessionID on browser
    3. Request Page on Flask/Django again
    4. Check for sessionID in Redis. If exists:
    5. Get flask/Django page.
