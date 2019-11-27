# Assignment 4. Data Integration

*Due 12/5/19 11:59 PM*

Entity Resolution is the task of disambiguating manifestations of real world entities in various records or mentions by linking and grouping. For example, there could be different ways of addressing the same person in text, different addresses for businesses, or photos of a particular object. In this assignment, you will link two product catalogs. Like the last assignment it will be up to you to determine how exactly to perform the linking.

## Getting Started
First, download the starter files from:
```
https://github.com/sjyk/cmsc21800/blob/master/assignment4.zip
```
Your code will go into `analzye.py`. You will also need to fetch the datasets used in this homework assignment:
```
https://www.dropbox.com/s/vq5dyl5hwfhbw98/Amazon.csv?dl=0
https://www.dropbox.com/s/fbys7cqnbl3ch1s/Amzon_GoogleProducts_perfectMapping.csv?dl=0
https://www.dropbox.com/s/o6rqmscmv38rn1v/GoogleProducts.csv?dl=0
```
Download each of the files and put it into your assignment folder.

Before we can get started, let us understand the main APIs in this project. We have provided a file named `core.py` for you. This file loads and processes the data that you've just downloaded. For example, you can load the Amazon catalog with the `amazon_catalog()` function. This returns an iterator over data tuples in the Amazon catalog. The fields are id, title, description, mfg (manufacturer), and price if any:
```
>>>for a in amazon_catalog():
...  print(a)
...  break

{'id': 'b000jz4hqo', 'title': 'clickart 950 000 - premier image pack (dvd-rom)', 'description': '', 'mfg': 'broderbund', 'price': '0'}
```
You can similarly, do the same for the Google catalog:
```
>>>for a in google_catalog():
...  print(a)
...  break

{'id': 'http://www.google.com/base/feeds/snippets/11125907881740407428', 'title': 'learning quickbooks 2007', 'description': 'learning quickbooks 2007', 'mfg': 'intuit', 'price': '38.99'}
```
A matching is a pairing between id's in the Google catalog and the Amazon catalog that refer to the same product. The ground truth is listed in the file `Amzon_GoogleProducts_perfectMapping.csv`. Your job is to construct a list of pairs (or iterator of pairs) of `(amazon.id, google.id)`. These matchings can be evaluated for accuracy using the `eval_matching` function:
```
>>> my_matching = [('b000jz4hqo', http://www.google.com/base/feeds/snippets/11125907881740407428'),...]
>>> {'false positive': 0.9768566493955095, 'false negative': 0.43351268255188313, 'accuracy': 0.04446992095577143}
```
False positive refers to the false positive rate, false negative refers to the false negative rate, and accuracy refers to the overall accuracy.

## Assignment
Your job is write the `match` function in `analzye.py`. You can use as many helper functions and classes as you want. You can run your code by running:
```
python3 analyze.py
```
Running the code will print out a result report as follows:
```
----Accuracy----
{'false positive': 0.690576652601969, 'false negative': 0.4926979246733282, 'accuracy': 0.38439138031450204}
---- Timing ----
114.487954 seconds

```
*For full extra credit, you must write a program that achieves at least 35% accuracy in less than 3 mins on a standard laptop.*

## Submission
After you finish the assignment zip up all of your .py files and email them to (please exclude the data files from the zip because they will be hard to download):
```
skr@cs.uchicago.edu
```
