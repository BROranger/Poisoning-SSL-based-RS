### Poisoned_datasets
Poisoning data generated by our scheme.

For each dataset, we generated fake users whose numbers are 1%, 2%, and 3% of real users.

It is worth noting that, in the three original *Amazon* datasets (*Beauty*, *Sports and Outdoors*, and *Toys and Games*), none of the users has multiple interactions with the same item, while in the *Yelp* dataset, users often interact with the same item multiple times.
Therefore, to ensure the stealthiness of our attack, when constructing the poisoning data of the *Amazon* datasets, we let each fake user only interact with the target item once, while in *Yelp*, we allow each fake user to interact with the target item multiple times.
For comparison, we also provide the poisoning data of the *Yelp* dataset where each user interacts with the same item at most once.

### Seq-poison
Our model for fake user generating.

#### datasets
Original pre-processed user-item interaction records obtained by the data downloaded from [Google Drive](https://drive.google.com/drive/folders/1ahiLmzU7cGRPXf5qGMqtAChte2eYp9gI) (which is publicly available). 

We use the “5-core” datasets as described in our paper.

#### Run
Create bi-classifier:
  
```
python train_classify.py
```

Now we get the bi-classifier model *{data_name}_bi_classify.pt*.

Train the generator that generates fake users:

```
python main.py
```

Generate poisoning data (the percentage of fake users can be set)：

```
python generate_data.py
```

