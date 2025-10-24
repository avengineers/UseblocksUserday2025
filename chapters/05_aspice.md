<!-- .slide: data-transition="none-out" -->

## A.SPICE

Automotive Software Process Improvement and Capability Determination <!-- .element: class="fragment" data-fragment-index="1" -->

https://vda-qmc.de/automotive-spice/ <!-- .element: class="fragment" data-fragment-index="1" -->

Note:
Now let's move on to our second challenge: A.SPICE.

"click"

The abbreviation A.SPICE stands for ...

Sounds fancy, but it is essentially a process model that describes the development of software in the automotive industry.

It is also a maturity model that defines maturity levels 0 to 5.

These maturity levels are achieved through the fulfilment of process requirements and must be demonstrated by defined artefacts.

I won't go into the maturity levels in detail, but I will go into the artefacts that need to be created.

--

<!-- .slide: data-transition="slide-in fade-out" -->

![](images/aspice_traceability.png)

Note:

Here you can actually see quite well what is expected of the developers: Lots of artefacts.

And then everything has to be linked together.

And since we as software engineers naturally want to automate everything, our goal is to be able to create the required artifacts with as little additional effort as possible using our platform.

Initially, we focussed on the processes

SWE.3: Software Detailed Design and Unit Construction and SWE.4: Software Unit Verification

processes.

--

<!-- .slide: data-transition="fade" -->

![](images/aspice_traceability_swe34.png)

![](images/lc_dir_tree.png)<!-- .element: class="fragment" data-fragment-index="2" -->

Note:

Here we can see again in detail what we have to do for SWE.3 and SWE.4.

We write the units in C and test them with Google Test or something similar, of course, we have that under control.

We create the documentation including the software detailed design with Sphinx and Restructured Text, also easy.

"click"

We put all of this for a component in a folder that looks like this: doc, src and test.

But how do we put it all into a document and link it together correctly?

The answer is ...

--

## Sphinx + Sphinx-Needs

conf.py:<!-- .element: class="fragment" data-fragment-index="2" -->
```python [152: 1|3-9|11-19]
extensions.append("sphinx_needs")

# Define own needs types
needs_types = [
    { directive="req", title="Requirement", prefix="R_", color="#BFD8D2", style="node" },
    { directive="spec", title="Specification", prefix="S_", color="#FEDCD2", style="node" },
    { directive="impl", title="Implementation", prefix="I_", color="#DF744A", style="node" },
    { directive="test", title="Test Case", prefix="T_", color="#DCB239", style="node" },
]

# Define own link types
needs_extra_links = [
    # SWE.3 BP.5: link from Implementation (Software unit) to Specification (Software detailed design)
    {"option": "implements", "incoming": "is implemented by", "outgoing": "implements"},
    # SWE.4 BP.5: link from Test Case (Unit test specification) to Specification (Software detailed design)
    {"option": "tests", "incoming": "is tested by", "outgoing": "tests"},
    # SWE.4 BP.5: link from Test Case (Unit test specification) to Test Result (Unit test result)
    {"option": "results", "incoming": "is resulted from", "outgoing": "results"},
]
```
<!-- .element: class="fragment" data-fragment-index="2" style="font-size:10pt" -->

Note:

Sphinx and Sphinx-Needs

"click"

Sphinx-Needs is an open source extension for Sphinx.

It makes it possible to define so-called "Needs" types and link them together.

"click"

We have defined our own types for the A.SPICE artefacts: Requirement, Specification, Implementation and Test Case.

"click"

We have also defined our own link types that describe the links between the artefacts.

Okay, so what does this look like in the code?

--

### Software Detailed Design

![](images/lc_swdd.png) <!-- .element: class="fragment" data-fragment-index="2" style="float: right; width: 40%" -->

```rst [1: 12-18]
Introduction
------------

The Light Controller module is responsible for managing
the behavior of a light based on the system's
power state. This document outlines the design considerations
and the high-level structure of the module.

Design Considerations
---------------------

.. spec:: State Management
   :id: SWDD_LC-001
   :integrity: B

    The light can be in one of two states: ON or OFF.
    The state transitions are triggered by changes
    in the system's power state.


```
<!-- .element: class="fragment" data-fragment-index="1" style="float: left; font-size:10pt; width: 55%" -->

