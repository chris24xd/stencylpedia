## Contents

* Introduction
* Setting up Game Center on iTunes Connect
* Starting Game Center
* Reporting High Scores and Achievements
* Displaying Boards
* Troubleshooting
 

## Introduction

Game Center is an Apple-operated service that records high scores, achievements, and charts these types of stats against those of friends and acquaintances.

Stencyl supports the high scores (leaderboards) and achievmements portions of Game Center. We don't support the multiplayer features.


## Setting up Game Center on iTunes Connect

In order to even test out Game Center functionality, **you must set your game up on iTunes Connect** and enable Game Center support for the game. Then, you must set up the leaderboards and achievements for your game.

This process is well-documented, but it constantly changes. For that reason, we'll point you to a 3rd-party article for setup, rather than put out something in-house that will fall out of date.

[Read this article](http://code.tutsplus.com/tutorials/ios-sdk-game-center-achievements-and-leaderboards-part-1--mobile-5701) for details.
 

## Starting Game Center

**You must start the Game Center service through a behavior before using it**. You want to do this as early as possible, preferably at the start of the game.

#### Signing In

For example, create a behavior that uses the following block (under Game > Mobile) and add it to your first/starting scene. 

![start-game-center](http://static.stencyl.com/help/images/gamecenter/image05.png)

When the Game Center bar appears, the player is considered to be signed in to Game Center.


#### Checking that the player is signed-in

Before you use any Game Center functionality, you should check that the player is signed-in. You can do this either with a block or an event.

You can check for this status using the following block, or you can use an Event (Add Event > Mobile > Game Center > Game Center is started) if you wish to be notified when this happens.


## Reporting High Scores and Achievements

To submit a high score or achievement, use the blocks shown below. The ID is the **Leaderboard ID** you specified on iTunes Connect.

Block | Description | Where to Find
--- | --- | ---
![stencyl-high-score-block](http://static.stencyl.com/pedia2/ch11/submit-score.png) | ID = Leaderboard ID<br/>Score must be a number | Game > Mobile
![stencyl-achievements-block](http://static.stencyl.com/pedia2/ch11/report-achievement.png)  | ID = Leaderboard ID<br/>Number must be between 0 - 100 inclusive | Game > Mobile

> **Note:** Submitting a score or achievement does *not* pause the game. If you'd like to pause the game, consider using a Game Center event (Add Event > Mobile > Game Center > Game Center receives a score / achievement.)
 

## Displaying the High Score and Achievements Boards

Displaying the high score or achievements board involves the following blocks. As described below, you provide the **Leaderboard ID** that you entered into **iTunes Connect**.

Block | Description | Where to Find
--- | --- | ---
![stencyl-show-leaderboard-block](http://static.stencyl.com/pedia2/ch11/show-leaderboard.png) | Shows the specified leaderboard (given a Leaderboard ID) | Game > Mobile
![stencyl-show-achievements-block](http://static.stencyl.com/pedia2/ch11/show-achievements.png)  | Shows all achievements for this game | Game > Mobile

When you use these blocks, the leaderboard (or achievements page) will appear. The game will pause, so you don't need to worry about the game continuing to run while the leaderboards are being viewed.
 

## Troubleshooting

#### Scores and Achievements not showing up?
Sometimes you have to wait a few hours for the data to show up in Game Center. This seems to afflict those who are far from Apple's server farms in the US, particularly Europe.

Another common cause is that sometimes, **Game Center requires that at LEAST 2 players need to submit scores for the board to show up at all**.

#### Game Center doesn't work at all in iOS 7 for my app. I canceled Game Center a few times.
Is a user has canceled Game Center 3 or more times, Game Center is permanently disabled for that app. The following post explains how to reverse this. 

http://stackoverflow.com/questions/18927723/reenabling-gamecenter-after-user-cancelled-3-times-ios7-only

 
#### Game Center doesn't work in iOS 8 while I'm testing it.
Solution - You must enable Game Center Sandbox Mode. Consult the following page.

http://stackoverflow.com/questions/25238646/ios-8-beta-5-game-center-sandbox-wont-recognize-my-app