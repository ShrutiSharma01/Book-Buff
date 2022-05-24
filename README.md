### Objective ✍
The objective is to build an application for all Book Lovers 📖 like us out there where all you have to 
do is rate ⭐ some of your favorite books and the application will do it's **magic** 🧙‍♂️ and give you some more books that you may **love to read**.

### Preview 👀
![2](https://user-images.githubusercontent.com/81433585/170096087-dc45dfea-c2ae-4377-a317-16098f178501.PNG)

![3](https://user-images.githubusercontent.com/81433585/170096111-f2a69419-c19b-4c41-a39a-4ef722979ad3.PNG)

### Dataset 🧾
The Dataset used for this task is the [goodbooks-10k](https://github.com/zygmuntz/goodbooks-10k) dataset. It consists of 10k books with a total of 6 million ratings.

**Dataset Structure** 
```
GoodBooks10k 
    ├── books.csv         # Contains book info with book-id                         
    ├── ratings.csv       # Maps user-id to book-id and rating  
    ├── book_tags.csv     # Contains tag-id associated with book-ids
    ├── tags.csv          # Contains tag-name associated with tag-id
    ├── to_read.csv       # Contains book-ids marked as to-read by user  
```

### PreProcessing 🛠
Since this is a recommendation problem, we have to make sure that the `books.csv` is as clean as possible and only consider those ratings whose book-id is present, same goes for vice versa.

More Cleaning for `books.csv`
- Missing Book Image URLs
- Book & Rating Duplicates

### Model Exploration 🤯
For Recommendation Problems there are multiple approaches that are possible:
- Embedding Matrix
- Singular Matrix Decomposition
- Term Frequency

Embedding Matrix & Term Frequency methods were chosen:

- **Embedding Matrix** - This Embedding Matrix constructs a vector for each user and each book, such that when the product is applied with additional constraints it gives us the rating. Book embedding is used as a representation of the books to infer underlying patterns. This led to the embedding able to detect books from the same authors and also infer genres such as Fiction, Autobiography and more.

- **Term Frequency** - This method is like a helper function to above, it shines where embedding fails. Term Frequency takes into account the tokens in a book title be it the book title itself, the name of authors and also rating. Taking into consideration it finds books which match closely with the tokens in the rated book.
