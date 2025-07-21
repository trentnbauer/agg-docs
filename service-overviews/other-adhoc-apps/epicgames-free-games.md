# EpicGames Free Games

[Link to GitHub or Website](https://github.com/claabs/epicgames-freegames-node)

Automatically login and find available free games the Epic Games Store. Sends you a prepopulated checkout link so you can complete the checkout after logging in. Supports multiple accounts, login sessions, and scheduled runs.&#x20;

We use the cookie import method to authenticate users.

This app is hosted on Cocoa as a docker container

{% @github-files/github-code-block url="https://github.com/trentnbauer/agg/blob/main/docker-compose/epicgames.yml" %}

| Port | Purpose |
| ---- | ------- |
| 3434 | WebUI   |

| Host Volume       | Container Volume | Purpose                        |
| ----------------- | ---------------- | ------------------------------ |
| epicgames\_config | /usr/app/config  | Stores config and cookie files |

## Cookie Import

1. [Follow the official guide to export your cookies](https://github.com/claabs/epicgames-freegames-node?tab=readme-ov-file#cookie-import)
2. Log into [Portainer](../portainer-and-gitops/)
3. Select Cocoa
4. On the left, select Volumes
5. Click on 'Browse' next to the epicgames\_config volume
6. Click on upload
7. Upload your JSON file
8. Edit the config.json file
   1. Download the config.json file
   2. Open the config.json in Visual Studio code
   3. Locate line 35 (accounts), click on the end and then hit enter
   4.  Copy and paste the below code block and replace the example email with yours

       ```json
           {
             "email": "example@email.com"
           },
       ```
   5. Save the file
9. Upload the edited config.json file
10. On the left, click on Stacks
11. Select Epic Games
12. Click on 'Stop this stack', then OK
13. Click on 'Start this stack'
