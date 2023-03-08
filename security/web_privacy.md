# Web Privacy

## Cookies
* a temporary structure to store web data items
* revolutionized the web
    * turned web ecosystem from stateless to stateful
    * good for authentication
    * bad for privacy
* example
    * SID=DQAAAK...Eaem_vYg; Domain=example.com; Path=/index.html; Expires=Wed
* a typical cookie has SID, domain, path, expiration, and flags
    * the example has two flags
        * secure - only send over HTTPS
        * Httponly - accessible only by HTTP/S (not scripts or style sheets)
* helps authenitcation by enabling setting od permissions for users on a website
* a user doesn't have to log in every time they visit a website
* undermines privacy because websites abuse cookies to store user preferences
* the user preference data can be used for potentially uncolicited ads

* cookies can enable web profiling of a user
* web profiling:
    * traffic monitoring
    * service monitoring
    * temporal monitoring
    * content monitoring

## EverCookies
* evercookies are seemingly persistent cookies
    * javascript API
    * cookies automatically repopulate even if you delete them
    * done by copying cookie content into all available data stores
    * scripts are used to enable the auto repop
* evercookies started out to enable data storage for web browsers
    * user data
    database items
    