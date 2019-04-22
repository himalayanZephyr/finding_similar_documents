Implementation the pipeline for finding simliar documents, as given in the book *Mining of Massive Datasets* (Jure Leskovec, Anand Rajaraman, and Jeffrey David Ullman.Mining of massive datasets. Cambridgeuniversity press, 2014).

The implementation is shown on a set of 8 documents containing reviews of products and accommodations.

### Dataset
The dataset used is [UCI Opinions Dataset](https://archive.ics.uci.edu/ml/machine-learning-databases/opinion/). This dataset contains 51 documents, of which a subset of 8 documents as our test set was selected. The average word count for each document in the test set is approximately 1142. Each file contains a number of reviews for a product.

### Implementation
* Shingles of size 5 for each document were generated. All the words were converted to lowercase and the spaces were replaced with underscores.
* A boolean matrix was created where a column represents boolean vector of shingles, of each document, in the complete space of all the shingles.
* Using the boolean matrix Jaccard similarity of each pair of documents was computed.
* Jaccard similarity threshold of _0.25_ was chosen(trial and error method). The range of similarities between the documents in the test set was 0.094 to 0.266.
* In order to generate Signature matrix, 100 hash functions of the form *{(ax+b) mod n}* were used, with different values of a and b.
* The signature matrix of size 100 (hash functions) x 8 (docs) was initialized to infinity value at each cell.
* The minhashing algorithm was implemented to generate a signature matrix. 
* A Minhash similarity of _0.25_ was chosen to see similar documents.
* In order to implement LSH, a threshold of 0.25 was chosen which approximately led to b=34 and r=3. The documents that were hashed into same bucket, were compared using the Minhash similarity defined before.

### Results

##### Matrix representation of documents
![Matrix representation of documents](/imgs/1.png)

##### Signature Matrix for MinHashing
![Signature Matrix for MinHashing](/imgs/2.png)

##### Results of LSH
![Results of LSH](/imgs/3.png)
