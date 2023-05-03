Download Link: https://assignmentchef.com/product/solved-cs2040s-recitation-10
<br>
Google Maps team has hired you to improve their driving directions service in the US. As things are currently implemented, a user can query for the shortest path between any two cities. However, sometimes users care about other things, such as ensuring that they always maintain convenient access to a gas station along the road during their trip. For instance, they might request to be no further than 2 miles from the nearest gas station at any point along their recommended route.

Suppose US has a policy that mandates adjacent gas stations along the same road to be located apart by a <em>minimum </em>of 1 mile and a <em>maximum </em>of <em>k </em>miles. Moreover, two adjacent gas stations is always separated by an integer number of miles apart. For instance, there are never two adjacent gas stations at 2<em>.</em>5 miles apart. You may assume that <em>k </em>is relatively small compared to the number of cities and the number of roads.

For two cities <em>a </em>and <em>b</em>, we define the <em>best </em>route from <em>a </em>to <em>b </em>as the route which minimizes (out of all routes) the maximum separation distance between gas stations (in a single route). We refer to the maximum separation distance between adjacent gas stations along this <em>best </em>route as the <em>minimax </em>distance. If the minimax distance is 10, then it means that a driver travelling from location <em>a </em>to location <em>b </em>is guaranteed a route along which he/she will never be more than 10 miles from the nearest roadside gas station.

Consider the road network example in Figure 1, the maximum distance between adjacent gas stations is provided for each stretch of road. Suppose the start location is <em>a </em>and the destination location is <em>c</em>. Then the route [<em>a </em>→ <em>s </em>→ <em>e </em>→ <em>f </em>→ <em>c</em>] has a gas station at most every 7 miles apart. The route [<em>a </em>→ <em>d </em>→ <em>g </em>→ <em>h </em>→ <em>e </em>→ <em>f </em>→ <em>c</em>] also has a gas station at most every 7 miles apart and is therefore an equally best route (according to our minimax metric). By contrast, if the start location is <em>a </em>and the destination location is <em>e</em>, then the best route is [<em>a </em>→ <em>d </em>→ <em>g </em>→ <em>h </em>→ <em>e</em>] where the minimax distance is 4 miles.

<strong>Figure 1: </strong>Letters denote cities, numbers along roads denote maximum separation (in miles) between adjacent gas stations along it.

<h1>Problem Specification</h1>

<strong>Input</strong>

Your input to the problem is a road map (much like the one in Figure 1), where each road is labelled with the maximum distance between adjacent gas stations along it. For simplicity, each city is identified by an <em>integer </em>rather than a name string. The map is provided as an <em>adjacency list</em>, i.e. an array in which each entry in the array represents a city and contains a list of roads that run out of the city. Each entry in the list (i.e. a road) consists of a pair containing the city to which the road connects to, and the maximum distance between adjacent gas stations along that road. You may assume that all the roads are two-way, and that there is a gas stations in every city (so we are only concerned about gas stations along the roads).

<strong>Requirement</strong>

Your solution should comprise of two stages:

<strong>Preprocessing stage: </strong>Initialize the service by <em>preprocessing </em>the given road map and storing it in a data structure (DS) for querying.

<strong>Query stage: </strong>Service user requests by <em>querying </em>the DS for the maximum distance between adjacent gas stations along the <em>best </em>routes recommended to them (i.e the minimax distances).

Specifically, your solution must implement the following two functions to realize each stage respectively:

<ol>

 <li>void preprocessMap(Vector&lt;Vector&lt;ii&gt;&gt; map): Reads in the map and initialize the chosen DS</li>

 <li>int queryMinimax(int start, int destination): Return the minimax <em>distance </em>corresponding to the best route for the given start-to-destination request (Note that your algorithm <em>does not </em>have to actually track and return the best route itself)</li>

</ol>

Note that there are many possible solutions to this problem. Different solutions have different trade-offs in terms of preprocessing cost versus querying cost: some solutions may have a very fast preprocessing step but is very slow at answering queries; other solutions may have a very slow preprocessing step but is very fast at answering queries. In this case, we would prefer queries to be relatively fast. However we also want to minimize the time spent on preprocessing the map which may be very, very big.

<strong>Problem 1. </strong>Come up with at least two solutions and present them in pseudocode. Explain why your solutions work and provide their time and space complexities. What are the tradeoffs between your solutions?