# **Readings: Authentication & Production Server**

## **What is JSON Web Token?**

JSON Web Token (JWT) is an open standard that defines a compact and self-contained way for securely transmitting information between parties as a JSON object. This information can be verified and trusted because it is digitally signed. 

<br>

### **Signing JSON Web Tokens**

*Signed tokens* can verify the integrity of the claims contained within it, while *encrypted tokens* hide those claims from other parties. 

When tokens are signed using public/private key pairs, the signature also certifies that only the party holding the private key is the one that signed it.

<br>


### **When should you use JSON Web Tokens?**

- **Authorization:** When you need to authenticate a user and/or perform actions on behalf of a user.

    *Single Sign On* is a feature that widely uses JWT nowadays, because of its small overhead and its ability to be easily used across different domains.


- **Access Control:** When you need to control access to a resource. 

- **Information Exchange:** When you need to exchange information between different parties.

    Because we're using public/private key pairs—you can be sure the senders are who they say they are. Additionally, as the signature is calculated using the header and the payload, you can also verify that the content hasn't been tampered with.

<br>

### **What is the JSON Web Token structure?**


In its compact form, JSON Web Tokens consist of three parts separated by dots (.), which are:

- **Header:** 

    The header typically consists of two parts: 
    - **Type:** The type of the token. (e.g. JWT)
    - **Algorithm:** The algorithm used to sign the token. (e.g. RSA, HMAC, SHA256, )

        ```json
        {
            "alg": "HS256",
            "typ": "JWT",
            
        }
        ```

<br>

- **Payload:** 

    The payload contains the claims you want to pass, which are statements about an entity (typically, the user) and additional data. 

    ```json
    {
        "sub": "1234567890",
        "name": "John Doe",
        "iat": 1516239022
    }
    ```

Basically you will see the token is composed by the above three parts as such:
```
xxxxx.yyyyy.zzzzz
```
```
header.payload.signature
```

So we have here:
```
header = eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9
payload = eyJ0b2tlbl90eXBlIjoiYWNjZXNzIiwiZXhwIjoxNTQzODI4NDMxLCJqdGkiOiI3ZjU5OTdiNzE1MGQ0NjU3OWRjMmI0OTE2NzA5N2U3YiIsInVzZXJfaWQiOjF9
signature = Ju70kdcaHKn1Qaz8H42zrOYk0Jx9kIckTn9Xx7vhikY
```

<br>

- **Signature:** 

     create the signature part you have to take the encoded header, the encoded payload, a secret, the algorithm specified in the header, and sign that.
    ```json
    HMACSHA256(
        base64UrlEncode(header) + "." +
        base64UrlEncode(payload),
        secret)
    ```

<br>
<br>

## **How do JSON Web Tokens work?**

In authentication, when the user successfully logs in using their credentials, a JSON Web Token will be returned. Since tokens are credentials, great care must be taken to prevent security issues. In general, you should not keep tokens longer than required.

Whenever the user wants to access a protected route or resource, the user agent should send the JWT, typically in the Authorization header using the Bearer schema. The content of the header should look like the following:

```
Authorization: Bearer <token>
```

<br>

The following diagram shows how a JWT is obtained and used to access APIs or resources:

![Client Cred](imgs/client-credentials-grant.png)


1. The application or client requests authorization to the authorization server. This is performed through one of the different authorization flows. For example, a typical OpenID Connect compliant web application will go through the /oauth/authorize endpoint using the authorization code flow.

2. When the authorization is granted, the authorization server returns an access token to the application.

3. The application uses the access token to access a protected resource (like an API).

<br>


## **Installation & Setup**

1. run this command: 
    ```
    pip install djangorestframework_simplejwt
    ```

2. And then add the following to your settings.py:

    ```
    REST_FRAMEWORK = {
        'DEFAULT_AUTHENTICATION_CLASSES': (
            'rest_framework_simplejwt.authentication.JWTAuthentication',
        ),
    }
    ```

3. And then add the following to your urls.py:

    ```
    from django.urls import path
    from rest_framework_simplejwt import views as jwt_views

    urlpatterns = [
        # Your URLs...
        path('api/token/', jwt_views.TokenObtainPairView.as_view(), name='token_obtain_pair'),
        path('api/token/refresh/', jwt_views.TokenRefreshView.as_view(), name='token_refresh'),
    ]
    ```


