# Space Jam

Space Jam's [website](https://spacejam.com/) has a very straightforward and simple layout. This tutorial breaks down the HTML behind its layouts and describes potential adaptations of its code. 

Space Jam's home page is its logo surrounded by various planets leading to different locations of the site, suspended in the center of "outer space". I was surprised that it was table-based, with each planet placed in a specific box.

The background elements of the website are implemented like this:

    <body bgcolor="#000000" background="img/bg_stars.gif" text="#ff0000" link="#ff4c4c" vlink="#ff4c4c" alink="#ff4c4c">
   
  It sets the background color to black, repeats a small 111 x 111 file as the background, and sets all hyperlink colors to #ff4c4c, a neon red color. This creates the space-themed background.

The site uses a `<center>` tag to center the planets and uses another `<center>` block with a hidden `<nobr>` containing a `<table>`object with no content. It is followed by a smaller `<table>` object and three `<br>` objects. I can only assume this was for padding purposes, but I want to see if there's an easier way to create this indent than juggling tables and pixels. The indent height used is 120px after adding up everything, using Chrome's Inspect tool.

(Note: the `<br>` tag is 18px tall on my browser. It might be different for you, so double-check with the Inspect tool.)

The `<center>` tag is obsolete in HTML5, so we can include "margin-right:auto;" and "margin-left:auto;" in the table's style attribute. This will center it. 

We can then set up the table like this:

    <table width="500" border="0" style="margin-top:120px; margin-right:auto; margin-left:auto;">

The table in Space Jam's website is 4 rows long and 5 columns wide. The Space Jam logo takes up space in the center at rows 2-3 and columns 2-4. Depending on the pictures used, you can definitely adjust your table's width and number of rows and columns; however, keeping the logo at the center is key for that Space Jam look. 

Each cell tends to follow this format:

    <td><a href=""><img src="" height="52" width="58" alt="Jump Station" border="0"></a>

(Note: The alt attribute helps people who use screen readers understand what the image represents. Try including the alt attribute in any future HTML projects)

We can go for a row by row examination of the code used.

Row 1 has the Press Box Shuttle, Jam Central, Planet B-Ball, and Lunar Tunes icons. The Press Box Shuttle icon takes up two columns and uses the 'align' attribute. The Press Box Shuttle icon uses three `<br>` tags to force its icon downwards, but I would recommending adding `style="position:relative; top:54px;"` to its `<img src>` tag.

I'm not including the `<href>` and `<img src>`tags included below, but I wanted to make you take a look at how the valign and align attributes are used to make the planets look like they're in orbit.

    <td colspan="2" align="right" valign="middle"> <!-- press box shuttle --> </td>
    <td align="center" valign="middle"> <!-- jam central --> </td>
    <td align="center" valign="top"> <!-- planet b-ball --> </td>
    <td align="center" valign="bottom"> <!-- lunar tunes --> </td>

Row 2 has the Line Up, the Space Jam logo, and the Jump Station tags. Again, much of the same deal as before. The Line Up uses two `<br>` tags. We know what the deal is: 18px*2 = 36px. Throw a `style="position:relative; top:36px;"` into its `<img src>` tag. Aside from that, there isn't anything to note. 

    <td align="middle" valign="top"> <!-- Line Up --> </td>
    <td colspan="3" rowspan="2" align="right" valign="middle"> <!-- Logo --> </td>
    <td align="right" valign="bottom">

Row 3 has the Junior Jam, part of the Logo, and the Warner Studio Store. I don't think there's anything interesting here aside from the Store taking up two rows. You can remove the rowspan from it, but you'll have to change up the valign and style attributes for both Jump Station and the Store. Up to you.

    <td align="center" valign="bottom"> <!-- Junior Jam --> </td>
    <td rowspan="2" align="center" valign="top"> <!-- Warner Studio Store --> </td>

Row 4 has Stellar Souvenirs, the Site Map, and Behind the Jam. It creates an empty first cell, so the three icons can occupy columns 2-4. The Site Map has four `<br>` tags, but it's better to replace it with a style attribute for future changes.

    <td></td>
    <td align="center" valign="top"> <!-- Stellar Souvenirs --> </td>
    <td align="center" valign="bottom"> <!-- Site Map --> </td>
    <td align="center" valign="middle"> <!-- Behind the Jam --> </td>
    
And with the last row, we can close off the `</table>`.

I won't go into the footer links, but they should be pretty straightforward. 