Note:

First, let's take a look at the software detailed design.

"click"

Here we see an example of a Needs element in Software Detailed Design, i.e. directly in rst.

Here we use the Needs type "spec" for Specification, give the spec element a name and a unique ID.

"click"

The generated document then looks like this.

Here you can already see the link to the other artefacts.

--

### Unit Test Specification

![](images/lc_uts.png) <!-- .element: class="fragment" data-fragment-index="2" style="float: right; width: 40%" -->

```C++ [50: ]
/**
 * @rst
 * .. test:: light_controller.test_light_stays_off
 *    :id: TS_LC-006
 *    :tests: SWDD_LC-001, SWDD_LC-004, R_001
 * @endrst
 */
TEST(light_controller, test_light_stays_off)
{
    CREATE_MOCK(mymock);

    // Initial state: Power is OFF, so the light should be OFF.
    EXPECT_CALL(
        mymock,
        RteGetPowerState()
    ).WillRepeatedly(Return(POWER_STATE_OFF));
    EXPECT_CALL(
        mymock,
        RteSetLightValue(_)
    ).Times(0); // Expect that the light value doesn't change.

    for (int i = 0; i < 10; i++) {
        lightController();
    }
}
```
<!-- .element: class="fragment" data-fragment-index="1" style="float: left; font-size:10pt; width: 55%" -->

https://boschglobal.github.io/doxysphinx/ <!-- .element: class="fragment" data-fragment-index="2" -->

Note:

In the unit test specification, i.e. directly in the test code, the situation is somewhat different.

"click"

Here is a code example of a Needs element with the type "test" in an rst block within a Doxygen comment.

As you can see here, with a test element we also specify which spec elements and/or requirements are tested.

"click"

To get these rst blocks into our Sphinx document, we use Doxygen on the one hand and another open source tool called doxysphinx on the other.

Doxyshpinx enables us to integrate the complete HTML output of Doxygen into our Sphinx document.

--

### Software Unit

![](images/lc_swu.png) <!-- .element: class="fragment" data-fragment-index="2" style="float: right; width: 40%" -->

```C [106: ]
/**
 * @rst
 * .. impl:: Light Controller's main function
 *    :id: SWIMPL_LC-006
 *    :implements: SWDD_LC-001
 * @endrst
 * 
 * @brief Controls the light state.
 *
 * Uses a state machine to determine the light state based on
 * several inputs, e.g., the system's power state.
 */
void lightController(void) {

    switch (currentLightState) {
    case LIGHT_OFF:
...
    }
}
```
<!-- .element: class="fragment" data-fragment-index="1" style="float: left; font-size:10pt; width: 55%" -->

Note:

The situation is similar in the software unit.

"click"

Here we use a Needs element of type "impl" and link the spec elements that we are implementing.

"click"

An impl element with the link to the corresponding spec element then appears in the Sphinx document in the description of the documented function.

--

### Unit Test Results

![](images/lc_utr.png) <!-- .element: class="fragment" data-fragment-index="2" style="float: right; width: 50%" -->

```rst [1: ]
Unit Test Results
=================

.. test-report:: Unit Test Results
    :id: TEST_RESULT_src_light_controller
    :file: light_controller/junit.xml
```
<!-- .element: class="fragment" data-fragment-index="1" style="float: left; font-size:10pt; width: 45%" -->

<p style="text-align: center; font-size: 0.5em;">
<a href="https://sphinx-test-reports.readthedocs.io/">https://sphinx-test-reports.readthedocs.io/</a> <!-- .element: class="fragment" data-fragment-index="2" -->

Note:

And last but not least, the Unit Test Results.

"click"

We use another Sphinx extension called sphinx-test-reports to integrate the test results.

"click"

This extension integrates JUnit XML files into our sphinx document and supports sphinx-needs at the same time.

A test result is automatically linked to the corresponding test case via the name of the test case.

Conclusion: with Sphinx, Sphinx-needs, Doxygen, doxysphinx and sphinx-test-reports, we have brought together everything we need for Automotive SPICE in terms of unit construction and validation.
