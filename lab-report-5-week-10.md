# **WEEK 10 Lab Report**
## Tests examples from the 652 commonmark-spec tests 
***
- ### ***2 Tests getting different results from my implementation and lab 9 implementation***

    ### How I found the testing difference 


    *I saved the my implementation and Lab 9 directory's running results of ```bash script.sh```  in the files ```results.txt``` respectively in their own folders. Then, I copied both files and compared them manually and find out 2 tests that have different results.*

    ### *1st Test*: 

    File name: ```22.md```

    File content: 
    ```
        [foo](/bar\* "ti\*tle")


    ```
    Running result of mine:

    ![Image](Test22My.png)

    Running result of Lab 9 repository 

    ![Image](test22Lab9.png)

    ***

    ### *2nd Test*:
    
    File name: ```194.md```

    File content: 
    ```
        [Foo*bar\]]:my_(url) 'title (with parens)'

        [Foo*bar\]]


    ```
    Running result of mine: 

    ![Image](test194My.png)

    Running result of Lab 9 repository

    ![Image](test194Lab9.png)

***

- ### ***Problems of both implementations and potewntial ways to fix them***

    ### Problem in the 1st Test (both test results are shown above in the images)



    ```
            else {
                toReturn.add(markdown.substring(openParen + 1, closeParen));
                currentIndex = closeParen + 1;
            }
    ```
    
    
    *I believe that my implementation in the ```MarkdownParse.java``` should be wrong for this test. The mistaken part is shown above. As we can see, my current implmentation does not eliminate the strings that contains ```" "``` sign, which is why testing result went wrong.*

    *My testing result returns a "link" that contains a ```" "``` sign (a space in the link), which should not exist in URLs. To fix that issue, I will add a new if statement to make sure that only when the string we get between parentheses contains no ```" "``` sign, the potential "link" string can be added to the returning result.*


    ***

    ### Problem in the 2nd Test (both test results are shown above in the images)


    ```
            if (!markdown.substring(openParen - 1, openParen).equals("]")) {
                currentIndex = closeParen + 1;
                continue;
            }
    ```
    
    *For this test, I believe that my implementation is also wrong. The mistaken part is shown abov. As we can see, my implementation will skip the whole contents in between the parentheses when the character right in front of the open parenthese is not a close bracket. In that case, the program will simply skip the URL in this test file and lead to wrong output.*

    *To fix that, I think I need to change the if statement from current form to checking whether there is a pair of complete bracket in front of the open paren. In that case, it will not skip the URL that easy.*









