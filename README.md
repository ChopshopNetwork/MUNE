# MUNE
### Roll20 Macros for playing the Solo-D&amp;D system known as MUNE.    
    
NOTE - *These macros make use of the TokenMod API script that is only available to Roll20 Pro subscribers.*  
*You can easily use these macros without the automatic Intervention Point tracking, but you will need to tinker*
*and remove the pieces of code that are TokenMod specific.*    
    
NOTE - *Many of these macros include my character's namer,  " Thorn " .  Anywhere Thorn appears in the code should*
*be replaced with your character's name.  The tokenmod script also calls upon my character's token ID, which is a*
*a long string of characters that look like this,  " -LILHc05l60uKJ0qwGHr " .  You will need to find your token ID*
*and swap it out for Thorn's if you wish for the automatic Intervention Point tracker to work.*

**Find TheAaron's TokenMod script at the link below**
https://github.com/Roll20/roll20-api-scripts/tree/master/TokenMod



### Rollable Tables
###### *This macro system takes advantage of the Rollable Tables in Roll20. Make sure your table name uses the exact name below.*
**Name:** portent-table   
**Instructions:**   
You need to load the table with entries that are single words or single two-word phrases. Keep them all weighted at 1.  I googled 
 " Random Word List "  and entered in about 250 words into mine.  You don't necessarily need to enter that many.  The macros are set 
up to combine two entries from the table each time you use a portent, so fifty words would result in thousands of possible combinations.
  
  
  
### Hidden Macros
###### *These macros DO NOT need to have the  " in bar "  option checkmarked.  They should have the exact name listed below or they will not function properly*
  
  
**Name:** IV-point   
**Code:**   
 " &{template:npcaction} {{name=Rolled a Six}} {{rname=Intervention Point}} {{description=**[[@{thorn|other_resource}+1]]/3 Intervention Points**}}
!token-mod --set bar3_value|+1 --ids -LILHc05l60uKJ0qwGHr   " 
  
  
**Name:** Ignore   
**Code:**
 " &{template:npcaction} {{name=Player Action}} {{rname=Ignore the Oracle}} {{description=**?{Details|}**}}   " 



### NARRATIVE MACROS
###### *These are macros I use to Narrate my character's actions or to narrate the story from a  " narrator voice " . Both of these macros should have the  " in bar "  option checkmarked*


**Name:** Action   
**Code:**   
 " /me ?{ " Thorn... " |}   " 


**Name:** Narrate   
**Code:**   
 " /desc ?{Scene Description|}   " 
  
  
  
### ORACLE MACROS
###### *These are macros you use to engage the MUNE mechanics.  These macros should all have  " in bar "  option checkmarked.*
  
  
**Name:** Interest-Check   
**Code:**   
&{template:npcaction} {{name=Ask the Oracle}} {{rname=Player Inquiry}} {{description=**Is there anything of interest?**}}    
&{template:npcaction} {{name=Dungeon Master Emulator}} {{rname=Oracle}} {{description=**Answer** = [[1d6]]    
1 = No, and...    
2 = No    
3 = No, but…    
4 = Yes, but...    
5 = Yes <br>    
6 = Yes, and... | +1 IV point    
[Add IV Point](!&#13;#IV-point)    
[Roll Intervention](!&#13;#Intervention)    
[Ignore](!&#13;#Ignore)}}
  
  
**Name:** Status-Quo   
**Code:**   
 " &{template:npcaction} {{name=Ask the Oracle}} {{rname=Player Inquiry}} {{description=**Does everything appear normal?**}}
&{template:npcaction} {{name=Dungeon Master Emulator}} {{rname=Oracle}} {{description=**Answer** = [[1d6]]
1 = No, and...
2 = No
3 = No, but..
4 = Yes, but...
5 = Yes
6 = Yes, and... | +1 IV point
[Add IV Point](!&#13;#IV-point)
[Roll Intervention](!&#13;#Intervention)
[Ignore](!&#13;#Ignore)}} " 
  
  
**Name:** Intervention   
**Code:**   
“!token-mod --set bar3_value|0 --ids -LILHc05l60uKJ0qwGHr
&{template:npcaction} {{name=Dungeon Master Emulator}} {{rname=Intervention}} {{description=**Answer** = [[1d6]] 
1 = New entity
2 = Entity positive
3 = Entity negative
4 = Advance plot
5 = Regress plot
6 = Wild
[roll portent](!&#13;#Portent)}} " 
  
  
**Name:** NPC   
**Code:**   
  " &{template:npcaction} {{name=Dungeon Master Emulator}} {{rname=NPC Attitude}} {{description=**Answer** = [[1d6]] 
1-2 = Hostile
3-4 = Neutral
5-6 = Friendly}} " 
 
 
**Name:** Oracle   
**Code:**   
 " &{template:npcaction} {{name=Ask the Oracle}} {{rname=Player Inquiry}} {{description=**?{Ask the Oracle|}?**}}
&{template:npcaction} {{name=Dungeon Master Emulator}} {{rname=Oracle}} {{description=**Answer** = [[1d6]]
1 = No, and...
2 = No
3 = No, but..
4 = Yes, but...
5 = Yes
6 = Yes, and... | +1 IV point
[Add IV Point](!&#13;#IV-point)
[Roll Intervention](!&#13;#Intervention)
[Ignore](!&#13;#Ignore)}} " 
  
  
**Name:** Oracle-No   
**Code:**   
 " &{template:npcaction} {{name=Ask the Oracle}} {{rname=Player Inquiry}} {{description=**?{Ask the Oracle|}?**}}
&{template:npcaction} {{name=Dungeon Master Emulator}} {{rname=Oracle}} {{description=**Likely No** = [[1d6]] | [[1d6]]
1 = No, and...
2 = No
3 = No, but...
4 = Yes, but...
5 = Yes
6 = Yes, and... | +1 IV point
[Add IV Point](!&#13;#IV-point)
[Roll Intervention](!&#13;#Intervention)
[Ignore](!&#13;#Ignore)}} " 
  
  
**Name:** Oracle-Yes   
**Code:**   
 " &{template:npcaction} {{name=Ask the Oracle}} {{rname=Player Inquiry}} {{description=**?{Ask the Oracle|}?**}}
&{template:npcaction} {{name=Dungeon Master Emulator}} {{rname=Oracle}} {{description=**Likely Yes** = [[1d6]] | [[1d6]]
1 = No, and...
2 = No
3 = No, but...
4 = Yes, but...
5 = Yes
6 = Yes, and... | +1 IV Point
[Add IV Point](!&#13;#IV-point)
[Roll Intervention](!&#13;#Intervention)
[Ignore](!&#13;#Ignore)}} " 
  
  
**Name:** Portent   
**Code:**  
 " &{template:npcaction} {{name=Dungeon Master Emulator}} {{rname=Portent}} {{description=[[1t[portent-table]]][[1t[portent-table]]]}} "   
