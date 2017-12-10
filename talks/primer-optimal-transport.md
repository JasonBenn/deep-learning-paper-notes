## [A Primer on Optimal Transport](https://optimaltransport.github.io/)

* tl;dr:
    * Bottom line: helps you compute the distance between two distributions.
        * Averaging things together gives is like teleporting mass. W distance is like shifting mass gradually. Makes for better interpolations.
    * How do we compute them?
        * Imagine two discrete distributions (each with 5 points). Goal is to compute 5x5 distance matrix. With that, we can compute the total cost of moving mass from A to B (given the locations of each point).
        * Solving optimal transport (imagine histogram on X, histogram on Y, and thin line between two, drawn darker where more mass is moving from one to the other) is computationally intractable.
        * By adding entropy regularization (image thin line from above getting fatter/fuzzier), we can solve this by iteratively estimating matrix decomposition factors u and v with Sinkhorn's algorithm ("very simple, everyone in this room could figure it out").
        * Once we have them, we multiply u x K x v (K is a kernel function of some kind) and get our distance matrix.
    * Uses:
        * Document comparison: by mapping words into vector space with word2vec, we can represent documents as distributions in space (locations are words, weights are simple counts or tf-idf weightings of those words), now we can compute and compare distances between documents.
        * Social networks: a new person joins, want to estimate who their friends are. We can model connections as a distribution, so we compute a weighted average of the nearby distributions using Wasserstein barycenter (weighted average of W distances).
        * And of course, as a loss metric for generative models: WGANs.

* Intro, motivating problems, description of problem
    * tldr: "Natural geometry for probability measures"
        * tool for comparing probs by giving us a distance metric
    * probabilities show up everywhere in ML
        * statistical models
        * bags of features
            * geometry: word2vec gives us space of words (surprising!)
        * brain activation maps
            * geometry: surface of brain
        * color histograms
            * geometry: RGB space
        * generative models vs data
    * Monge's problem (1781): moving earth.
    * Kantorovich problem
        * Moving troops during WWII.
        * Transportation matrix constraints: p: need to assure that all soldiers leave barracks, and all destinations are filled
        * Distance matrix: rows are sources, columns are destinations, table is how much to move each.
            * (1, 2): source point 1 to destination point 2 (both out of 3).
        * Cost function: total amount of work in distance function.
    * Math formalism
    * OT as geometry
    * OT as loss function
* How to optimize (algorithms)
    * Typology: discrete/continuous problems
        * discrete -> discrete. Good!
        * discrete -> continuous. WIP
        * continuous -> continuous. WIP
    * Bures metric
        * Between two Gaussians:
            * Optimal map: linear map
            * This map is the gradient of the convex function
            * This matrix is positive definite
        * Discrete -> Discrete
            * Neat special case: when points are all the same magnitude: Optimal assignment = optimal transport
            * More general case: weights must add up to 1, locations can be anywhere
            * This comes down to a "linear program"
            * Minimum of set of all matrices that satisfy these constraints. Solved via the dual.
    * Easy cases, zoo of solvers
    * Entropic regularization
        * Min cost flow solver: n^3 log(N). Better than a linear program, apparently, but still not great.
        * Wasserstein: not differentiable: solutions will jump around as you perturb your loss function.
            * Image of right angle rotating around hexagon (solution space)
        * Adding entropy: instead of mapping mass from one dist to another, move it fuzzily.
        * As gamma (entropy term) goes to infinity: product of distributions
        * Suddenly we've got fast & scalable algorithm
            * Factorizes very well somehow
        * Simplifies. Sinkhorn's algorithm: alternate solving for u and v (what are they again?), and it'll converge on a solution.
            * u and v are diagonal factors of transportation matrix.
                * For discrete <-> discrete this makes sense
                * If either side is continuous, this is a function (which you can still factorize)
                * K is a kernel function
                    * Has something to do with the dual of the problem?
                    * Represents proximity metric - approaches 0 if they're close?
                    * How is this a matrix that you can multiply by?
            * Combine them all and you'll get the answer!
        * Bottom line: if you're OK with slightly fuzzier solution: 1M times speedup from matrix multiplication.
        * This dude said "very simple" at least 150 times
            * "Very simple algorithm that everyone in this room would be able to figure out"
* Applications! (W as loss)
    * Wasserstein distances for retrieval
        * Rubner '98 (histograms of color space)
        * If you can embed words into Euclidean space, then you can understand document as point cloud in that space
            * Now that you have histogram, you can figure out similarity between documents
            * Word Mover's distance: Kusner '15, amazing for document retrieval/search
    * W barycenters (averages)
        * Averaging measures
            * With L2/KL distance: image of purple distribution with 4 peaks instead of the 2 that blue has and 2 that red has, etc
        * Barycenter = weighed average
        * Hmm. But you'd have to compute transport distances to every point to each possible barycenter.
            * Instead of computing a million Ws, assumign you're willing to use entropic regularization to make it differntiable, you can use gradient descent to find barycetner (start at hypothesis, then iterate - how many times? til it converges?)
        * Applications of W barycetners:
            * Finding barycenter of all brain surface activations = general activation
            * Aggregating parallelization outputs: W posterior (WASP)
                * If your dataset is too big to fit on one machine...
                * Find a bunch of parameterized distributions, then find their barycenter!
                * Distribution aggregation! Cool.
                * Great for parallelization, too.
            * Semi supervised social network estimation
                * Social network: everyone has distributions of friends
                    * Assumption: similar people have similar sets of friends
                * For every new person with unknown friends, compute barycenter of their nearby friends!
                * Great image in the slides about this. (77?)
            * Dictionary learning
                * Basis that describes these histograms over space of words?
                * Small set of bases that explain very large dictionary of topics?
                * ??? Wish I understood this application better.
    * W for unsupervised learning
        * W PCA (variance)
    * W inverse problems
        * I have a dictionary, I think it's an average, I want to explain it in terms of its component corners
        * Example: I have a teddy bear with holes, use database of complete teddybears to compute who teddybear
    * Transfer learning:
        * Use optimal transport to align one image dataset to another (Amazon photos with nice labels)
        * Products are probably distributed similarly, right?
        * Once dataset is shifted over, train a classifier.
            * Awesome pic on 87.
* W loss for generative models (W for estimation)
    * New development: W distance between probas with diff mass!
    * Generative modeling: whole point is to "push-forward" low D space (latent encoding) into high D space (nice image)
    * Maximum likelihood estimation: doesn't work - is 0 in most places. Blame KL?
        * Lots of alternative distances - this problem has been around for a while.
    * Best possible classifier is good choice of loss metric
* Not mentioned
    * statistical challenge to compute w (they talked about computational)
    * linear assignment: W :: quadratic assignment : Gromov-Wasserstein
    * Dynamical aspects of optimal transport (?)
    * Transporting vectors/matrices
* Terms I didn't understand
    * closed problem
    * Primal/dual
        * constraints <=> variables
    * Diracs
    * "lift" euclidean space into dirac space
    * linear program
    * product of distributions
    * Kernel functions
    * cf.
