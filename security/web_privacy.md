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


## HSTS SuperCookies
* HSTS: HTTPS Strict Transport Security
* used to prevent web browsers from accidentally using a HTTP version of a site
    * HSTS SuperCookies store a command to force browsers
* security analysts found out that a host issuing HSTS SuperCookies can be comprimised and made to leak a user's web profile
    * all users of the host are vulnerable

## PanoptoClick
* cookies aren't the only privacy menace
* many programs enable unique identification of users
* webservers can make your browser execute all sorts of scripts and media content to determine your web profile

## Enhancing Privacy for Web Browsers
* privacy enhancing technologies (PET)
    * browser plugins
        * uBlock origin, privacy badger, ghostery, etc
    * disable third-party cookies
        * configuration option in most modern web browsers
        * can break some funcationality (i.e. ads and trackers)
    * Tor browser
    * Tails OS
        * live OS focusing on privacy
        * each boot ends a session with shutdown
        * some user-allowed persistent data from one session to another
        * configured to use Tor and other encryption tools
    * 'Do Not Track' (DNT) configuration setting
        * supported by most modern web browsers
        * HTTP header field values
            * 1: don't track
            * 0: track
            * NULL: no preference
        * problems
            * not satisfactorily defined
            * no incentives or regulation ensuring sites implement your DNT

## HTTPS Side Channel Leaks
* side channel leaks extract information from attributes of encrypted traffic
    * no decruption required
    * leverages known properties about webpage objects and content
    * focuses on enumerating low entropy data
    * focuses on data packets with higher density
    * works for TLS and WPA2
        * padding doesn't protect completely

* encrypted traffic from each website produces a similar encryption pattern
    * encryption pattern stays same for specific content types
    * from the captured encrypted data, we can determine
        * which website the data originated from
        * what type of content is in the data
        * what characters are in the data (especially for search engine queries)

* flow vectors
    * encrypted data regarding user navigation on a webpage
    * reveals info such as
        * which tabs/buttons of the website were clicked by the user
        * did a user select a condition
        * did a user select an option
        * what settings does the user have on a webpage
    