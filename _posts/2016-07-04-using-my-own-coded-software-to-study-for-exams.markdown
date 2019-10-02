---
title: Using my own coded software to study for Exams
date: 2016-07-04 20:25:48 Z
categories:
- JavaScript
- Six weeks training
author: ranvirsingh1114
comments: true
layout: post
link: https://ranvirsinghprojects.wordpress.com/2016/07/05/using-my-own-coded-software-to-study-for-exams/
wordpress_id: 261
---

Some time ago sir hosted a hackathon to make some progress to enhance the ebook software that he was using on his website. Everyone was given a specific task on that day. My task was to read the script and make some changes in the script. But some reason we had to drop that idea. So I decided to start building something new instead.




I wrote some code and was able to create a replica of the software( Although It was not as great as that software). The code of the software can be found [here.](https://github.com/singh1114/ebook)




Due to dropping of the idea the task become much more complex and we are still figuring it out. But I showed the new code written by me to sir and sir asked me to test it for the books of my choice. I was not able to test it because I don't read much books unless it is very important (although I love to read books).




So, the time came when it become very important to read as it was the Exam time. I was not having the notes of the subject so I went to one of my friend and asked him to give me the notes. As he was also studying so I decided not to disturb him and take the pictures of the notebook. I used my phone for this purpose. I started studying the pictures from the phone and soon enough become fed up because of the small screen then I decided to move the pictures to my laptop. I started studying but before the completion of the page it become difficult for me concentrate.




Then I decided to use the software that I have coded some time ago. First of all I decided to change the name of the pictures as for the pictures to get imported we have to change the name and bring the images to the png format and It was a large task to change the name of each and every file so I looked for some python script on the internet. Soon enough I found something that was explained enough so that I can use it. I changed the script according to my needs and was able to successfully change the name of images.




After I saw the images carefully I was able to find that the images were not in the right order so I went to one of my senior(Amarjeet). He told me to create a list first and then send the list to the function which changed the name of the images. Earlier it was a dictionary by default and since the values in the dictionary are in a random order so we were not getting the correct order.




So in the end I solved this problem and took the pictures and put them into the required folder. And in the end I manipulated the JSON file and finally was able to run the image on the browser.




On opening the browser I found that the images were 90 degree toward the left. So, I used this command to rotate it back to normal.




mogrify -rotate "90" *.png
