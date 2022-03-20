# sed
![image](https://user-images.githubusercontent.com/38063689/159167476-41d6385b-a4d9-41eb-9e67-e91f2a0acde2.png)
https://coach.sgdigital.com/#/online-courses/45d5a588-e3fe-445f-afbc-adf533ec223e


```
sed -i 's/old-text/new-text/g' input. ...
```


## Removing ANSI color codes from text stream
`sed 's/\x1b\[[0-9;]*m//g'`
- \x1b (or \x1B) is the escape special character (sed does not support alternatives \e and \033)
- \[ is the second character of the escape sequence
- [0-9;]* is the color value(s) regex
- m is the last character of the escape sequence

From <https://superuser.com/questions/380772/removing-ansi-color-codes-from-text-stream> 



# find
Find all the files under the current tree that have the .js extension and print the relative path of each file that matches:
```
find . -name '*.js'
```

Find directories under the current tree matching the name "src":
-type f to search only files
-type l to only search symbolic links
```
find . -type f -name test.txt
find . -type d -name src
```

You can search under multiple root trees:
```
find folder1 folder2 -name filename.txt
```

Find directories under the current tree matching the name "node_modules" or 'public':
```
find . -type d -name node_modules -or -name public
```

You can also exclude a path using -not -path:
```
find . -type d -name '*.md' -not -path 'node_modules/*'
```


# vim
Command Mode:
Description | Shortcut
--- | ---
Copy current line | yy
Paste line after/before current line | p/P
Delete current line | dd
Navigate up/down | j/k
Navigate left/right | h/l
Undo | u
Jump to first line | gg, J 
Jump to last line | G, L
Insert, cursor to begin of line | I
Insert, cursor before character | i (doesn't move)
Insert, cursor to end of line | A
Insert, cursor after character | a
. | .
See line numbers | :set number
Paste Modus | :set paste  <br>:set nopaste

## Deleting Words in Vim
1. Use dw to delete word. Cursor placement is important! ...
2. Use diw to delete inside word. Deletes the entire word that your cursor resides in.
3. Use dt<char> to delete to character. Deletes from your cursor to the specified character.

From <https://www.google.com/search?client=opera&q=vi+remove+word&sourceid=opera&ie=UTF-8&oe=UTF-8> 
  
  
## Find and Replace in Vim / Vi
From <https://linuxize.com/post/vim-find-replace/> 
  
## Cheatsheet
https://web.archive.org/web/20161221161539/http://bullium.com/support/vim.html#move
  
  
## Layout
https://hamwaves.com/vim.tutorial/en/index.html
![image](https://user-images.githubusercontent.com/38063689/159168008-be93cf56-a4b9-4feb-ae86-2b9e4033ff3e.png)


# Iterate over files in dir
And append the content into another one
```
>> = append
>  = overwrite 
```

```
for file in *MktTemplates.sql; do cat "$file" >> 1_Bwin_MktTemplates.sql; done
```
  
# tar
- compress `tar -czvf folder.tar.gz <folder>`
- uncompress `tar -xzvf folder.tar.gz`

# Remove duplicate lines from a text file
The uniq command is used to remove duplicate lines from a text file in Linux. By default, this command discards all but the first of adjacent repeated lines, so that no output lines are repeated. Optionally, it can instead only print duplicate lines. For uniq to work, you must first sort the output.

From <https://geek-university.com/linux/remove-duplicate-lines-from-a-text-file/> 

```
sort file.txt | uniq
```

To display only duplicate lines, use the -d option:
```
sort file.txt | uniq -d
```
  
# Permissions
In the form `trwxrwxrwx`. First character is the type of the entry: 
- `-` for a file 
- `d` for a directory 
- `I` for a symbolic link 

Next three groups list the permissions for the `owner`, the `owners group`, and `all users`. 
- `r` assigns read permission
- `w` assigns write permission 
- `x` assigns execute permission 
- `A` in any position denies that permission
  
Each permission within a permission group is assigned a binary representation. 
- 4 for read
- 2 for write
- 1 for execute
  
These are summed to give the permission for the group. Examples: 
- `rwx` is 4 + 2 + 1 = 7
- `rw-` is 6
- `r-x` is 5
   
All the individual group permissions are strung together to give an overall permission: 
- `-rw-rw-r--` has a binary permission of 664 
- `-rwxr-xr-x` has a binary permission of 755 
  
  
# Add directory to PATH
```
# pip3 show locust (displays the path)

# adding the locust framework
if [ -d "$HOME/.local/lib/python3.6/site-packages/locust" ] ; then
    PATH="$HOME/.local/lib/python3.6/site-packages/locust:$PATH"
fi
```
  

# tree (for Windows)
> I have downloaded the tree.exe inside the zip file from here http://gnuwin32.sourceforge.net/packages/tree.htm as suggested.
> Then I have extracted the tree.exe file to C:\Program Files\Git\usr\bin 
> (I have added this folder to windows path to make it work with the regular CMD but it works with GITBash too).

From <https://superuser.com/questions/531592/how-do-i-add-the-tree-command-to-git-bash-on-windows> 

Download (binaries)
http://gnuwin32.sourceforge.net/packages/tree.htm
  
