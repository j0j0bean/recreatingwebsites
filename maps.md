# `<map>` 

The `<map>` tag in HTML helps create clickable, interactive maps like the non-Flash ones we find in Neopets or this [page](https://spacejam.com/cmp/jump/jumpframes.html) in Space Jam.

Creating a map in HTMl is fairly straightforward. You just need to post an image and then assign it an usemap attribute. You then create a map with the same name without the # at the front.

    <img src="https://lh3.googleusercontent.com/n8h7oi1weTP__5bgG4FTuONW0eyVw_h90qesqa_6UX5LaF2ymk3xNAdlCVGdx3gzvDcoMq12_hxUn3V9d05zViO81nlZKV3Rpw=w1200-h630-rj-pp-e365" alt="loona in sowhat" display="block" width="100%" height="100%" object-fit="cover" usemap="#keyMap">
        <map name="keyMap"> 
            <area alt="heejin" title="heejin" coords="82,42,207,535" shape="rect" href="https://www.youtube.com/channel/UCOJplhB0wGQWv9OuRmMT-4g">
            <area  alt="hyunjin" title="hyunjin" coords="327,319,211,83" shape="rect" href="https://www.youtube.com/channel/UCOJplhB0wGQWv9OuRmMT-4g">
            <area  alt="chuu" title="chuu" coords="347,95,474,315" shape="rect" href="https://www.youtube.com/channel/UCOJplhB0wGQWv9OuRmMT-4g">
            <area  alt="yves" title="yves" coords="480,85,578,412" shape="rect" href="https://www.youtube.com/channel/UCOJplhB0wGQWv9OuRmMT-4g">
         </map>

The above creates a map with rectangular boxes. Clicking on the boxes will send you to where the hyperlink points to. You can also create polygonal and circular areas. 

    <area  alt="gowon" title="chuu" coords="347,95,45" shape="circle" href="https://www.youtube.com/channel/UCOJplhB0wGQWv9OuRmMT-4g">
    <<area  alt="yves" title="yves" coords="80,85,78,409,58,120,80,85" shape="poly" href="https://www.youtube.com/channel/UCOJplhB0wGQWv9OuRmMT-4g">
<!-- coords are not accurate -->


For circular areas, the coords format is "x, y, radius".
For rectangular areas, the coords format is "x-coordinate of the top-left corner, y-coordinate of the top-left corner, x-coordinate of the bottom-right corner, x-coordinate of the bottom-right corner"
For polygonal areas, the coords format is "x-coordinate of the starting point, the y-coordinate of the starting point, x-coordinate of the connecting point, ..." and so, until it closes with the first two coordinate values.

Other than sending users to links on and off your website, you can also use maps to play music and change your mouse cursor.

I found this information on using maps to play music [here](https://stackoverflow.com/questions/22650716/using-a-javascript-function-in-an-html-area-to-play-audio-on-click).

I adapted parts of the code to try playing the solos for each LOONA's member by creating a Javascript dictionary that had a key-value pair of member-name.mp3. 

    <script>
    var songs = {"kimlip":"kimlip.mp3","jinsoul":"jinsoul.mp3","choerry":"choerry.mp3"};
    function playSound(name) {
     var audio = new Audio(songs[name]);
     audio.play();
    } </script>

    <img src="some link" usemap="#oddeyecircle">
    <map name="oddeyecircle">
	    <area alt="kimlip" title="kimlip" coords="327,319,211,83" href="Javascript:playSound('kimlip');"
	    <area alt="jinsoul" title="jinsoul" coords="327,319,211,83" href="#" onclick="playSound('jinsoul');">
	    <area alt="choerry" title="choerry" coords="327,319,211,83" href="#" onclick="playSound('choerry');">
	    
Chrome, IE, and Safari does not allow style attributes for area tags in maps, but you can also change your mouse cursor look like [this](https://stackoverflow.com/questions/6589768/cursor-not-changing-to-pointer-in-usemap-area-case):

    <script>
    var cursors = {"yves":"yves.png","chuu":"chuu.png", "gowon":"gowon.png", "olivia":"olivia.png"};
	function changeimage(name){
	    document.body.style.cursor = 
	    URL(cursors[name]);
    } <script>
    

