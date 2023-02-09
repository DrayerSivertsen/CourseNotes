# Making Money

* there are costs associated with deploying any app
    * development equipment
    * developer registration (for app store and play store)
    * testbed hardware
    * developer time

* apps might also have specific additional costs
    * content creation / licensing (game levels, articles)
    * access to third party APIs
    * infrastructure

## Charging for the App
* one obvious approach is to charge for the app
* apple, google, amazon, etc all have app marketplaces
* they all allow you to charge for your application, if you want

* big marketplaces migh have a cost of entry
    * apple has annual, organization-level fee
    * google is one-time, but per dev
    * amazon is free
* could roll your own marketplace for android

## Marketplace Considerations
* apple, google, amazon are all going to take a cut of your sales
* in exchange, you get:
    * payment processing
    * hosting
    * update management
    * a certain air of respectiability

* app marketplaces tend to have set price options
    * typically things like $x.99

* generally, can't charge again for the "same version" of an app
    * updates are normally free
    * if you do a complete rewrite or something, you probably have to list a new version

## In-app Purchases
* all of the major marketplaces support in-app purchases
    * typically marketplace is going to want a cut, but give you things for that
    * can often manage the purchase via your website, if you want to cut them out

* IAP give us a few different options for monetizing, e.g.
    * trial editions
    * freemium
    * piecemeal functionality
    * one-off purchases

## Trial / Demo Versions
* goal is get customers in the door before they have to pay
* allow user to play with part of your functinality before committing money
    * the first few levels of a game
    * the full app, but with limiations
        * disable import / export
        * watermark output
        * limit resources

## Freemium App / Services
* common with apps and internet services
* offer a free app with basic functionality, charge for the full verion
    * differs from a trial in that base is always free and useful

* can work with either subscriptions or one-time purchases
    * dropbox gives out 2GB of storage for a username and password
    * pay them monthly / annually for a lot more storage

* need to provide a useful free service, make the value of upgrading clear

## Piecemeal Functionality
* for some apps, it makes sense to sell functionality piecemeal

* consider an app that draws diagrams:
    * most people want flow charts, org charts, etc
    * maybe charge a one-time fee for other things
        * UML diagrams
        * network schema

## One-off purchases
* purchases intended to more or less immediately turn into something else
* reddit coins, in-game currency

* largely a game thing, and requires care
    * need to provide a value preposition: what does customer get out of it?
    * need to be careful about balance in multiplayer games
        * pay-to-win is generally a bad look
    * also need to be super careful around "loot crates"
        * highly variable, quickly changing regulatory environment
        * easily overlaps with pay-to-win
        * gambling, addition
        * only including cosmetics seems safest
* depending on rewards, a few 'whales' can easily fund your entire userbase

## Subscriptions
* user regularly pays for something, rather than one-time purchases
* generally most useful for ongoing costs
    * you only have to develop a brush once, so pay for it once
    * media outfits need to pay their content creators
    * anyone with infrastructure needs to keep it running

* marketplaces generally support handling subscriptions, for a cut

* opportunities here to play with your value proposition
    * piecemeal purchases or a subscription for the whole library
    * monthly vs annual rates
    * different tiers of access

## Advertising
* various and sundry ad networks for mobile
* apple no longer does advertising, but google does for both platforms

* plenty of options for how to integrate ads:
    * show a small banner ad in your interface
    * use ad views to engable a desirable thing
        * view an ad for an extra life
        * view an ad to export a high-res image
    * use one-time or subscription purchase to disable ads

* generally, users will tolerate unobtrusive ads, or ones they opt into seeing
* be aware that there are ad blocks for mobile, and network-level blockers exist
