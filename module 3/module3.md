# Fail-log Module 3

## Exercise One - Regex

### Step 1 
* I am having a lot of trouble with this exercise. I have been trying this for over two hours, and simply can not manage to get things right.
	* I am pasting the curl command into my Command Line
		* curl http://archive.org/stream/diplomaticcorre33statgoog/diplomaticcorre33statgoog_djvu.txt > texas.txt
	* I am opening the texas.txt file using nano
	* I am trying to delete everything except for the correspondance, using ctrl + shift + 6, and using ctl + k to cut the data
	* I am saving and exiting the file.
	* Then, I type "grep '\bto\b' texas.txt" in the command line
	* Paste the text from texas.txt into RegExr
	* Played with the formula
	* Paste the following into the command line
		* sed -r -i.bak 's/(.+\bto\b.+)/~\1/g' texas.txt
	* Try to open texas.txt using nano
* My problem, after having completed this exact routine about 4 times (deleting my texas.txt file and restarting with the saved backup) is that whenever I open texas.txt, it seems to simply be the same file (a bunch of html text), rather than the neat list of correspondances with ~ at the beginning of each line, that I see in the course video!

DAY TWO

* After a long scroll through the file, I am realizing that there are actually lines with ~ before them *in* the texas.txt file
* My problem was that I had missed the step of exporting texas.txt as a file, opening it with a text editor on my desktop, deleting the unecessary lines, then reuploading the new texas.txt. I have no clue why I kept missing this step. (Getting started, #3)
* I downloaded the texas.txt file to my desktop, opened it with a text editor, deleted the unnecessary lines both at the top and bottom of the document, then re-uploaded to DHBox.
* Because I had already run the following command
	* sed -r -i.bak 's/(.+\bto\b.+)/~\1/g' texas.txt
* There were already tidles at the beginning of all my files once I inspected it using nano.
* I (finally) succesfully created a file containing a list of correspondances, with tildes at the beginning of them. 

### Step 2
* I copy and pasted the following command into the Command Line to move all lines that do *not* start with a tilde to another document.
	* grep '~' texas.txt > index.txt

### Step 3
* To be completely honest, I scrolled to the bottom of the file to copy this function as I tried to re-read the RegX introduction to try and come up with my own formula, at no avail.
* I pasted "sed -r -i.bak 's/(,)( [0-9]{4})(.+)/\2/g' index.txt" in the command line.
* I understand "s/" and "g/" (switch generally)
* It is the formula in between that is quite confusing. Perhaps working late at night is not ideal for this.

### Step 4
* For this step, I know that 
	* s/ means " switch" and /g means "globally", so whatever happens in between these two entries entails switching one word for another in the file
	* s/*something*/*something*/g will switch out one for the other
	* s/~//g, where I leave the space after "/" blank, means that ~ will be replaced by nothing, or deleted
* I try this command in RegX, and it seems to be working
* My problem is with copying this command into the command line. 
* I try
	* "sed -r -i.bak s/~//g index.txt", which doesn't work.
	* At this point, I scroll to the bottom of the file and realise that the formula is placed in between apostrophes, as follows:
	* "sed -r -i.bak 's/~//g index/txt"

Note: In absolute honesty, I can not recall the reason why this formula had to be placed in between apostrophes. However, doing this made it work. Looking through the document again, I am realising that most formulas are actual 'presented as such'.

### Step 5
The goal of this step is to replace "to" with a comma. I am trying to do this without relying on the formulas made available at the bottom of the workbook.
Here are notes of my thinking:

* s/ and /g will switch things globally
* s/ *here, I am looking to switch "to" to ","* /g
* s/to\, /g - this is an extremely plain way of doing it. Howver, it will not work because I need to isolate the word "to".
* s/\b to\b/,/g - in English, would read as "Switch "to" to "," globally", so I think I am getting close.
* I run the command on RegX, and it doesn't replace all of the to's, and the command just doesn't seem to be working.
* I restart the exercise.

TRY TWO
* I am convinced that these parts of my attempts are correct:
        * s/\b to\b/,/g 
* However, upon close reading of the workbook ("We include the space preceding âtoâ in the regular expression, as well as the \b to denote the word ending."), I notice that I did not add a space after "to" to "denote the word ending".
* My new formula is as follows: "s/\b to \b/,/g"
* I run it through RegX, and it stil doesn't work.
* I compare my formula to the class formula, and notice that I need parentheses to make this work. At this point, I simply crely on the command provided in the workbook to complete the exercise.

My command:
* s/\b to \b/,g

The actual command.
* 's/(\b to \b)/,/g'

What I type into the Command Line:
* sed -r -i.bak 's/(\b to \b)/,/g' index.txt
 
### Step 6
* For this step, I simply copy the command from the workbook into the command line:
* "grep -r ".+,.+,.+," index.txt"
* And then create a csv file using "cp index.txt cleaned-correspondence.csv"
* I download this to my desktop.

### Exercise Two - Open Refine

I am realising that OpenRefine is basically a more accessible version of all of the exercises we have been doing in Module 2 and 3. Using the command line was a way of understanding the background workings of this tool. Somewhat like learning a new language - you can learn 20 words by heart, but might not know how to put them together well. It is only by learning grammar that you can actually manage to build your own sentences, little by litte. Here's what I did this time around:

##Steps 1 & 2
* I succesfully managed to download OpenRefine. 
* I then uploaded my cleaned texas.txt file
* I selected facet -> text facet for both the sender and recepient colums in order to have the opportunity to cluster them
* I began looking at clusters of similar names, and selecting "merge"
* At first, I seemed to only be able to merge my 192 senders to about 175 entries, although the workbook target was 160
* I found that using the "nearest neighbor" method with the "levenshtein" distance function, and playing with the Radius (switching from 1.0 to 2.0, 3.0, etc) rather than the Block Chars allowed me to find the last bits of data clusters to merge.
* In total, I used this method to clean my file and have 148 senders, and 162 recipients.
* I saved the csv file, and also saved the two-column (source -> target) .csv file, which I then uploaded to my DH Box

Notes: I am noticing that a few lines here and there (not plenty) are missing dates. This may be due to a mistake I made during a previous exercise while manipulating the texas.txt file, or maybe it is just because there is no data for that entry.