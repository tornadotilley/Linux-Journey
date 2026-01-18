`tail` displays the last ten lines of a file by default. 

`[ttilley@somelinux ~]$ tail sometext.txt`

By default, this will have an output of the last ten lines of the .txt file. To modify this, we will use the `-n` flag for this command.

`[ttilley@somelinux ~]$ tail -n 4 sometext.txt`

The output will be the last four lines of the text file. 


It is also possible to use 'tail' in a pipeline with '[[head]]'. It is written like this:

`[ttilley@somelinux ~]$ head -n -5 text_header_footer.txt | tail -n +5 > text.txt` 

This pipeline will give us an excerpt from the file that is ten lines long. 

### Flags 

- `-f` - let's tail keep updating the contents of a file in real time
	- *This can be ended with CTRL+C* 



