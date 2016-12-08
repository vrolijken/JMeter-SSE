# JMeter-SSE
Attempt to get JMeter working for my SSE scenario, though hopefully it will be usefull to other people/scenarios

See http://stackoverflow.com/questions/38590354/jmeter-parrallel-requests-with-server-sent-events/40941905 

My first thought at solving this was something like this: 

![parallel samplers](https://raw.githubusercontent.com/vrolijken/JMeter-SSE/master/Parallel%20Samplers.png)

Here some new element (A) would be parent to two other elements (B and C). Element B would be a SSE sampler where there needs to be some configuration: Element B should be able to have an arbitrary number of events that can be detected and those should be reworked into an arbitrary number of signals. 

Element C should receive the signals and call any number of embedded Samplers, depending on which signal it is.

But in creating that image it occurred to me that this: 

![as logic controller](https://raw.githubusercontent.com/vrolijken/JMeter-SSE/master/as%20LogicController.png)

might also be feasable (possibly better?). The SSE request now looks a lot like a complex "Logic Controller". Again the SSE request must be configured to act on incoming requests. But rather than send out a signal, the "SSE Controller" fires off one of it's child Samplers (possibly with a parameter) depending on the event received. 

Not sure any of this will be doable.
