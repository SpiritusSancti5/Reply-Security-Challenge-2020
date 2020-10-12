# Reply-Security-Challenge-2020

Description:

```The space-time coordinates bring R-boy to Florence in 1320 AD. Zer0 has just stolen the unpublished version of the "Divine Comedy" from its real author, the "Wandering Poet", giving it to his evil brother, Dante.

Help the "Wandering Poet" recover his opera and let the whole world discover the truth.

Pswd: PoetaErranteIsMyHero!
gamebox1.reply.it, port 1320, Pwd: PoetaErranteIsMyHero!
```
First step login.

```console
nc gamebox1.reply.it 1320
Password: PoetaErranteIsMyHero!
```
And you enter a funny text based adventure, however only one answer works so there's no way to get into a dead end.

The Wandering Poet had his document stolen and is yelling from within a crowd about the theft. The crowd is calling him a liar. You decide to step in (that's the only choice you're given) and help him out. After a short conversation you're asked:

```
Where are we going?:
```

And you're given console output, displayed as a document encoded in hex:
[Document](https://github.com/SpiritusSancti5/Reply-Security-Challenge-2020/blob/main/Document)

```python
import re 
 
doc = ''

with open('m100.txt','r') as f:
    for line in f:
        line = line.rstrip()
        
        doc += re.sub('[\W_]+', '', line)

print (doc) 

hex_stuff = bytes.fromhex(doc).decode('utf-8')
print(hex_stuff)
```

Result is a QR code:

![](Untitled.png)

Once scanned you get:
```
Name : Ludovico Arrosto
Postal address private Via Vittorio Emanuele II, 21
Firenze 
Italy

email l.arrosto@pacademy.com

Organization 
Poetry Academy
```

The answer to the previous question is:
*Via Vittorio Emanuele II, 21*

The text adventure continues:

```
"Where are we going?": Ludovico Arrosto
I don't know where it is! Try again: Via Vittorio Emanuele II, 21

"You know where Ludovico Arrosto lives? Great! Let's go!"
You and the Poeta Errante leave the house and start walking in the direction of
Ludovico Arrosto's mansion...


You and the Poeta Errante arrive at Ludovico Arrosto's house. At a first glance
no one seems to be home.
What do you want to do? [knock the door, look around]: knock the door
There is nobody...
What do you want to do? [knock the door, look around]: look around

You found the mailbox of Ludovico Arrosto's house. Since the president of
Poetry Academy isn't at home at the moment, you could leave a letter.
What do you want to do? [open mailbox]: open mailbox
In order to open the mailbox you have to guess the 4 digits code (each position
could contain a number from 0 to 9), given the following evidences:

3871    1 correct digit and in right position
4170    1 correct digit and in wrong position
5028    2 correct digits and in right position
7526    1 correct digit and in right position
8350    2 correct digits and in wrong position

Insert the code:
```
So this is the game of bulls and cows. The answer is:
**3029**

```
The mailbox opens!
You ask to the Poeta Errante to write his indictment letter...
"Ha-ha, leave it to me! Not surprisingly i am a poet!"
The Poeta Errante write his letter, and insert it in the mailbox.
"Thank you again! Let's see what happens tomorrow. You can sleep in my house
tonight, you deserve it!"
You have a strange feeling, the history you know did not turn out this way...
You return to the Poeta Errante's house, spend the evening there until you fall
asleep... [Press Enter to continue]

Zzz... Zzz... Zzz... 

You wake up with a start in the middle of the night. You are sweaty...
You get up to drink a glass of water. The Poeta Errante is still sleeping
What do you want to do? [go to bed, save the history]:

save the history

You decide to return to Ludovico Arrosto's house to destroy the letter of the
Poeta Errante. Even if he is the real author of the Divina Commedia, in the
history you know Dante is known as the poet who written it.
You arrive in front of the mailbox. You open it and found the letter.
What do you want to do? [destroy letter, return home]: return home
So, why are you came here?

What do you want to do? [destroy letter, return home]: destroy the letter
I don't understand.

What do you want to do? [destroy letter, return home]: destroy letter    
Are you sure? [yes, no]: yes
Really? [yes, no]: yes

You rag the letter in thousand of pieces, and throw them around so no one
can find them. Then you return to the Poeta Errante's house to sleep...

[Press Enter to continue]

You wake up the next day, at dawn, and your mood is not the best. You and the
Poeta Errante decide to go to the market town, to hear if there is any news
about the letter. Once arrived you note that there is a minsterl in the center
of the square. What he says leaves no doubt:
"Dante annouces his next opera! The Divina Commedia!"
"Dante annouces his next opera! The Divina Commedia!"
The Poeta Errante does not understand what is going on...
What do you want to do? [hug poeta errante, do nothing]: hug poeta errante

The Poeta Errante runs away, until he disappears from your sight. You have done
your duty, and now it's time to leave. In this epoch you did not find Zer0.
You return to Zer0's time machine you used to travel up here, but the spacetime
coordinates are all wrong. What a mess! Someone touched this machine when you
were with the Poeta Errante! There is the instructions manual opened on a
particular page and a little folded piece of paper.
Do you want to open it? [yes, no]: yes

This communication method is something never seen in this epoch. It's not really
like sending a big, whole, message, but, instead, dived it in little p...ieces,
and send them one at time...

Do you want to return to the present? SOLVE THIS RIDDLE! AH AH AH!

   Zer0
```

The console displayed something which I first thought to be a hex dump that i had to fix:

[Zero's Riddle](https://github.com/SpiritusSancti5/Reply-Security-Challenge-2020/blob/main/Zer0's%20riddle)

Being stuck, i then looked at the last character of each chunk and then I thought I spotted the flag:
**{FLG:i74370prrn343<}**
Which was wrong.

However Jani, one of my team mates pointed out these are actually TCP packages have to be decoded (using a hex packet decoder) so you can reorder them based on the time received.

## FLAG

**{FLG:i7430prrn33743<}**



