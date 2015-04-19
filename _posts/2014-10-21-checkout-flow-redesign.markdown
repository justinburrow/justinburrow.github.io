---
layout: post
title:  "Checkout Flow Redesign"
date:   2014-07-22 12:00:00
categories: portfolio
tags: Development UX Magento
---
One of the initiatives I pioneered was a complete rethinking of our checkout flow. It was something no one had really peeled back the curtain on in quite a while, and I saw some very major improvements that could be made which would greatly enhance UX in the purchase path.

<!--break-->

Here are some of the pain points I attempted to address:

*   After adding an item to cart, you were immediately whisked away to the cart page. In order to get back to the page you were on to keep shopping, you had to press the back button, and to get to checkout, you had to first start on the cart page and then proceed to there. I felt that the user should be able to remain on the page and keep adding items, or move directly to checkout without having to hit the cart first.

*   The login function at the top of the cart was visibly insignificant to me, even though I knew where to look. I wanted to really call out the checkout as guest or login option, and include social sign-in functionality.

*   The long one-page checkout flow was just tedious. So many fields to stare at before completing your purchase. I felt that separating these out into a horizontal layout that slid the immediate fields into focus as you progressed, with clear indication of how much was left in the process would likely decrease bounce rate.

*   The function that calculated shipping options was a little wonky. It relied on AJAX to pull in the relevant shipping options based on address, but required a button press since the AJAX didn't reliably fire all the time. Since shipping rates are calculated based on the first three digits of the zip code, we worked out a function that calculated and recalculated shipping options when either three digits were entered, or the user deleted back to two digits and added a third digit back in. No button press necessary.

*   Finally, I wanted to hide the promotional code field, as there's some psychology to users seeing a promotional code input field and feeling incentivized to go find a coupon code to put in there. By hiding it, the intention was to discourage people from feeling motivated to find a coupon code.

This is running in a dev environment which is why the page feels laggy, but I feel this is a good illustration of the improvements we made.

<div class="video-container"><iframe src="http://www.youtube.com/embed/1Hj0cC9FaJA?rel=0" frameborder="0" allowfullscreen></iframe></div>

My wireframe set is available below - please open it in Acrobat and view it as a single page. It's a linked pdf so various parts of the page will progress the flow as intended.

![Checkout Flow Wireframe](/img/post-content/checkout-flow-redesign/checkout_wireframe_still.jpg){:.center}

[Download the full wireframe .pdf here](/img/post-content/checkout-flow-redesign/magento_checkout_UX.pdf)