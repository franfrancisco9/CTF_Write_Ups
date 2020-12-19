# X-MAS-CTF-2020
This was my first attempt at a CTF after being recently introduced to the concept. I challenged a friend and we set to try and do as many challenges as possible.
Personally, I also had the goal of trying to understand how the different types of areas worked and which ones I had most insterest!
The format of the CTF allowed for just that, specially with the adding of new challenges every other day as well as a good and active community on discord.
Great description of the competition can be found in the official competition website: <https://xmas.htsp.ro/home>

This will be my first attempt at write ups, so any suggestions let me know! Here is my discord Franfrancisco9 #0105

List of the categories and challenges I solved:
- !Sanity Check
    - [Merry Christmas!](https://github.com/franfrancisco9/X-MAS-CTF-2020/blob/main/README.md#merry-christmas-55-points)
    - [The place where all the elves hang out](https://github.com/franfrancisco9/X-MAS-CTF-2020/blob/main/README.md#the-place-where-all-the-elves-hang-out--55-points)
- Forensics
    - [Conversation](https://github.com/franfrancisco9/X-MAS-CTF-2020/blob/main/README.md#conversation-2650-points)
- Miscellaneous
    - [PMB](https://github.com/franfrancisco9/X-MAS-CTF-2020/blob/main/README.md#pmb-5050-points)

*Note: For every challenge I will present the points they had at the end of the competition / the points at the begginning as the platform adjusted the difficulty according to how many teams have solved the challenge*

*Note 2: For every challenge I will give my personall evaluation of difficulty*

## !Sanity Check
>Introductory category and just for fun 


#### **Merry Christmas! (5/5 Points)**

First challenge when you entered the competition made for fun as a welcoming text, flag was given in the description:

![Image of Merry Christmas!](https://github.com/franfrancisco9/X-MAS-CTF-2020/blob/main/Merry_Christams!.png)

Flag was **X-MAS{H0_H0_H0_H4ck_4_4_br1gh73r_fu7ur3_4nd_m3rry_X-MAS!!!}**

#### **The place where all the elves hang out  (5/5 Points)**

Another fun challenge where you were directed to join the discord server and haas the name suggests, when checking *general* channel's description, there was your flag:

![The place where all the elves hang out](https://github.com/franfrancisco9/X-MAS-CTF-2020/blob/main/The_Place_Where_All_The_Elves_Hang_Out.png)

Flag was **X-MAS{Alr1gh7_50_W3_g07_734_b15cui75_4nd_7h3_w4rm357_w1n73r_50ck5_w3_c0uld_f1nd.L37'5_g0!}**

## Forensics 

#### **Conversation (26/50 Points)**
>Author: Yakuhito

![Image of conversation description](https://github.com/franfrancisco9/X-MAS-CTF-2020/blob/main/Conversation/Conversation_Description.png)

We were given a file called *logs.pcapng*, and being new to CTF competitions I followed all the introductory steps you can find online when dealing with any file, being one of them of course the strings function.

Uppon calling the strings function, after some scrolling you could found the folling sequence of readable text:
>Hello there, yakuhito

>Hello, John! Nice to hear from you again. It's been a while.

>I'm sorry about that... the folks at my company restrict our access to chat apps.

>Do you have it?

>Have what?

>The thing.

>Oh, sure. Here it comes:

>Doesn't look like the thing

>A guy like you should know what to do with it.

At first I was really confused because it seemed there was nothing but giberish after *Here it comes:* but after a close look I noticed a text sequence that suggested some sort of base64 encryptation

>JP1ADIA7DJ5hLI9zpz9gK21upzgyqTyhM19bLKAsLI9hMKqsLz95MaWcMJ5xYJEuBQR3LmpkZwx5ZGL3AGS9Pt==

I imidiately run the echo | base64 --decode line just to find a pack of unreadable chars. After some digging I was recommend [cyberchef](https://gchq.github.io/CyberChef/), which definetely the best tool to quickly run over basic encodings, analysis, etc ( specially for begginers!)

I used the magic analysis and immediatly got a response with ROT13 base64 decoding:

![Imgae of conversation cyber chef](https://github.com/franfrancisco9/X-MAS-CTF-2020/blob/main/Conversation/Conversation_Cyber_Chef.png)

Flag was **X-MAS{Anna_from_marketing_has_a_new_boyfriend-da817c7129916751}**

Difficulty:  *Easy* 

I felt like this was a pretty standart and easy challenge, which also showed me the importance of starting to identify the most common types of encoding

## Miscellaneous

#### **PMB (50/50 Points)**
>Author: Yakuhito

![Image of PMB description](https://github.com/franfrancisco9/X-MAS-CTF-2020/blob/main/PMB/PMB_description.png)

This challenge was really all about the nuances in the different descriptions. After connecting with the given IP you would be greeted by this menu:

![Image of PMB Menu](https://github.com/franfrancisco9/X-MAS-CTF-2020/blob/main/PMB/PMB_menu.png)

They tell us our number cannot have a modulus higher or equal to 100 and that it can ***any*** number ( this will be important). I started with some basic tests:

>Interest: 1

![PMB months](https://github.com/franfrancisco9/X-MAS-CTF-2020/blob/main/PMB/PMB_months.png)

So it seems that is a simple multiplication process each month, the problem is we cannot have any positive value until the last month.

That is where the ***any*** so strongly written importance appears, as it is sopposed to remind us that you can also use complex numbers! They also have a modulus to respect but they have this great thing where for z = a + bj if we have a = 0 and b = 1, then we have j

And j^2 = -1, and -1j = -j and -j^2 = 1, which means we just need to use a certain b with j that gets us to the required 10 million

That number is 10, as 10 x 1000 = 10 000, 10 000 x 10 = 100 000, 100 000 x 10 = 1 000 000 and 10 x 1 000 000 = 10 000 000 000

Joining 10 with j (does not matter if it is -10j or 10j) we will get to the 10 million and obtain the flag:

![PMB flag](https://github.com/franfrancisco9/X-MAS-CTF-2020/blob/main/PMB/PMB_flag.png)

Flag was **X-MAS{th4t_1s_4n_1nt3r3st1ng_1nt3r3st_r4t3-0116c512b7615456}**

Difficulty:  *Easy*


Great challenge that shows importance of reading descriptions carefully!

#### **Bobi's Whacked (50/50 Points)**
>Author: Bobi

For this challenge we start with nothing else but this line:

![Bobis description](https://github.com/franfrancisco9/X-MAS-CTF-2020/blob/main/Bobi's%20Whacked/Bobis_Whacked_Description.png)

This suggests this is an OSINT challenge, meaning we have to look for clues online, usually in social media or other available websites, and try to follow clues or hints for the information we want.

In this case I immediatly looked the name *Bobi whack* and found one channel on the name *Bobi's wHack*. 

The reason i immediatly went for youtube is because the description mentions *caption* which is a usual word for subtitles.

4 videos showed to have captions inserted by the channel owner. By clicking on the video and choosing the transcript option I got to text bits:

>X-MAS{nice_thisisjustthefirstpart

>_congrats}

I tested to submit *X-MAS{nice_thisisjustthefirstpart_congrats}* but it did not work, meaning there is probably a middle section missing.

When checking the channel, I found the following sequence in the *about* section:

>6D6964646C6570617274

Using cyber chef we got from hex decoding the word *middlepart*

Flag was **X-MAS{nice_thisisjustthefirstpart_middlepart__congrats}**

Difficulty:  *Easy*

Great challenge overall




























