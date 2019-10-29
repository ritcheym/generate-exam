# generate-exam
R markdown for generating a formatted exam from a csv of questions

This repository shows an example of an R markdown script (**exam.Rmd**) that reads in a csv file of exam questions and turns it into a formatted exam. By using the `knitr` functions implemented in RStudio, you can easily knit the Rmd file into html, markdown, or Word documents. The script includes functions for randomizing question order and multiple choice options, making it easy to create different exam versions.

# How to use
1. Download **exam.Rmd**. 
2. Generate a csv file with your exam questions. The repository includes an example: **examquestions.csv**
 - You can include as many columns as you want for various types of meta-data, but the fields that you absolutely need to run the script are: `Question`, `Type`, `Points`, `CorrectAnswer`. 
3. There are formats defined for the following question types: `multiple-choice`,`T/F`,`short-answer`,`long-answer`, and `image-labels`.
 - For the `multiple-choice` type, you will additionally need to define `Lure1`, `Lure2`, and `Lure3`. These will be presented along with the correct answer in a random order.
 - For the `image-labels` type, you will additionally need to define `Image`, which will be the filename of the image you want to present.
 - Need another format? Add a function to the `defineFormats` chunk, and include it as an option in the if-statement in `presentQuestions` chunk.
4. Edit the exam information in the YAML header. 
5. Edit the instructions after the `loadQuestions` chunk.
6. Seed your `seedNum` - an arbitrary number that will be used to reset the randomization. This will let you reproducibly generate different versions of the exam.
7. You can additionally edit the `dplyr` code in the `loadQuestions` chunk to sort your questions by whatever variable you want (in the example, `Week`), or to filter them according to other variables that you've included in your csv file.
8. Knit the **exam.Rmd** file to whatever format you wish.
  - Important note: R markdown does not like to preserve large patches of white-space. So I would recommend knitting to Word doc format, then going through the file to add the appropriate amount of space after each short- or long-answer question. If anyone comes up with a better fix, let me know (inserting multiple `\n` calls doesn't work).

# Output

After knitting, you will have an **exam.doc** or **exam.html** file. See **exam_output.md** for an example of the formatted output. 

The script also generates a csv file that contains your exam key. See **examquestions_withkey_v123.csv** for an example key. The key will be labeled with your seed version number.

Happy teaching!

Author: Maureen Ritchey, February 2017
