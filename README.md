




















































import processing.core.PApplet;
//this is my cool Space_Game
//the way you play is you try to make your ship avoid the incoming objects
//you have three lives in the top left corner
// 't' resets the game and 'q' quits the game
// good luck
public class Space_Game extends PApplet{
	// the x axises of the blocks
	int blockOne = 800;
    int blockTwo = 600;
   	int blockThree = 900;
   	int blockFour = 690;
   	int blockFive = 500;
   	int blockSix = 600;
   	//Your lives
   	int lives = 3;
   	//the score
   	int score;
   	//this is so it will only decrease one life per time hit
   	int loopNeed = 1;
   	int loop;
    public static void main(String[] args) {
        PApplet.main("Space_Game");
    }
    public void settings(){
   //Making the window
    	size(700,300);
    }
    public void setup(){
    //making the background
    	background(0,0,0);
    	
    }

    public void draw(){
    //clearing the window
    	fill(100,200,0);
    	rect(0,0,700,300);
    	loop = loop + 1;
    //drawing lives
    	fill(200,100,0);
    	if(lives == 3) {
    		rect(0,0,90,20);
    		rect(70,20,20,60);
    		rect(0,80,90,20);
    		rect(70,100,20,60);
    		rect(0,160,90,20);
    	}else if(lives == 2){
    		rect(0,0,90,20);
    		rect(70,20,20,60);
    		rect(0,80,90,20);
    		rect(0,100,20,60);
    		rect(0,160,90,20);
    	}else if(lives == 1) {
    		rect(35,0,20,160);
    	}
    //drawing the ship
    	fill(250,250,250);
    	rect(10,mouseY - 10,20,20);
    	fill(0,100,250);
    	rect(10,mouseY - 5,20,10);
    	fill(0,0,0);
    	rect(20,mouseY - 3,10,6);
	//drawing and moving the blocks
    	fill(200,0,0);
    	rect(blockOne,0,10,50);
    	rect(blockTwo,50,10,50);
    	rect(blockThree,100,10,50);
    	rect(blockFour,150,10,50);
    	rect(blockFive,200,10,50);
    	rect(blockSix,250,10,50);
    	blockOne = blockOne - 3;
        blockTwo = blockTwo - 4;
        blockThree = blockThree - 2;
       	blockFour = blockFour - 5;
       	blockFive = blockFive - 3;
       	blockSix = blockSix - 4;
       	if(blockOne <= 0) {
       		blockOne = 700;
       		score = score + 1;
       	}
       	if(blockTwo <= 0) {
       		blockTwo = 700;
       		score = score + 1;
       	}
       	if(blockThree <= 0) {
       		blockThree = 700;
       		score = score + 1;
       	}
       	if(blockFour <= 0) {
       		blockFour = 700;
       		score = score + 1;
       	}
       	if(blockFive <= 0) {
       		blockFive = 700;
       		score = score + 1;
       	}
       	if(blockSix <= 0) {
       		blockSix = 700;
       		score = score + 1;
       	}
       	// to detect if your ship touches a block
       	if(blockSix >= 10 && blockSix <= 30 && mouseY + 10 >= 250 && mouseY - 10 <= 300 && loop >= loopNeed){
       		loopNeed = 15;
       		loop = 0;
       		lives--;
       	}
       	if(blockFive >= 10 && blockFive <= 30 && mouseY + 10 >= 200 && mouseY - 10 <= 250 && loop >= loopNeed){
       		loopNeed = 15;
       		loop = 0;
       		lives--;
       	}
       	if(blockFour >= 10 && blockFour <= 30 && mouseY + 10 >= 150 && mouseY - 10 <= 200 && loop >= loopNeed){
       		loopNeed = 15;
       		loop = 0;
       		lives--;
       	}
       	if(blockThree >= 10 && blockThree <= 30 && mouseY + 10 >= 100 && mouseY - 10 <= 150 && loop >= loopNeed){
       		loopNeed = 15;
       		loop = 0;
       		lives--;
       	}
       	if(blockTwo >= 10 && blockTwo <= 30 && mouseY + 10 >= 50 && mouseY - 10 <= 100 && loop >= loopNeed){
       		loopNeed = 15;
       		loop = 0;
       		lives--;
       	}
       	if(blockOne >= 10 && blockOne <= 30 && mouseY + 10 >= 0 && mouseY - 10 <= 50 && loop >= loopNeed){
       		loopNeed = 15;
       		loop = 0;
       		lives--;
       	}
       	//checking to see if your lives are at 0
       	if(lives <= 0) {
       		//telling you your score
       		//the lives thing is just a way to make it not print this a thousand times
       		if(lives == 0) {
       		System.out.println("your score was " + score);
       		lives = -1;
       		}
       		//Putting a loop to keep the screen red
       			fill(250,0,0);
       			rect(0,0,700,300);
       	}
       		
       	//checking for t or q during the game to reset or quit
       	if(key == 't') {
				blockOne = 800;
				blockTwo = 600;
				blockThree = 900;
				blockFour = 690;
				blockFive = 500;
				blockSix = 600;
				lives = 3;
				loopNeed = 1;
				loop = 0;
				score = 0;
				key = 'w';
			}else if (key == 'q') {
				System.exit(0);
			}
    }
}
