---
title: "666 Malevolence Lane"
date: 2026-04-25T00:00:00+08:00
draft: false
github_link: "https://github.com/gurusabarish/hugo-profile"
badges:
  - Unreal - Blueprints
  - Technical Direction
  - Build Automation - Python
  - Gameplay Programming
imagelink:
  enable: true
  link: /projects/666-malevolence-lane
image: /images/mallane2.jpg
#banner: /images/mallanebanner.png
description: ""
summary: "An action-packed minigame focused local multiplayer experience for you and your friends! Click 'Read more' to learn about my involvement!"
toc: 
---

{{<image width=100% maxwidth=100% src="/images/mallanebanner.png">}}

## My Involvement

I made this game as a collaborative effort during senior year of my degree as my capstone project. As Technical Director on the project, I was involved in most engineering aspects of the game, such as architecture of the core systems, heading development on the Player AI systems, and handling build automation. I also contributed two of the playable minigames in 666 Malevolence Lane, which are outlined in more detail below. Beyond the systems I made, I worked in most of the codebase doing polish and general bugfixing for the last few months of development.

### Build Automation

One of my prouder contributions to the project was a system for automatically updating a machines' code and art assets through P4 and building the project nightly. I hooked this system up to a Discord bot and used a combination of the bot and webhooks to display information regarding build automated test statuses, which helped us identify quickly what changelists last broke the ability to package our project.

Here's a small example of how I was fetching these files and building the game using Python and APScheduler:

```
#Build function that runs once every 24 hours via APScheduler
def BuildGame(self):
        #Changes directory to UE5 build tools
        os.chdir(f"{self.epic_games_folder_path}/Engine/Build/BatchFiles/")

        #Builds the project's code into a target file
        exit_code = subprocess.call(f"Build.bat {self.project_name} Win64 Development \"{self.game_uproject_path}\"")

        if not exit_code == 0:
            self.webhook.send(f"# Build Information\n\nFailed to build target file from source code! {alert_role_id}", thread=self.thread_id)
            return False

        #Starts build and package of project at game_uproject_path
        exit_code = subprocess.call(f"RunUAT BuildCookRun -project=\"{self.game_uproject_path}\" -platform=Win64 -clientconfig=Development -serverconfig=Development " +
                                    f"-skipcook -maps=AllMaps -compile -stage -pak -archivedirectory={self.build_folder_path} -archive", shell=True)
        
        #If exit_code is anything other than 0 then build has failed, pings Camilla in discord
        if not exit_code == 0:
            self.webhook.send(f'# Build Information\n\nBuild failed! {alert_role_id}', thread=self.thread_id)
            return False
        else:
            data = BuildUtils.GetBuildJSONData()
            data["version"] += 1
            BuildUtils.StoreBuildJSONData(data)
            rel, mile, ver = data["release"], data["milestone"], data["version"]
            self.webhook.send(f'# Build Information\n\nBuild successful! Current version: v{rel}.{mile}.{ver} {alert_role_id}', thread=self.thread_id)
            return True
```

### Player AI

This was a feature that posed a few technical challenges for making the game, the fact that each minigame in 666 Malevolence Lane needs some sort of unique implementation complicated things, but a solid foundation of reusable tasks and helper components to give the AI more information and make them smarter players goes a long way in making the game more enjoyable to play when you don't have enough people to fill out all the slots.

{{<image width=100% maxwidth=100% src="/images/mallanebt.png">}}

### Minigames

While working on the game, I contributed 2 out of the 10 playable minigames available in 666 Malevolence Lane. The first one was part of our initial playtesting prototype, known in-game as 'Musical Scares', which is a chance based minigame where players pick from hiding spots that are slowly made inaccessible as the enemy eliminates more players. Since we wanted a unified Interact button that served multiple purposes across different minigames, this seemed like a good minigame to start our prototype with and to flesh out that system.

{{<image width=100% maxwidth=100% src="/images/mallanems.gif">}}

I also developed a minigame focused on an infinite procedural hallway that plays on older horror tropes, called 'Hall'O'Way Chase'. The procedural generation for the hallway uses a number of tileable models made by our artists before adding additional details such as lights, windows, pillars, etc. Finally obstacles and clutter are placed through the hallway in a periodic and fair manner.

{{<image width=100% maxwidth=100% src="/images/mallanehowc.gif">}}

## Steam Release

Our team leads decided early that one of our end goals for the project was publication on Steam, as we deemed it to be a big learning experience that we couldn't pass up on. We felt that achieving a full game launch before the end of the year would mean that managed to appropriately scope the features and content of the game to fit within our allotted project timeframe. With some last minute crunch, we were glad to accomplish this as of April 22nd, 2026! If you would like to support our project or check out our trailer, [you can find us over on Steam](https://store.steampowered.com/app/4450260/666_Malevolence_Lane/)!

[![Image](/images/mallanebanner2.png)](https://store.steampowered.com/app/4450260/666_Malevolence_Lane/)