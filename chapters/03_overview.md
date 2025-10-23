
## What are our key challenges?

* Project diversity <div class="fragment" style="color:red">Software Product Lines</div>
* Documentation and verification of software quality <div class="fragment" style="color:red">A.SPICE</div>
* Continuous Integration <div class="fragment" style="color:red">Less is more</div>

Note:
In the automotive world, we have to deal with an incredible variety of products. Tens of different manufacturers, with different models, model variants and then adapted to different markets and regions, depending on legal requirements.
Setting up each product as an individual project and rewriting the software again and again would be death for any company.
You have to find a suitable way to map this multitude of product variants via configurations.
We solve this via software product lines and thus break down the complexity of our product range to a certain extent.

(click)

To do this, we have to constantly check the quality of our products. In principle, this applies to every software product.
In the automotive world, however, we are very often dealing with safety-relevant functions where human life, or at least the safety of human life, is paramount.
Every developer is provided with a set of process rules for this purpose. This can be used to develop standardised software in such environments.
Even if many see this as an obstacle, it is intended more as an aid. 
I am talking here about Automotive Spice, or A.SPICE for short.

(click)

Thirdly, we naturally want to finalise and deliver our products quickly.
Time-to-market may not be everything, but it is a good basis.
We will now explain step by step what our solution looks like and why you don't actually need that much for a good CI.
