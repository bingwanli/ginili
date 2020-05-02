---
layout: default
title: Projects
---


<div class="main-content">
  <h2>LIGNE</h2>
  <h4><a href="http://www.my-ligne.com" target="blank" text-align="center">my-ligne.com</a></h4>
  <em>Problem:</em>
  <p>The connection between discovering new brands and purchasing from the new brand is weak. People discover new brands on platforms
  like Instagram and Pinterest, but rarely make purchases there.</p>

  <em>Solution:</em>
  <p>We created a website where editorial images from small international brands are featured randomly in a clean but endlessly scrolling page.
  Users can leisurely scroll through the page, and like or unlike images they feel fit their personal style. On the brand page, users are introduced
  to only the brands with editorial images that she has liked. She can learn about the brand, add products to her cart, or share with friends. </p>


  <em>Context:</em>
  <p>We worked in a team of 4 and have one week from idea to execution. The process evolved from Figma prototypes to a live demonstration
  at the end of the week. My role was backend. Here's a peek at my responsibilities:</p>


  <strong>Schema</strong>
  <p>I turned our team's concept and features into models with PostgreSQL. Our main models were products, users, and brands, but since there
  were multiple brand images per brand, we created a separate model for brand images. </p>
  <div class="code">
    <img src= "assets/images/schema.png" class="code">
  </div>

  <strong>Users</strong>
  <p>We used Devise for our user database. With Devise, I was able to save data to the current_user, including the brand images and products they have liked or added to cart.
  I also set permissions on pages that needed log-in authorization and pages that did not.</p>

  <strong>Scraping</strong>
  <p>Initially we tried to scrape data off e-commerce websites to populate our pages. However, since we were working with small brands,
    we had to rewrite our code for every brand which was too cumbersome. We ended up seeding the data through the mechanism below. </p>
    <div class="code">
    <small>Scraping data</small>
      <img src= "assets/images/scraping.png" class="code">
    </div>

  <strong>References - Brands and Brand Images</strong>
  <p>Users see randomly ordered brand images on the main index page that they can like. She can see all the brand images that she liked, organized by brand on a separate page. A brand has many brand images and brand images belong to a brand.
  Because our team had to seed a lot of brands in advance of demo day, I also created an admin area where we could upload multiple brand images and create a brand and
  its linked images at the same time. We used Carrier Wave and Cloudinary for the uploads.</p>

  <div class="code">
    <small>Admin form for uploading multiple brand images and a brand at the same time</small>
    <img src= "assets/images/newbrandview.png" class="code">
  </div>
  <div class="code">
    <small>Adding brand images in the brand controller via multiple uploads</small>
    <img src= "assets/images/brandcontrollercreate.png" class="code">
  </div>
  <div class="code">
    <small>Liking mechanism for brand images in brand images controller</small>
    <img src= "assets/images/brandimagecontroller.png" class="code">
  </div>

<strong>Recommendations</strong>
<p>We used the gem Recommendable to generate product recommendations with collaborative filtering logic. The liking mechanism we had on brand images and products fed the calculations. We used Redis to
  deliver recommendations and created jobs to recalculate the recommendations. We deployed on Heroku.</p>
  <div class="code">
    <small>Recommendations view on the user's profile</small>
    <img src= "assets/images/RecUserProfile.png" class="code">
  </div>
  <div class="code">
    <small>Job to recalculate recommendations</small>
    <img src= "assets/images/RecRecalculateJob.png" class="code">
  </div>
</div>
