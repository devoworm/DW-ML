To be cross-posted to [Synthetic Daisies](http://syntheticdaisies.blogspot.com/) and [The Node](https://thenode.biologists.com/) blogs. Date: 10/30/19

## Pre-trained Models for Developmental Biology  
Bradly Alicea, Richard Gordon, Abraham Kohrmann, Jesse Parent, Vinay Varma 

#### 1351 words
Our virtual discussion group (DevoWormML) has been exploring a number of topics related to the use of pre-trained models in machine learning (specifically deep learning). Pre-trained models such as GPT-2 [1], pix2pix [2], and OpenPose [3] are used for analyzing many specialized types of data (linguistics, image to image translation, and human body features, respectively) and have a number of potential uses for the analysis of biological data in particular. It may be challenging to find large, rich, and specific datasets for training a more general model. This is often the case in the fields of Bioinformatics or Medical Image analysis. Data acquisition in such fields is often restricted due to the following factors:

1) privacy restrictions inhibit public access to personal information, and may impose limits on data use.

2) a lack of labels and effective metadata for  describing cases, variables, and context.

3) missing data points, which require a strategy to normalize and can make the input data useless.

We can use these pre-trained models to extract a general description of classes and features without requiring a prohibitive amount of training data. We estimate that the amount of required training data may be reduced by an order of magnitude. To get this advantage, pre-trained models must be suitable to the type of input data. There are a number of models specialized for language processing and general use, but options are fewer within the unique feature space of developmental biology, in particular. In this post, we will propose that developmental biology requires a specialized pre-trained model. 


This vision for a developmental biology-specific pre-trained model would be specialized for image data. Whereas molecular data might be better served with existing models specialized for linguistic- and physics-based models, we seek to address several features of developmental biology that might be underfit using current models:

1) cell division and differentiation events.

2) features demonstrating the relationship between growth and motion.

3) mapping between spatial and temporal context.

Successful application of pre-trained models is contingent to our research problem. Most existing pre-trained models operate on two-dimensional data, while data types such as medical images are three-dimensional. A study by Raghu et.al [4] suggests techniques specified by pre-trained models (such as transfer learning by the ImageNet model) applied to a data set of medical images provides little benefit to performance. In this case, performance can be improved using  data augmentation techniques. Data Augmentation, such as  adding versions of the images that have undergone transformations such as magnification, translation, rotation, or shearing, can be used to add variability of our data and improve the generalizability of a given model.

One aspect of pre-trained models we would like to keep in mind is that models are not perfect representations of  the phenomenology we want to study. Models can be useful, but are often not completely accurate. A model of the embryo, for example, might be based on the mean behavior of the phenomenology. Transitional states [5], far-from-equilibrium behaviors [6], and rare events are not well-suited to such a model. By contrast, a generative model that considers many of these features might generally underfit the mean behavior. We will revisit this distinction in the context of “blobs” and “symbols”, but for now, it appears that models are expected to be both imperfect and incomplete.

The inherent imperfection of models is both good and bad news for our pursuit. On the one hand, specialized models cannot be too specific, lest they overfit some aspects of development but not others. Conversely, highly generalized models assume that there are universal features that transcend all types of systems, from physical to social, and from artificial to natural. One example of this is found in complex network models, widely used to represent everything from proteomes to brains to societies. In their general form, complex network models are not customized for specific problems, relying instead on the node and edge formalism to represent interactions between discrete units. But this also requires that the biological system be represented in a specific way to enforce the general rules of the model. For example, a neural network’s focus on connectivity requires representations of a nervous system to be simplified down to nodes and arcs. As opposed to universality, particularism is an approach that favors the particular features of a given system, and does not require an ill-suited representation of the data. Going back to the complex networks example, there are specialized models such as multi-level networks and hybrid models (dynamical systems and complex networks) that solves the problem of universal assumptions.


Another aspect of pre-trained models is in balancing the amount of training data needed to produce an improvement in performance. How much training data can we save by applying a pre-trained model to our data set? We can reformulate this question more specifically to match our specific phenomenon and research interests. To put this in concrete terms, let us consider a hypothetical set of biological images. These images can represent discrete points in developmental time, or a range of biological diversity. Now let us suppose a developmental phenotype for which we want to extract multiple features. What features might be of interest, and are those features immediately obvious? 

In the DevoWorm group (where we mostly deal with embryogenetic data), we have approached this in two ways. The first is to model the embryo as a mass of cells, so that the major features of interest are the shape, size, and position of cells in an expanding and shifting whole. Last summer, we worked on applying deep learning to 

