# RoboCodeTank

package rlh;
import robocode.*;
import java.awt.Color;

// API help : https://robocode.sourceforge.io/docs/robocode/robocode/Robot.html

/**
 * CokeHead - a robot by (McLovin)
 */
public class CokeHead extends Robot
{
	/**
	 * run: CokeHead's default behavior
	 */
	public void run() {
		// Initialization of the robot should be put here

		// After trying out your robot, try uncommenting the import at the top,
		// and the next line:

		 setColors(Color.green,Color.red,Color.orange); // body,gun,radar

		// Robot main loop
		while(true) {
			// Replace the next 4 lines with any behavior you would like
			ahead(200);
			turnGunRight(300);
			back(100);
			turnGunRight(300);
		}
	}

	/**
	 * onScannedRobot: What to do when you see another robot
	 */
	public void onScannedRobot(ScannedRobotEvent e) {
		// Replace the next line with any behavior you would like
		if (e.getDistance() < 150)
		{
			fire(3);
		}
		else
		{
			fire(1.5);
		}
		
	}

	/**
	 * onHitByBullet: What to do when you're hit by a bullet
	 */
	public void onHitByBullet(HitByBulletEvent e) {
		// Replace the next line with any behavior you would like
		turnRight(150);
		back(-25);
	}
	
	/**
	 * onHitWall: What to do when you hit a wall
	 */
	public void onHitWall(HitWallEvent e) {
		// Replace the next line with any behavior you would like
		turnLeft(360);
		turnRight(80);
		back(200);
		back(-300);
	}	
}
