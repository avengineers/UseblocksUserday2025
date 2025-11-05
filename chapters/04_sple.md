### Software Product Line<br>Engineering Platform

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
<span style="color: grey;">*(Michael)*</span>  
Aim: Develop a family of similar software products. They are particularly useful in areas where similar products need to be developed for different customers or markets.

**Shift Left:**

* Enhance software quality by preventing defects as early as possible
* Achieve higher quality software, faster feedback loops and improved collaboration among team members.  
* TDD, Unit Testing, Static Code Analysis

**Reuse**

* Identify common features and functionalities
* Create different products on the basis of a common code
* Extend these with specific functions that are unique to each product.
* Consistent quality across different products
* Variant Management, Reusable Components, Docs-As-Code

**Automation**

* Increase efficiency, improve quality, optimize resource allocation and reduce costs. 
* Focus on more complex and creative tasks, while repetitive and time-consuming activities are handled by automated systems.  

**Continuous Integration**

* Integrate frequent and small software changes into a common shared codebase.
* Each change is verified by an automated build.

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

<span style="color: grey;">*(Michael)*</span>  
Although our talk is about the automotive industry, I would now like to explain SPLE using the example of lamps. This is a small  project that we have created for demonstration purposes.

However, the methods are of course also transferable to other areas. Our framework is in productive use with real and complex projects.

So welcome to our diverse world of lighting!

I would like to introduce you to three unique members of our lamp family.

At first glance, these lamps appear to be completely different.

<span style="color: grey;">*(click)*</span>

The **Disco** light with its energetic flashing function, ideal for parties;

<span style="color: grey;">*(click)*</span>

The **Sleep** light, which creates a calming atmosphere for a good night's sleep with its gentle colour change and dimmability;

<span style="color: grey;">*(click)*</span>

And the **SPA** light, which has a relaxing and rejuvenating effect with its gentle pulsation.

These lamps have been developed to create a unique mood in different environments.

But for all their differences, they have one thing in common.

--

## One core, many possibilities: <br>Our Software Product Line

![](images/core-assets.png) <!-- .element: style="width: 50%" -->

Note:
<span style="color: grey;">*(Michael)*</span>  
What connects these lamps on a deeper level is their **core**.
All three lamps use the same basic software to control their LEDs.
This common platform is the core of our product line.
Customized features have now been added.  

We have added a flashing function to the **Disco** light.
For the **Sleep** light, we have focused on integrating a colour change and dimming mechanism.
And the **SPA** light has a gentle pulsation.

By recognizing and reusing core components, the development effort is reduced enormously.
Maintenance costs are reduced because we avoid code erosion.
And how core parts and customer requirements come together is determined by our underlying build system consisting of Cmake and KConfig.

<span style="color: grey;">*(Hand over to Jochen)*</span>
