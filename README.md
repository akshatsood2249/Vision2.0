<html>
<body>
    
<h1 align=center> Vision 2.0 </h1>

<h3> Problem Statement</h3>
    
<p align=center>
    <img align=center src="media/bot-with-arena.png">
</p>

1. There are <b>2 paths</b> in our arena (see above) (<i>inner</i> and <i>outer</i> square) and there are <b>4 connecting paths</b> of different colours joining them. <br>
2. Bot can change from outer path to inner path or vice versa. Bot is allowed to move in <b> clockwise direction </b> only. The portion of the arena in <b> black colour </b> is restricted for the movement of the bot. <br>
3. There will be <b>3 shapes</b> (<i>square, circle</i> and <i>triangle</i>) of <b>2 different colours</b>, distinguishing each block in 6 different ways. <br>
4. On the outermost path there will be <b>4 black arrows</b> at the end of connecting paths pointing in clockwise direction. These arrows mark the <b> starting zone </b> where the bot will be placed initially on any one of the arrows. <br>
5. The Centre of the arena is the <b>home zone</b>. The bot has to traverse the arena, complete a full round and finish at the home zone. <br>

<p flat=center>
    <img src = "media/arena.gif" alt = "Arena" width = "350">
    <img src = "media/husky.gif" alt = "Bot" width = "350"> 
</p>

<h3> Task To Do</h3>

1. The bot is placed at one of the <b>starting zones</b>. <br>
2. An abbreviation which associate to specific colour and shape. <br>
  <ul>
   - <b> RT </b> for Red Triangle. <br>
   - <b> RS </b> for Red Square. <br>
   - <b> RC </b> for Red Circle. <br>
   - <b> YT </b> for Yellow Triangle. <br>
   - <b> YS </b> for Yellow Square. <br>
   - <b> YC </b> for Yellow Circle. <br>
 </ul>
3. On start of each turn, a function returns a random shape from the list above.The bot must then find the closest block (with the corresponding shape) which it can reach following a clockwise path. <br>
4. As soon as the bot stops moving, bot has to ask for input using the function provided. <br>
    5. This continues till the <b>bot has completed a full round around the center</b>, then it should move to home via the connecting paths that it started on. <br>
6. On reaching home the bot should signal that it has finished the task. <br>
    
<h3> Our Approach </h3>
    We used <b> Computer Vision</b> for <i>image segmentation</i> i.e. extracting shapes of different colors from the arena.<br>
    Applied <b>Breadth First Search</b> algorithm (on a customly designed <i>directed graph</i>) to trace path from the current position of the bot to all occurences of the corresponding shape in the arena. From all the paths secured above, one with minimum length was considered.<br> 
    Popular physics engine <b>PyBullet</b> was utilized for simulating our bot on the arena. <br><br>
    First, a <b>directed graph</b> is created, in which edges are added in the direction of allowed movement. <br>
Then, the shape and color in each grid of the arena is detected using several techniques such as masking, erosion, dilation and contour approximation.<br>
    <b>Aruco Marker</b> is used to determine the current position of the bot at any instant. <br>
    A function (<code>roll_dice</code> in our case) returns a shape-color combination to the bot in order to find out the next destination. <br>
    Then, <b>BFS</b> is used to determine the shortest path from the current position to the next destination. <br>
After that, two vectors are created providing the positions, along with the angles, of the bot and the destination grid. Various custom-made functions, such as dist(), ang(), rotate() and move(), are employed in order to facilitate the movement of the bot. <br>
After the bot crosses the first grid, the graph edges are altered in a way that the bot enters the home after completion of a clockwise round. <br>
The task is completed after the bot reaches the central home grid.
    
<h3>Team ENIGMA</h3>
    
<table>
   <td align="center">
      <a href="https://github.com/Aadi1110">
         <img src="https://avatars2.githubusercontent.com/u/60649618?s=460&v=4" width="100px;" alt=""/>
         <br />
         <sub>
            <b>Aadi Shukla</b>
         </sub>
      </a>
      <br />
   </td>
   <td align="center">
      <a href="https://github.com/Akshatsood2249">
         <img src="https://avatars3.githubusercontent.com/u/68052998?s=400&u=d83d34a2596dc22bef460e3545e76469d2c72ad9&v=4" width="100px;" alt=""/>
         <br />
         <sub>
            <b>Akshat Sood</b>
         </sub>
      </a>
      <br />
   </td>
   <td align="center">
      <a href="https://github.com/Caesar71">
         <img src="https://avatars3.githubusercontent.com/u/60649622?s=460&u=be11d2f1873dc0b4aa044051cfb9389857225f83&v=4" width="100px;" alt=""/>
         <br />
         <sub>
            <b>Eshaan Gupta</b>
         </sub>
      </a>
      <br />
   </td>
</table>
 
</body>
</html>




