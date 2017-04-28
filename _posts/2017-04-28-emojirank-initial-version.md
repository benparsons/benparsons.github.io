---
layout: post
title:  "EmojiRank first version"
date:   2017-04-28
categories: projects
---
Having not had a side project for a while due to work being interesting enough to take all my creative energy, I  was receptive to something self-contained but worth releasing.  
My old friend Doug suggested a way of comparing different emoji designs from vendors inspired by (websites), and after batting the idea around for a short while I was excited to start.  
It would also be fun to work on something together after not doing so since school. 
Such a simple project could have been created in any number of stacks, but I chose node and mongodb on Heroku due to familiarity and having recently used it successfully.  
First task was to populate a db with the glyphs and metadata needed. The Unicode website provides a complete list of emoji along with glyphs  from various major vendors. I wrote a NodeJS script to read the huge (XXmb)  table, and for each row save the image to a PNG file plus append a mongo insert statement to a file for later execution.  
Emoji v4.0 includes variations in the form of different skin tones for certain glyphs. After some discussion we decided to "flatten" the glyphs, that is, we consider there is only one level of classification, so (normal) (light brown) are considered separately and not nested or otherwise connected.  
The user is presented with a complete set of glyphs for a single emoji. First they click to select a favourite, then from the remainder they click to select their least favourite. These votes (+/-) are used to calculate the glyph score, which is used later for ranking the glyphs.  
After each pair of votes the user can choose to be shown another set of glyphs, which chooses a random emoji to display. If the user enters the site at / we only select from the first 1024 (i.e. the more standard) emojis to avoid confusion about what is going on.  
To display the results I used CSS to build a pictograph of the calculated glyph scores. The further a row stretches to the right, the more loved it is, the more to the left, the more hated.  Pictographs were chosen as they look fun but still convey how glyphs performed relative to each other. It's important to emphasis that these results are just for curiosity and humour rather than any useful analysis.  
Working on EmojiRank was a slight departure for me because there were only two stakeholders and almost nothing at stake. Light as the project was, all decisions still needed some consideration and discussion before taking action.  
We "released" an initial version to friends, and it was fairly well used and liked. People seemed to get the idea, though there was repeated feedback around lack of an ending. To this end, discussions with more experienced product workers brought up the need for gamification. There are a couple of ideas there which could produce an improved second version. 