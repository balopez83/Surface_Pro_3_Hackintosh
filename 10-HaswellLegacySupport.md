##  Chapter 10) Haswell Legacy Graphics Support (OCLP)
### macOS Ventura no longer supports Haswell computers. The following instruction will walk you through using OpenCore Legacy Patcher (OCLP) to re-enable support.

1. Install or upgrad to macOS Ventura (Graphics Acceleration will not be enabled yet)
2. Complete first boot user setup. (will be slow as there will not be Graphics Acceleration)
3. Download the latest version of OpenCore Legacy Pathcer (OCLP) here: [OCLP Download](https://github.com/dortania/Opencore-Legacy-Patcher/releases)
4. Copy app to your Applications folder and run
5. Confirm your model is listed as "MacBookPro14,1"
6. Click "Post Install Root Patch"
7. The "Post-Install Menu" should state that a graphics patch exists. Click "Start Root Patching". 
8. Follow remaining prompts and restart your computer when asked to do so. 
9. Upon reboot Graphcis Acceleration should be working. 
