# Problem Solving
### Expectation:
The Developer is able to display logical reasoning by drawing inferences that can be correlated to facts gathered, and prediction by extrapolating potential outcomes of solutions to identify risks and unintended consequences.

### Justification
On my engagement, an issue came up where we needed to find a general way to restrict assess to certain endpoints on our API in order to prevent data from leaking to unauthorised users within the company. I was tasked with first designing a permissions system based on our current user models that grants permissions to certain users and restrict certain users from the platform.

In order to do this, I had to review the current user models we have on the platform. I also asked questions to understand the kind of access and and restrictions that needs to be put in place. With this I was able to implement an access level control middleware that basically checks if a user can assess an endpoint based on the type of user and type of company the user also belongs to. This permission system is what is still being used despite the fact that users of the platform has almost doubled since the implementation.

I also have come up with possible solutions to how deployment/versioning problem at my current engagement. Which involves what state to put both the UI and API when deploying and how best to alert the user when new versions are released. [link](https://drive.google.com/open?id=109VBoaIIPKlwbXWecwcbYpm0gkouwaUX)