Simple Requests module for FoundryVTT
https://github.com/Achoobert/FoundryVTT-Simple-requests/releases
https://foundryvtt.com/packages/simple-requests

Simple Requests is a module I  have started to maintain for the Foundry Virtual Tabletop platform. It's forked from `advance requests` by Nazgob. His version was not updated past `v11`, and what started as a simple "fork and update" turned into a very different project. The original had a lot of integrations with his (paid) visual novel mod. But aside from that there was a lot of pop-ups that players would get, and I would have to go in and do a lot of work to select the correct photos. In order to save a few seconds of later work, I spent hours on this mod.

## what does it do?
It introduces a streamlined "Requests" system that allows players to signal their desire to speak during a session, using three levels of urgency (Common, Important, Urgent). This helps GMs manage table talk and ensures everyone gets a chance to contribute, without disrupting the flow of the game.
Key Features:
Real-time, synchronized request queue for all players and the GM
Three request levels, each with customizable audio cues
Intuitive UI integrated into the FoundryVTT chat sidebar
Accessibility and customization options for both players and GMs
"Epic prompt" GM can visually alerting all users


See the project on GitHub:
https://github.com/achoobert/FoundryVTT-Simple-requests


## Tech highlights
### Cross-Platform UI Consistency:
Ensured the request queue UI worked seamlessly across different FoundryVTT versions (v12, v13), handling changes in DOM structure, sidebar behavior, and chat input placement.
### CSS & Layout Debugging:
Resolved complex issues with flex and grid layouts, including handling flex-direction: column-reverse, sticky positioning, and ensuring the request queue always appeared in the correct place regardless of sidebar state or visibility of other elements.
### Robust Event Handling:
Debugged and fixed right-click (contextmenu) event handling for removing requests, ensuring correct user permissions and reliable DOM updates


## Automated Testing:
After about 10 manual tests, I got annoyed and got Cypress end-to-end tests working, 
(meaning handling asynchronous UI updates, dynamic selectors, and ensuring tests Worked with both versions of foundry)
### Modern Release Automation:
Refactored a GitHub Actions workflow I found, simplifying the release process.
### Settings & Customization:
Greatly simplified user and GM settings for sound, image, and queue behavior, including using a smart default for audio volume based on user interface settings.
### Codebase Refactoring & Best Practices:
Modularized the code, improved maintainability, and adopted best practices from other successful FoundryVTT modules (raise-my-hand, dice-tray). I really like the original design, but bro did not have his queue logic working correctly. I moved the queue management logic away from the socket IO and UI management, because I'm lazy and that made debugging easier