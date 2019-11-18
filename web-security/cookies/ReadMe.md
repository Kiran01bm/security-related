## General Notes

Localstorage is designed to be accessible by javascript, so it doesn't provide any XSS protection. 

However, cookies have security flags which protect from XSS and CSRF attacks. HttpOnly flag prevents client side javascript from accessing the cookie, Secure flag only allows the browser to transfer the cookie through ssl, and SameSite flag ensures that the cookie is sent only to the origin. If SameSite is not supported in the client then to protect from CSRF it's better to use other strategies. For example, sending an encrypted token in another cookie with some public user data.

So cookies are a more secure choice for storing authentication data.
