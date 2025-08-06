# Transformer_Based_Title_Generation

This project focuses on building and evaluating models for automatic book title generation based on book descriptions. It is divided into three main parts — from raw text extraction and preparation to model training, fine-tuning and evaluation.

Generating meaningful and creative titles from descriptions is a particularly challenging task in natural language processing. Unlike summaries or classifications, titles are often abstract, metaphorical or intentionally ambiguous and they don’t always offer a direct reflection of the book’s content. While descriptions provide clear insight into the storyline or subject matter, titles may be poetic, symbolic or chosen for marketing appeal, making them hard to predict from a purely semantic or structural standpoint.

In addition to the inherent difficulty of the task, this project is further constrained by the limited size of the dataset. A small corpus increases the risk of overfitting and reduces the model’s ability to generalize. To counter this, careful preprocessing and data augmentation techniques are applied to enhance the dataset and improve training outcomes.

By combining practical data handling with advanced transformer-based models, the project explores how far we can push automated title generation under real-world constraints.

Part 1: Data Collection and Preparation
In the first stage, book data is collected through web scraping from an online bookstore (books.toscrape.com is a demo website for web scraping purposes). This includes titles, descriptions, star ratings and prices. Since the raw dataset is relatively small, two data augmentation techniques are applied to improve model generalization:
Backtranslation: English descriptions are translated into German and then back into English to generate semantically equivalent but syntactically varied text.
Paraphrasing: A T5-based paraphraser generates alternative versions of descriptions while preserving the original meaning.
This step ensures that the training data is diverse and suitable for fine-tuning language models.

Part 2: Transformer Model for Title Generation
The second part involves building a custom transformer-based model that generates book titles from descriptions. This includes:
Byte-Pair Encoding (BPE) for effective tokenization of input/output text.
Hyperparameter optimization using Optuna, guided by the ROUGE score as the evaluation metric.
The goal is to learn an end-to-end mapping from description to title.

Part 3: Fine-Tuning a Pretrained T5 Model
In the final part, a pretrained T5 model is fine-tuned on the same description-to-title task. By leveraging the model's pretrained language understanding, we aim to improve performance on title generation, especially with limited training data. This step serves as a benchmark against the custom transformer developed in Part 2.
