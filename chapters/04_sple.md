#### Software Product Line Engineering Platform

<div class="grid2x2">
<table>
<tr>
  <td>
    <figure class="fragment" data-fragment-index="0">
      <img src="images/ShiftLeft.png" alt="" style="width: 85%;">
      <figcaption>SHIFT LEFT</figcaption>
    </figure>
  </td>
  <td>
    <figure class="fragment" data-fragment-index="1">
      <img src="images/Reuse.png" alt="" style="width: 82%;">
      <figcaption>REUSE</figcaption>
    </figure>
  </td>
</tr>
<tr>
  <td>
    <figure class="fragment" data-fragment-index="2">
      <img src="images/Automation.png" alt="" style="width: 85%;">
      <figcaption>AUTOMATION</figcaption>
    </figure>
  </td>
  <td>
    <figure class="fragment" data-fragment-index="3">
      <img src="images/Continuous_Integration.png" alt="" style="width: 81%;">
      <figcaption>CONTINUOUS INTEGRATION</figcaption>
    </figure>
  </td>
</tr>
</table>
</div>

Note:

Software product lines, also known as software product lines (SPL), are an approach to software development that aims to efficiently develop a family of similar software products.

The basic idea is to identify common features and functionalities that occur in several products and make them reusable. This approach makes it possible to create different products on the basis of a common code and component base and to extend these with specific functions that are unique to each product.

The main advantage of this approach is the reusability of the software, which leads to a reduction in development time and costs.

In addition, this approach enables consistent quality across different products and facilitates the maintenance and further development of the software.

Software product lines are particularly useful in areas where similar products need to be developed for different customers or markets.

Although our presentation is about the automotive industry, I would now like to explain SPLE using the example of lamps. This is a small game project that we have created for demonstration purposes.

However, the methods are of course also transferable to other areas. Our framework is in productive use with real and complex projects.

--

## Our Light Collection

<div class="three-wide">
  <figure class="fragment" data-fragment-index="0">
      <img src="images/disco-light.png" alt="">
      <figcaption>flash</figcaption>
  </figure>
  <figure class="fragment" data-fragment-index="1">
      <img src="images/sleeping-light.png" alt="">
      <figcaption>dim & gentle fade</figcaption>
  </figure>
  <figure class="fragment" data-fragment-index="2">
      <img src="images/spa-light.png" alt="">
      <figcaption>gentle pulse</figcaption>
  </figure>
</div>

Note:

So welcome to our diverse world of lighting!

I would like to introduce you to three unique members of our lamp family.

At first glance, these lamps appear to be completely different.

(click)

The disco light with its energetic flashing function, ideal for parties;

(click)

The sleep light, which creates a calming atmosphere for a good night's sleep with its gentle colour change and dimmability;

(click)

And the spa light, which has a relaxing and rejuvenating effect with its gentle pulsation.

These lamps have been developed to create a unique mood in different environments.

But for all their differences, they have one thing in common.

--

## One core, many possibilities: <br>Our Software Product Line

![](images/core-assets.png) <!-- .element: style="width: 50%" -->

Note:
What connects these lamps on a deeper level is their core.

All three lamps use the same basic software to control their LEDs.

This common platform is the core of our product line.

Customised features have now been added.

We have added a flashing function to the disco light.

For the sleep light, we have focused on integrating a colour change and dimming mechanism.

And the spa light has a gentle pulsation.

By recognising and reusing core components, the development effort is reduced enormously.

Maintenance costs are reduced because we avoid code erosion.

And how core parts and customer requirements come together is determined by our underlying build system consisting of Cmake and KConfig.
