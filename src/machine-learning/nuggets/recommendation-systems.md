# Recommendation Systems

Recommendations are for helping users to find something within a limited time, solving the problem of discovery.

Recommendation engines perform tasks like:

* Filter relevant products
    * Similar to ones the user like
    * Liked by similar users
    * Products purchased along with the product
* Predict what the user would choose
    * Clicked on
    * Added to the cart
    * Rated highly
* Rank on relevance to the user

Most recommendation systems use one or more of the techniques below.

## Content-based Filtering

Comparing similarity of the objects. Filtering based on item attributes, description and/or content. Used to find the products similar to the ones that the user has already indicated that they "like".

Normally used with text documents (books, articles, etc)

Start by:
1. Identifying `attributes` that differentiate products, that may be influential in deciding if the user will like the product or not. Represent products in terms of descriptors or attributes. Represent all these attributes as `vectors` or `tuples`.
2. Create a user's profile based on the user's history, by quantifying what the user likes. Represent users using the same product descriptors or attributes.
4. Find products that match the user's profile based on distance between two vectors.

Identifying the right set of attributes is the key challenge in content-based filtering, typically collection manually.

Alternatively, you could use NLP for generating descriptors, based on presence, absence or frequency of words in the document. Once you have the frequency, you can then find the nearest neighbors for matching.

Content-based filtering requires `manual data collection` phase, to map every product and user against the identified attributes. Hence pure content-based filtering are `less common`.

The most successful example is [the music genome project](https://en.wikipedia.org/wiki/Music_Genome_Project), owned by Pandora radio. They built descriptors for every song in their catalog. Every song is represented by 450 "genes" or factors or attributes. Trained musical analysts score each song on these attributes. The process normally takes 20-30 minutes per song. Using all this data, the radio keeps playing songs that match the user's preferences.

## Collaborative Filtering

Liked by similar users. Predicting what a user may like, without knowing anything about the product. This technique is `preferred a lot`. It does not even require you to know the description of the product.

Ask a friend, who likes the same things as you do!
So if two users have the same opinion about a bunch of products, then they are likely to have the same opinion about other products too. The algorithms rely on user behavior (browse clicks or searches and purchase history, ratings, similar users, etc). It `cannot` use product descriptions and user demographics. It's objective is to predict a user's score for a particular product.

Two popular techniques are:
1. `Nearest Neighbor based methods` - tries to find users who are most similar to a particular user, based on some similarity metrics and using weighted average
2. `Latent Factor based methods` - uses attributes identified in content-based filtering and maps users and products against those factors. Inspired by content-based but you still cannot use product description or user demographics.

### Nearest Neighbor

The objective is to predict a user's rating for a product they haven't rated yet.

Also known as `Memory based method`, because they usually involve in-memory based calculations or looping through a large part of the database, which is also a challenge for scalability reasons. Amazon and Barnes & Noble uses memory-based collaborative filtering techniques for most of their recommendations.

1. Find the `k-nearest neighbors` of the user
2. Take a weighted average of their rating for the product
3. Build a `rating matrix` between user and items. No ratings by the user for the item will stay blank.
4. Compare ratings and return the weighted average rating for the item in question.
5. This same metric can be used for the weight of each neighbor in the predicted rating.

`Similarity` (or `distance`) between two vectors or tuples can be measured in many ways. Popular ones being:
1. `Euclidean Distance` is simply a distance between two coordinates in a straight line, calculated using pythagoras theorem. The same concept can be applied to a 3-d space.
2. `Cosine similarity` is calculated by Cosine angle between two coordinates. Lower angle is a sign of high similarity.
3. `Pearson Correlation` is same as correlation used in linear regression. Analogous to cosine similarity, but after adjusting the vectors by the respective means. Users have a `natural bias`. Some naturally rate movies higher, while others rate everything low. One way to normalize this bias is by taking average rating. This is a mean of all ratings for the user, and then shift each number by their mean. Cosine similarity between these two new vectors is called Pearson correlation.

Here in the equation, weight constant is the similarity between users. Or weighted average rating between users, for example.

For `top picks`, predict ratings (using the formula for weighted average for n users) for the product not purchased or seen, and then pick the top N rated products.

Instead of user-centric, this can be performed for item-centric as well. For example, for a 3rd part of the movie, find ratings for first two parts and rate 3rd part accordingly.

### Latent Factor

Latent factor methods identify hidden factors that influence users from user history. `Matrix Factorization` is used to find these factors. This method was first used and then popularized for recommendations by the `Netflix` Prize winners. Many modern recommendation systems including Netflix, use some form of matrix factorization.

## Association Rules

Purchased along with the ones the user liked. The main idea is to find some kind of association between two products, if one is bought, then the other will also be bought. Example: batteries for camera.

## Resources

* 
