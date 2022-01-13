# RoboCodeTank

```
package rlh;
import java.awt. * ;
import robocode.Robot;
import robocode.ScannedRobotEvent;
import robocode.util.Utils;
import robocode. * ;
import java.awt. * ;
import static robocode.util.Utils.normalRelativeAngleDegrees;

public class fnlbot extends AdvancedRobot {
  public int num = 1;
  public int rotation = 90;
  public void run() {

    setAdjustGunForRobotTurn(true);
    
    turnLeft(getHeading());
    TacticalAvoidance();
    while (num == 1) {
      setAdjustRadarForRobotTurn(true);
      turnRadarRight(360);
    }
  }

  public void TacticalAvoidance() {
    ahead(150);
  }

  public void onHitWall(HitWallEvent event) {
    turnLeft(rotation);
  }

  public void BulletHitEvent() {
    TacticalAvoidance();
  }

  public void onHitRobot(HitRobotEvent event) {
    turnRight(180);
    rotation = -1*90;
    TacticalAvoidance();
  }

  public void onScannedRobot(ScannedRobotEvent e) {
    double absoluteBearing = getHeading() + e.getBearing();
    double bearingFromGun = normalRelativeAngleDegrees(absoluteBearing - getGunHeading());
    turnGunRight(bearingFromGun);
    if (getGunHeat() == 0 && Math.abs(getGunTurnRemaining()) < 10) {
    	  double distance = e.getDistance();
    	  if(distance >= 400){
          fire(1);
        }
        else if(distance < 400 && distance > 200){
          fire(2);
        }
        else{
          fire(3);
        }
    }
    TacticalAvoidance();
  }

}
```
