---
author: ranvirsingh1114
comments: true
date: 2016-11-16 20:59:33+00:00
layout: post
link: https://ranvirsinghprojects.wordpress.com/2016/11/17/creating-graphs-using-data-form-csv-file/
slug: creating-graphs-using-data-form-csv-file
title: Creating graphs using data form .csv file
wordpress_id: 479
categories:
- JavaScript
---

Yesterday I was talking to a friend and he told me that he has some work that he needs to complete by the following night. He asked me for the help and I decided to help as my exam was postponed. He said that he had a .csv file( comma separated values) and want to shift the whole data into postgresql database.

I told him that I will like to help him and ask him to send me the files. First task was to install postgresql.


<blockquote>$ sudo apt-get install postgresql postgresql-contrib</blockquote>


Now use the following command to start postgresql terminal and start typing postgresql commands which are somewhat similar to MySQL.


<blockquote>$ sudo -u postgres psql postgres</blockquote>


After this a terminal will open up where you put all your commands. If this does not work use the following command.


<blockquote>$ sudo /etc/init.d/postgresql restart</blockquote>


Now use the earlier command again and it will definitely work.

After this I created a table in postgresql using simple create table command.

Now to copy the data of .csv file into postgresql table use the following command.


<blockquote> postgres=# `COPY zip_codes FROM '/path/to/csv/ZIP_CODES.txt' DELIMITER ',' CSV HEADER;`</blockquote>


Now you can use the command like select * from table_name; and watch the table on your screen populated with the new data.

After this was done I had to create a graph out of the given data. I searched this on the google and found a good javascript library for doing this.

Here is the link for creating graphs from the input of .csv file.

[http://canvasjs.com/forums/topic/graph-a-csv-file/](http://canvasjs.com/forums/topic/graph-a-csv-file/)

Now as the .csv file had many comma separated values my friend went forward and asked me to create a script that can create different files with the required data for this I told him that it will require some time. I came back to my room and started making a python script that can keep two comma separated values in each file.

Here is the part that created the first file.


<blockquote>target = open("stat3112.csv", 'r+')
temp1 = 0
for line in target:
index = line.find(",")
resttext = line[index + 1:]
print resttext
index_rest_text = resttext.find(",")
net_index = index + index_rest_text + 1

newfile = "file" + str(temp1) + ".csv"
files = open(newfile, 'a')
print index_rest_text
files.write(line[:net_index] + "\n")
files.close()

target.close()</blockquote>


Therefore, The task was completed.
