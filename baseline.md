# W207 - Baseline Submission

#### Kathryn Hamilton & Frank Shannon

## Problem

The team would like to assess the relationship between the synopsis of a novel and its success by constructing a classifier.

The synopsis of a novel, a couple paragraphs of text found on the back or inside cover of a novel, provide a brief explanation of the book's genre and contents, and often some critical acclaim of the the author if applicable. The team would like to see if this information can be used to reliably predict whether or not the novel will be successful.

## Data Source

The data we will be using for this project come from two sources.

The first is an online repository of `.json` files compiled by Julian McAuley, Assistant Professor of Computer Science and Engineering at University of California, San Diego. These files, which can be found at `http://jmcauley.ucsd.edu/data/amazon/` will provides us with customer review information and product metadata

An example of a customer review entry is as follows:

    {
      "reviewerID": "A2SUAM1J3GNN3B",
      "asin": "0000013714",
      "reviewerName": "J. McDonald",
      "helpful": [2, 3],
      "reviewText": "I bought this for my husband who plays the piano.  He is having a wonderful time playing these old hymns.  The music  is at times hard to read because we think the book was published for singing from more than playing from.  Great purchase though!",
      "overall": 5.0,
      "summary": "Heavenly Highway Hymns",
      "unixReviewTime": 1252800000,
      "reviewTime": "09 13, 2009"
    }
    
 An example of a product metadata entry is as follows:
 
     {
      "asin": "0000031852",
      "title": "Girls Ballet Tutu Zebra Hot Pink",
      "price": 3.17,
      "imUrl": "http://ecx.images-amazon.com/images/I/51fAmVkTbyL._SY300_.jpg",
      "related":
      {
        "also_bought": ["B00JHONN1S", "B002BZX8Z6", "B00D2K1M3O", "0000031909", "B00613WDTQ", "B00D0WDS9A", "B00D0GCI8S", "0000031895", "B003AVKOP2", "B003AVEU6G", "B003IEDM9Q", "B002R0FA24", "B00D23MC6W", "B00D2K0PA0", "B00538F5OK", "B00CEV86I6", "B002R0FABA", "B00D10CLVW", "B003AVNY6I", "B002GZGI4E", "B001T9NUFS", "B002R0F7FE", "B00E1YRI4C", "B008UBQZKU", "B00D103F8U", "B007R2RM8W"],
        "also_viewed": ["B002BZX8Z6", "B00JHONN1S", "B008F0SU0Y", "B00D23MC6W", "B00AFDOPDA", "B00E1YRI4C", "B002GZGI4E", "B003AVKOP2", "B00D9C1WBM", "B00CEV8366", "B00CEUX0D8", "B0079ME3KU", "B00CEUWY8K", "B004FOEEHC", "0000031895", "B00BC4GY9Y", "B003XRKA7A", "B00GOR92SO", "B007ZN5Y56", "B00AL2569W", "B00B608000", "B008F0SMUC", "B00BFXLZ8M"],
        "bought_together": ["B002BZX8Z6"]
      },
      "salesRank": {"Toys & Games": 211836},
      "brand": "Coxlures",
      "categories": [["Sports & Outdoors", "Other Sports", "Dance"]]
    }
    
The team will then use an API to scrape novel synopsis information from Amazon.com using the list of product ID numbers included in the dataset of reviews.

## Outline of Approach

The team will use a variety of preprocessing techniques and a vectorizer to decompose the synopses and ratings. Then, the team must operationalize the definition of "success" as it pertains to the novels. This will be done using a combination of overall star rating, which on Amazon.com is 1-5, and an approximation of revenue, given by the price of the object and the number of reviews, which we assume to be proportional to the number of purchases. As this is a large assumption, the team will try to provide justification for it or find additional data to support or replace it. 

A preliminary table of variables is described below.

| Variable | Source and Description |
| --- | ---|
| X | book description, pulled from Amazon.com with API |
| Y1 | rating text (sentiment), from UCSD dataset |
| Y2 | star rating, from UCSD dataset |
| Y3 | revenue? (price x ranking?), from UCSD dataset |

Once the data has been collected and cleaned, the team will then select a supervised learning algorithm best suited to classify synopsis by level of success. The trained classifier can then (hopefully) be used to predict success of new novels based off of the information included in the synopsis.
