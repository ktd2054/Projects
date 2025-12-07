# IDOR (Insecure Direct Object Reference)

- access control vulnerability
- since the web application isn't verifying that the person making the request is the same person as the one who owns the package, an IDOR vulnerability appears, 
  allowing attackers to recover the details for packages belonging to other users. 
- Even worse is when a feature like this doesn't require a user to authenticate,
    then there would be no way to even tell who is making the request! 
- we need to understand authentication, authorization, and privilege escalation.

