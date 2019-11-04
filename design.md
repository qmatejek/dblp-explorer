My program solves the problem by reading in the file line by line using a BufferedReader, then it passes each line to a method that uses 
the json parser Jackson to parse the line and find any lines that have titles that contain the keyword. It then returns the list of 
references for those titles. These are tier 1 papers. The program then passes the list of those references to getRefs which finds all the
references of a list of references and returns them in a list. This function is used to get tier 2 - tier n papers. Finally, the two lists
of reference id's (tier 1 and tier 2-n) are passed to a function called refSearch that takes in a list of reference id's and returns their
titles and id's.

The way this is done somewhat efficiently is that the lists are sorted before they are passed into getRefs and refSearch. This makes it 
where I only need to make a single pass through the file to get ALL the info I need, instead of having to go over the json file once
for every item that needed to be found (titles, id's, references).

Doing it this way, I was able to avoid loading too many things into memory.