1) _Caenorhabditis elegans_ embryogenesis. [Github repository](https://github.com/devoworm/GSOC-2019)

2) colonies of the diatom _Bacillaria paradoxa_. [Github repository](https://github.com/devoworm/Digital-Bacillaria) 

While these models were effective for discovering discrete structural units (cells, filaments), they were not as effective at directly modeling movement, currents, or transformational processes. The second way we have approached this is to model the process of cell division and differentiation as a spatial and discrete temporal process. This includes the application of representational models such as game theory [7] and cellular automata [8]. This allows us to identify more subtle features that are not directly observable in the phenotype, but are less useful for predicting specific events or defining a distinct feature space. 

Our model must be capable of modeling multiple structural features concurrently, but also sensitive to scenarios where single sets of attributes might yield more information. Ideally, we desire a training dataset that perfectly balances “biologically-typical” motion and transformations with clearly masked shapes representing cells and other phenotypic structures. Generally speaking, the greater degree of natural variation in the training dataset, the more robust the pre-trained model will turn out to be. More robust models will generally be easier to use during the testing phase, and result in a reduction in the need for subsequent training. 


Finally, specialized pre-trained models bring up the issue of how to balance rival strategies for analyzing complex processes and data features. Conventional artificial intelligence techniques have relied on a representation which relies on the manipulation of symbols or a symbolic layer that results from the transformation of raw data to a mental framework. By contrast, modern machine learning methods rely on data to build a series of relationships that inform a classificatory system. While a combination of these two strategies might seem obvious, it is by no means a simple matter of implementation [9]. The notion of “blobs” (data) versus “symbols” (representations) draws on the current debate related to data-intensive representations versus formal (innate) representations [10-12], which demonstrates the timeliness of our efforts. Balancing these competing strategies in a pre-trained model allows us to more easily bring expert knowledge or complementary data (e.g. gene expression data in an analysis of embryonic phenotypes) to bear.

We will be exploring the details of pre-trained models in future discussions and meetings of the DevoWormML group. Please feel free to join us on Wednesdays at 1pm UTC at https://tiny.cc/DevoWorm or find us on Github (<a href="https://github.com/devoworm/DW-ML">https://github.com/devoworm/DW-ML</a>) if you are interested in discussing this further. You can also view our previous discussions on the DevoWorm YouTube channel, DevoWormML playlist (<a href="https://bit.ly/2Ni7Fs2">https://bit.ly/2Ni7Fs2</a>).


__References:__

[1] Radford, A., Wu, J., Child, R., Luan, D., Amodei, D., and Sutskever, I. (2019). Language Models are Unsupervised Multitask Learners. _OpenAI_, [https://d4mucfpksywv.cloudfront.net/better-language-models/language_models_are_unsupervised_multitask_learners.pdf](https://d4mucfpksywv.cloudfront.net/better-language-models/language_models_are_unsupervised_multitask_learners.pdf).

[2] Isola, P., Zhu, J-Y., Zhou, T., Efros, A.A. (2017). Image-to-Image Translation with Conditional Adversarial Nets. _Proceedings of Conference on Computer Vision and Pattern Recognition (CVPR)_.

[3] Cao, Z., Hidalgo, G., Simon, T., Wei, S-E., and Sheikh, Y. (2018). OpenPose: Realtime Multi-Person 2D Pose Estimation using Part Affinity Fields. _arXiv_, 1812.08008.

[4] Raghu, M., Zhang, C., Kleinberg, J.M., and Bengio, S. (2019). Transfusion: Understanding Transfer Learning for Medical Imaging. _arXiv_, 1902.07208.

[5] Antolovic, V., Lenn, T., Miermont, A., Chubb, J.R. (2019). Transition state dynamics during a stochastic fate choice. _Development_, 146, dev173740. doi:10.1242/dev.173740.

[6] Goldenfeld, N. and Woese, C. (2011). Life is Physics: Evolution as a Collective Phenomenon Far From Equilibrium. _Annual Review of Condensed Matter Physics_, 2, 375-399. doi:10.1146/annurev-conmatphys-062910-140509.

[7] Stone, R., Portegys, T., Mikhailovsky, G., and Alicea, B. (2018). Origins of the Embryo: Self-organization through cybernetic regulation. _Biosystems_, 173, 73-82. doi:10.1016/j.biosystems.2018.08.005.

[8] Portegys, T., Pascualy, G., Gordon, R., McGrew, S., and Alicea, B. (2016). Morphozoic: cellular automata with nested neighborhoods as a metamorphic representation of morphogenesis. In “Multi-Agent Based Simulations Applied to Biological and Environmental Systems“. Chapter 3 in "Multi-Agent-Based Simulations Applied to Biological and Environmental Systems", IGI Global.

[9] Garnelo, M. and Shanahan, M. (2019). Reconciling deep learning with symbolic artiﬁcial intelligence: representing objects and relations. _Current Opinion in Behavioral Sciences_, 29, 17–23.

[10] Zador, A.M. (2019). A critique of pure learning and what artificial neural networks can learn from animal brains. _Nature Communications_, 10, 3770.

[11] Brooks, R.A. (1991). Intelligence without representation. _Artificial Intelligence_, 47, 139–159.

[12] Marcus, G. (2018). Innateness, AlphaZero, and Artificial Intelligence. _arXiv_, 1801.05667.


<strong>Resources:</strong>

* Model Zoo: pre-trained models for various platforms: [https://modelzoo.co/](https://modelzoo.co)

* DevoZoo: developmental data for model training and analysis: [https://devoworm.github.io/](https://devoworm.github.io)

* Publicly available Medical Image datasets: [https://medical-imaging-datasets and open-access-medical-imaging-datasets"](https://medical-imaging-datasets and open-access-medical-imaging-datasets)

* Popular papers on medical image segmentation along with code: [https://paperswithcode.com/area/medical/medical-image-segmentation](https://paperswithcode.com/area/medical/medical-image-segmentation)

* Microscopy specific image datasets: [http://www.cellimagelibrary.org/pages/datasets](http://www.cellimagelibrary.org/pages/datasets) and [https://idr.openmicroscopy.org](https://idr.openmicroscopy.org)
