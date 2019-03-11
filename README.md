# Positional-Inverted-Index
The design I used for the positional inverted index is very straightforward. I used a dictionary to hold the entire inverted index, with keys are unique words in a set of documents, and values are dictionaries that hold documents and the assosiated positiona each word in that document. 

Specifically, I first retrieved the directory path from user’s input, and read files from the target directory. Then I split the words as required, converted all input words to lower case, removed punctuation, numbers, symbols and stopwords. Then I created a function that creates dictionary with word as key, and a list of positions in the files as value for a single file, then
another function will loop through all the files and generate the final inverted index. The inverted index will be saved to a json file called inverted_index.json.

Boolean Search:

It supports partial Boolean search (AND & OR), and no parentheses. AND operations always come before OR operations. The return results would be documents that satisfies condition specified, and each document contains the position for words appear in that document. Specifically, I first load the inverted index from the json file, then get query input from the user input, and conduct Boolean search on the inverted index based on the query. I split the Boolean search into a few situations, like single keyword search, the query that contains only AND, the query that contains only OR, the query that contains only keywords, the query that contains a combination of AND and OR. The output of the query will be printed to screen.

Inverted Index using MapReduce:


I created an inverted index using MapReduce. The process is split into two steps: Mapper and Reducer. For Mapper, the input (key,value) pairs are (docID, lines of that doc), and the output (key, value) pairs are (word, docID). And before output the results, I did convert all input words to lower case, remove punctuation, numbers, symbols and stopwords. The output pairs from the Mapper got sorted by key (word in this case) before passed to Reducer. The pairs with the same key will be sent to the same Reducer, and there will be multiple Reducers working on the input (word, docID) pairs. The Reducer in my design is doing aggregating for each unique word, it generates a list of docs for each word appears in the docs and associates the list with that word. The output from Reducer would be files with format of word: a list of docs. Then I merged files using the getmerge command.


Boolean search:
I used sftp get command to load the output file from the Virtual Machine to my local machine for Boolean search. First, I converted the content from the output file to a dictionary with keys are unique words and values are lists of docID associated with that word. Then I performed Boolean search similar to what I did in the part 2, but this time the output will not contain positions. The output of the query will be displayed on screen.

 
