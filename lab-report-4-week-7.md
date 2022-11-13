# Part 1

#### The task that I chose was: Changing the **start** parameter to **base**

The commands that my group came up with were:

``/start <enter>``

![image1](start.png)

This step uses /value to search for a sequence of characters in the file.
Then it sends you to the first character of the first found sequence

``c``
``e``

![image2](ce.png)

**ce** deletes the current word, then allows us to edit

``base``

![image3](base.png)

Then we replace the deleted word with **base**

``<Esc>``
``n``

![image4](esc_n.png)

Then **escape** sends us back into normal mode
We can then use **n** to find the next instance of the sequence that we are searching for

``.``

![image5](dot.png)

**.** stores the commands we used to edit the previous instance of start
When we use **.** it performs those commands in the same order

``n``

![image6](n2.png)

We then search for the last instance

``.``

![image7](dot2.png)

We repeat the commands with **.**

``:wq``

Then we save and quit.



