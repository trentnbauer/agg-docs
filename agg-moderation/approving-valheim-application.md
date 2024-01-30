# Approving Valheim Application

This page outlines the process followed to approve and whitelist a new player for the [valheim-private.md](../game-servers/valheim-private.md "mention") server

## New Application Submitted

When an application is submitted the mod chat will be ping'd. You will need to join the application thread to view the application. Review the form submitted by the user and ensure you are happy with the responses.&#x20;

* Feel free to request more information from the player
* If the player has provided the name of an existing server member, message them as a reference
* Request their SteamID64 string if not provided, [#getting-your-steamid-string](../game-servers/valheim-private.md#getting-your-steamid-string "mention")&#x20;

## Player is Approved

### Whitelist the Player

Once you are happy with the application and are ready to whitelist the player,

1. Browse to the [Pterodactyl Panel](https://panel.agamersgrind.com) and log in with your account
2. Click [here to open the Permittedlist.txt file](https://panel.agamersgrind.com/server/07374dff/files/edit#/.config/unity3d/IronGate/Valheim/permittedlist.txt) or
   1. Select the Valheim Private server
   2. Click on the Files tab
   3. Navigate to .config\unity3d\irongate\valheim and open the permittedlist.txt file
3.  Add the below lines and fill in the relevant data

    {% code title="PermittedList.txt" %}
    ```
    //Discord Name, Discord Application Number
    STEAMID64
    ```
    {% endcode %}
4. Save the file
5. Post in the Discord Thread and advise the player that they have been approved

### Installing the Modpack

Provide the user with a link to [#install-the-modpack](../game-servers/valheim-private.md#install-the-modpack "mention") if they have not already

### Close the Application

1. Add the user to the 'Valheim Private' discord role
2. Click 'close with reason', advising the application has been approved

## Player is Denied

Process not outlined yet
