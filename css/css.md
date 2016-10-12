##**Question**

Hey mentor,

I'm having a really hard time with some CSS. I've been given a PSD in an assignment. I know what the document should look like, but I'm getting this instead.

Can you help me with this? Here is my code!

-Student

```
<header>

</header>
<section class="pricing">
  <div class="pricing-tiers">
    <div class="tier">
      <h1>The plan</h1>
      <ul>
        <li>You get all the things</li>
        <li>plus more!!</li>
      </ul>
    </div>

    <div class="tier">
      <h1>The plan</h1>
      <ul>
        <li>You get all the things</li>
        <li>plus more!!</li>
      </ul>
    </div>

    <div class="tier">
      <h1>The plan</h1>
      <ul>
        <li>You get all the things</li>
        <li>plus more!!</li>
      </ul>
    </div>
  </div>
</section>
```

```
header {
  width: 100%;
  height: 60px;
  background-color: #333;
}

.pricing {
  width: 100%;
  padding: 20px;
  background-color: tomato;
}

.pricing-tiers {
  width: 960px;
  margin: 0px auto;
  background-color: #ddd;
}

.pricing-tiers .tier {
  width: 260px;
  margin: 20px;
  padding: 10px;
  background-color: white;
  float: left;
}

.tier h1 {
  font-family: "Helvetica", sans-serif;
  font-weight: bold;
  font-size: 2em;
  margin-bottom: 20px;
  text-align: center;
}

.pricing-tiers > .tier:last-child {
  margin-right: 0px;
}
```

##**Response**
Hey Student,

This is a common problem that designers and developers encounter as they first began to implement advanced CSS styling on their sites. The issue stems from floating html elements, the "Zero Height Container Problem", and a CSS technique known as "clearfix".

Before we begin through the solution it's going to be extremely beneficial to have some background knowledge on the "Zero Height Container Problem". Check out the link below for a quick introduction:

<a href='http://complexspiral.com/publications/containing-floats/'>http://complexspiral.com/publications/containing-floats/
</a>

The reason you're seeing your `<div class="tier"></div>` elements stick outside of the `<div class="pricing-tiers"></div>` container is because the 'class=pricing-tiers' html element is not stretching vertically to contain the 'class=tier' floated elements within it. To coerce the outer container to stretch and fit the inner elements there is a technique known as "clearfix". Checkout what "clearfix" looks like in a CSS style sheet below:

```
.clearfix:after {
	content: "";
  display: block;
  clear: both;
}
```

Now checkout a visual representation of what setting a "clearfix" in your stylesheets and html accomplishes:

<img src="http://i.stack.imgur.com/gYRqS.jpg" width="800px"/>

In essence, whenever you have a parent container which will have floated children elements within it, you'll want to append the "clearfix" class to it. This will force the parent container to stretch vertically and wrap around all of it's children. See an updated version of your code below:

```
<section class="pricing">
  <div class="pricing-tiers clearfix">
    <div class="tier">
      <h1>The plan</h1>
      <ul>
        <li>You get all the things</li>
        <li>plus more!!</li>
      </ul>
    </div>

    <div class="tier">
      <h1>The plan</h1>
      <ul>
        <li>You get all the things</li>
        <li>plus more!!</li>
      </ul>
    </div>

    <div class="tier">
      <h1>The plan</h1>
      <ul>
        <li>You get all the things</li>
        <li>plus more!!</li>
      </ul>
    </div>
  </div>
</section>
```

```
header {
  width: 100%;
  height: 60px;
  background-color: #333;
}

.clearfix:after {
	content: "";
  display: block;
  clear: both;
}

.pricing {
  width: 100%;
  padding: 20px;
  background-color: tomato;
}

.pricing-tiers {
  width: 960px;
  margin: 0px auto;
  background-color: #ddd;
}

.pricing-tiers .tier {
  width: 260px;
  margin: 20px;
  padding: 10px;
  background-color: white;
  float: left;
}

.tier h1 {
  font-family: "Helvetica", sans-serif;
  font-weight: bold;
  font-size: 2em;
  margin-bottom: 20px;
  text-align: center;
}

.pricing-tiers > .tier:last-child {
  margin-right: 0px;
}

```

##**Suggestions**
1. Re-read through the above and make sure you understand each topic.
2. Apply the "clearfix" to your code and make sure you understand what it's changing exactly.
3. Try applying a "clearfix" to other HTML code you've written and make sure you obtain the correct result.

Don't hesitate to ask me if you need further clarification or you have similar questions.

Best regards,

Stefan
