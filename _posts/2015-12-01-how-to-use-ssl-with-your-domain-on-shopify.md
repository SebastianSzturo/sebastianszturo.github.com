---
title:  "How to use SSL with your Domain on Shopify"
date:   2015-12-01 13:37
description: Shopify is a great platform to kickstart your startup...
---

**Update:** Thanks to the [Let's Encrypt](https://letsencrypt.org/) project Shopify just released SSL encryption for all shopify stores for free. [Check out their blog post for more details.](https://www.shopify.com/blog/73511365-all-shopify-stores-now-use-ssl-encryption-everywhere)

--

[Shopify](https://www.shopify.com/?ref=sebastian-szturo) is a great platform to start your online business with or to host a shop for your [multi million dollar business](http://shop.teslamotors.com/). With over 200,000 active stores, it's one of the biggest players in the market. There is just one disadvantage: You can't get a SSL certificate unless you use their enterprise level [Shopify Plus](https://www.shopify.com/plus/?ref=sebastian-szturo) plan.

### Why do I need a SSL certificate?

Let's ignore the [security reasons](https://www.quora.com/How-does-SSL-work) for a SSL certificate for a moment and just look at the business disadvantage that arise from not serving our page via https:

- Google's ranking algorithm will [rate your site lower](http://googlewebmastercentral.blogspot.de/2014/08/https-as-ranking-signal.html).
- Browsers are [starting to emphasize](https://twitter.com/rlbarnes/status/656554266744586240) the need for SSL to their users.
- Customers trust your site less if you don't have a SSL padlock.
<br><br>

### How do I get a SSL certificate for my Shopify store?

You can take advantage of [CloudFlare's free Universal SSL](https://blog.cloudflare.com/introducing-universal-ssl/) to get https for your Shopify store. They are using an extension of the TSL protocol named [Server Name Indication](https://en.wikipedia.org/wiki/Server_Name_Indication). This allows them to be able to serve a certificate for multiple domains using only one IP address, reducing the hosting cost.

Generally, if you're running a browser that is less than 6 years old, your browser is modern and Universal SSL on CloudFlare's free plans will work. The three biggest problem children legacy browsers are:

- Internet Explorer and Chrome on Windows XP (or older)
- Android pre-Ice Cream Sandwich<br>
<br>

If you are want to make sure your site also works on these older systems, pick CloudFlare's 20$ Pro Plan. The paid plan also provides you with more security by using "FULL SSL". (Encrypts the connection between your website visitors and CloudFlare, and from CloudFlare to your Shopify store.)

##### 1. Create an account and add your domain name to CloudFlare

![Cloudflare Sign Up]({{ site.url }}/assets/images/cloudflare-step-1.png)

##### 2. Move your DNS Records from your domain provider.

![Cloudflare Sign Up]({{ site.url }}/assets/images/cloudflare-step-2.png)

##### 3. Turn on Flexible SSL in Crypto -> SSL (with SPDY) -> Flexible

![Cloudflare Sign Up]({{ site.url }}/assets/images/cloudflare-step-3.png)


##### 4. Activate CloudFlare in DNS -> example.com -> Status Icon

![Cloudflare Sign Up]({{ site.url }}/assets/images/cloudflare-step-4.png)

##### 5. Add a https forwarding rule in Page Rules

![Cloudflare Sign Up]({{ site.url }}/assets/images/cloudflare-step-5.png)

Thanks to [Prem Sichanugrist](https://twitter.com/sikachu) and his blogpost on [Thoughtbot](https://robots.thoughtbot.com/set-up-cloudflare-free-ssl-on-heroku).

<div class="freelance">
  Need help setting up CloudFlare SSL on Shopify? <a href="mailto:s.szturo@me.com"> Contact me!</a>
</div>
