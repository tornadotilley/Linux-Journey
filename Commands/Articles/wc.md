`wc` stands for wordcount. In the default state, without any arguments, it will only count the lines of the file. 

`[ttilley@somelinux ~]$ wc`

If we use it in a pipeline, it would look something like this:

`[ttilley@somelinux ~]$ la /bin /usr/bin | sort | uniq | wc`


These are some of the optional flags that can be used:

- `-l` - limits the output to only lines
- 