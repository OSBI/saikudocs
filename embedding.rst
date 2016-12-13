Embedding
=========

Saiku can be embedded in a number of ways. Because of its restful nature, the server can be completely decoupled and used as a standalone service. If you just need Analytics in your webapp, then you have two choices.
IFrame Embedding
You can embed the Saiku UI within an IFrame and default to either a Table or Chart view. This is good when simple embedding within a wiki or webpage is required and no interaction between application and report is required. You could also change the CSS on the saiku server to mimic the target webpage so they look similar.
Saiku Embed Framework
Saiku Embed Framework is ideal for use cases when you require deeper embedding and interaction between source and target. For example you might want to create an application in which is passes parameters to Saiku reports to render the output, to do this Saiku Embed Framework is ideal.
