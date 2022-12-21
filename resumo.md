## Event triggered social media chatter model

### Gabriel José Souza e Silva / Matheus Marinatto
### Resumo

This project's goal is to describe and explore a social marketing-based model for information spread, testing different control techniques so to determine which one provides better results. An important constraint for most marketing campaigns nowadays is the advertising cost, therefore a key goal for dispersing a message is to do that as efficiently and possible respecting budget and time constraints. From that, many optimization problems can be formulated. The following question, described in [1] gives the reason for such models to exist:



> At a high level, how does an organization sell to someone? Typically, individuals or groups (like marketing agencies) are enlisted as message spreaders who broadcast that information in a variety of formats including billboards, social media posts, and television advertisements.



So in order to sell, it's necessary to spread information and the further question would be **how to maximize sells (and information spread) while minimizing costs**.



In [1], the approach to design an advertising model starts from the well established Vidale-Wolfe marketing model with some tweaks to better handle the social media dynamics. Quoting [2]:



> The Vidale-Wolfe marketing model is a first-order, linear, nonhomogeneous ordinary differential equation (ODE) where the forcing term is proportional to advertising expenditure. With an initial response in sales as the initial condition, the solution of the initial value problem is straightforward for a first undergraduate ODE course.



Mathematically, this model is described as follows:



$\frac{dS(t)}{dt} = \beta u(t)[M(t) - S(t)] - \delta S(t)$



where



- S(t) → Sales at time t;

- M(t) → Market size at time t;

- $\beta$ → Advertising constant;

- $\delta$ → Rate of brand sale decay;

- $u(t)$ → Control action at time t.



Most of the terms above are self-explanatory but $\beta$, which is described in [1] as “[…] the rate of decay of brand sale given no active advertising.”



From that, the Event-triggered Social Media Chatter Model is derived by doing the following:



1. Normalizing Vidale-Wolfe's model by setting $M(t) = 1$;

2. Breaking $\beta$ into two other constants:

1. $\beta_1$ → the social marketing campaign constant;

2. $\beta_2$ → the social interaction constant;

3. Generalizing the sales term $S(t)$ to an information spread value $X_t$.



In [1] the meaning of these constants is explained in the following paragraph



> The effectiveness of social marketing is affected by dynamic resource spending and promotion over the network to convince people to purchase a product, uphold a social or political movement, or join in an activity. The social marketing constant can be associated with a traditional advertising campaign or an event that triggers similar social media interest. Once people become exposed to an advertisement and decide to share the message, the social interaction constant may be viewed as the natural tendency of the social media network to advertise internally through posts, tweets, and likes without external influences and advertising.

>



The final mathematical model is



$$
dX_t = \beta_1 u(t)[1 - X_t] + \beta_2 [1 - X_t] X_t - \delta X_t
$$



or visually

![enter image description here](file:///Users/gabrieljsss/Library/Mobile%20Documents/com~apple~CloudDocs/ufrj-icloud/sexto-periodo/otimizacao/projeto_final/information-spread-optimization-model/assets/model.png)


The final definition to be presented is the concept of socio-equilibrium threshold. It basically describes the equilibrium level of social media chatter after the control (promotion) goes to 0 or mathematically



$$
X_{eqb} = 1 - \frac{\delta}{\beta_2}
$$



In [1], $\beta_2$ is multiplied by a factor k, but in this project the value of k will be embedded in $\beta_2$. Finally, the “[…] goal of social media marketing is to increase peoples’ attention and interest beyond the natural equilibrium point through the control action of spending resources on ads…” and at the same time minimizing the associated costs.